# MoreUI
MoreUI fills many of the major gaps in SwiftUI, including a vast number of unimplemented view controllers still not available as SwiftUI Views in the standard library. It alleviates the nuisance of manually interfacing with UIKit, and expands what's possible with pure SwiftUI. It also features a large collection of original views and capabilities that are highly practical for SwiftUI app development.

# Contents

Documentation is currently a work-in-progress, available via the [repository wiki](https://github.com/ryanrudes/MoreUI/wiki).

### UIKit → SwiftUI 

| UIKit                                   | MoreUI                                     | Status     |
| --------------------------------------- | ------------------------------------------ | ---------- |
| `UIReferenceLibraryViewController`      | `ReferenceLibrary`                         | Completed  |
| `PHPickerViewController`                | `PhotoPicker`                              | Completed  |
| `UIImagePickerController`               | `ImagePicker`                              | W.I.P.     |
| `UISearchBar`                           | `SearchBar`                                | Completed  |
| `UIPageViewController`                  | `PageView`                                 | W.I.P.     |
| `UIVideoEditorController`               | `VideoEditor`                              | W.I.P.     |
| `UIFontPickerViewController`            | `FontPicker`                               | Completed  |
| `UIDocumentBrowserViewController`       | `DocumentBrowser`                          | w.I.P.     |
| `UIDocumentPickerViewController`        | `DocumentPicker`                           | Completed  |
| `UIDocumentInteractionController`       | `DocumentInteractor`                       | W.I.P.     |
| `UICloudSharingController`              | `CloudSharingView`                         | W.I.P.     |
| `UIActivityViewController`              | `ActivityView`                             | W.I.P.     |
| `UIPrinterPickerController`             | `PrinterPicker`                            | W.I.P.     |
| `UISegmentedControl`                    | `SegmentedControl`                         | W.I.P.     |
| `UIFeedbackGenerator`                   | `Feedback` & `HapticGenerator`             | Completed  |

### Original SwiftUI Views
| View                                    | Description                                                         | Status     |
| --------------------------------------- | ------------------------------------------------------------------- | ---------- |
| `RangeSlider`                           | Two-handle slider for selecting an interval of values.              | Completed  |
| `PinchView`                             | View wrapper that enables scaling via the pinch gesture.            | Completed  |
| `PIPView`                               | View wrapper to present video content in picture-in-picture mode.   | W.I.P.     |
| `SFSymbolPicker`                        | Picker for the selection of SFSymbols.                              | Completed  |
| `Toast`                                 | View for presenting Apple-style toast alerts (new in iOS 15).       | W.I.P.     |
| `SpeechRecognizer`                      | View wrapper for performing actions according to dictated input.    | Completed  |

### Other Original SwiftUI Features
| Feature                                 | Description                                                         | Status     |
| --------------------------------------- | ------------------------------------------------------------------- | ---------- |
| `Animation.wiggle`                      | Wiggle animation, resembles shaking icons when editing home screen. | W.I.P.     |
| `.toast()`                              | View modifier for presenting alert toasts.                          | W.I.P.     |
| `.pip()`                                | View modifier for presenting content in picture-in-picture mode.    | W.I.P.     |
| `\.notificationCenter`                  | Environment value for delivering notifications.                     | Completed  |
| `Feedback` & `HapticGenerator`          | Custom property wrapper for triggering haptic feedback.             | Completed  |

### Notifications

MoreUI features the scheduling of local notifications for delivery by exposing an extended `UNUserNotificationCenter` through a new environment value, `\.notificationCenter`. See the basic implementation below.

```swift
struct ContentView: View {
    @Environment(\.notificationCenter) var notificationCenter
    
    var body: some View {
        Button("Send Notification") {
            notificationCenter.post(title: "My Notification",
                                    subtitle: "A brief description",
                                    body: "Some more info.",
                                    trigger: {
                let trigger = UNTimeIntervalNotificationTrigger(timeInterval: 3, repeats: false)
                return trigger
            })
        }
    }
}
```

https://user-images.githubusercontent.com/18452581/140665813-b26292f4-f042-4082-82e6-3c9fbb0ed4dd.mp4

You can customize all properties exposed by `UNNotificationContent`, including the badge, sound, optional attachments, and much more. In addition, you can customize the trigger, as in, how the system delivers the notification.

All in all, here's a succinct documentation of the notification delivery method, `post()`:

- Parameters:
    - `title`: The localized title, containing the reason for the alert.
    - `subtitle`: The localized subtitle, containing a secondary description of the reason for the alert.
    - `body`: The localized message to display in the notification alert.
    - `badge`: The number to apply to the app’s icon.
    - `sound`: The sound to play when the system delivers the notification.
    - `launchImageName`: The name of the custom launch image to display when the system launches your app in response to the notification.
    - `userInfo`: A dictionary of custom information associated with the notification.
    - `attachments`: An array of attachments to display in an alert-based notification.
    - `summaryArgument`: The string the notification adds to the category’s summary format string. This argument has been deprecated starting in iOS 15.0.
    - `summaryArgumentCount`: The number of items the notification adds to the category’s summary format string. This argument has been deprecated starting in iOS 15.0.
    - `categoryIdentifier`: The identifier of the category object that represents the notification’s type.
    - `threadIdentifier`: An identifier that you use to group related notifications together.
    - `targetContentIdentifier`: A value your app uses to identify the notification content.
    - `interruptionLevel`: The interruption level determines the degree of interruption associated with the notification.
    - `relevanceScore`: The value the system uses to sort your app’s notifications.
    - `options`: The authorization options your app is requesting. You may combine the available constants to request authorization for multiple items. Request only the authorization options that you plan to use. For a list of possible values, see ``UNAuthorizationOptions``. Some notification options are handled automatically based on the specification of other parameters, such as `.badge`, `.sound`, `.criticalAlert`, and `.alert`. These do not need to be specified manually by the user.
    - `trigger`: A function returning the condition that causes the system to deliver the notification. Specify `nil` to deliver the notification right away. See ``UNNotificationTrigger`` for documentation on concrete trigger classes.

# License

MoreUI is licensed under the [MIT License](https://github.com/ryanrudes/MoreUI/blob/main/LICENSE).

# Credits

MoreUI is a project of [@ryanrudes](httpsL//github.com/ryanrudes).

# Related Projects

- [SwiftUIX](https://github.com/SwiftUIX/SwiftUIX)
- [PhantomKit](https://github.com/pawello2222/PhantomKit)
