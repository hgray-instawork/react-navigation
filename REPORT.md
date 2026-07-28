# Next native-stack Screens gap report

## Scope

This report compares `@react-navigation/native-stack` 8.0.0-alpha.48 with
`react-native-screens` 5.0.0-alpha.1. The option reference is the unreleased
[React Navigation 8.x native-stack documentation](https://reactnavigation.org/docs/8.x/native-stack-navigator/).

The report tracks option coverage, missing Screens APIs, upstream bugs, and
temporary workarounds.

- **Supported**: Mapped and working.
- **Partial**: Mapped with the stated limit.
- **Forwarded; no effect**: Screens accepts the value, but the platform
  implementation does not apply it.
- **No API**: Screens 5 has no matching API for this platform.
- **Not mapped**: Screens 5 has a matching API, but this renderer does not use
  it.
- **—**: The option does not apply to the platform.

The **Different from stable native-stack** column compares this renderer with
the established native-stack renderer.

## Option and event coverage

### Cards

| Option or event    | Android                               | iOS                                   | Different from stable native-stack |
| ------------------ | ------------------------------------- | ------------------------------------- | ---------------------------------- |
| `contentStyle`     | Supported                             | Supported                             | No                                 |
| `inactiveBehavior` | Supported: `pause`, `unmount`, `none` | Supported: `pause`, `unmount`, `none` | No                                 |
| `usePreventRemove` | Supported                             | Supported                             | No                                 |
| `transitionStart`  | Supported                             | Supported                             | No                                 |
| `transitionEnd`    | Supported                             | Supported                             | No                                 |

### Headers

| Option                                          | Android                                      | iOS                                   | Different from stable native-stack                                  |
| ----------------------------------------------- | -------------------------------------------- | ------------------------------------- | ------------------------------------------------------------------- |
| `title`                                         | Supported                                    | Supported                             | No                                                                  |
| `header`                                        | Supported                                    | Supported                             | No                                                                  |
| `headerShown`                                   | Supported                                    | Supported                             | No                                                                  |
| `headerBackVisible`                             | Supported                                    | Supported                             | No                                                                  |
| `headerLeft`                                    | Supported                                    | Supported                             | No                                                                  |
| `headerRight`                                   | Supported                                    | Supported                             | No                                                                  |
| `headerTitle`                                   | Supported                                    | Supported                             | No                                                                  |
| `headerTransparent`                             | Supported                                    | Supported                             | No                                                                  |
| `headerBackground`                              | Supported                                    | Supported                             | No                                                                  |
| `headerBackTitle`                               | —                                            | Partial: `headerLeft` callback only   | Yes: Screens 5 has no native iOS back-title API                     |
| `headerSubtitle`                                | Forwarded; no effect                         | Supported: string and custom, iOS 26+ | Yes: Screens 5 adds iOS subtitle support                            |
| `headerTintColor`                               | Partial: back/menu icons and custom elements | Partial: custom elements only         | Yes: Screens 5 has no iOS tint API or Android native-title tint API |
| `headerBackIcon`                                | Supported                                    | No API                                | Yes: Screens 5 has no native iOS back-icon API                      |
| `headerType`                                    | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `headerBackgroundCollapseMode`                  | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `headerBackButtonTintColorPressed`              | Supported                                    | —                                     | Yes: Screens 5 adds this Android API                                |
| `headerBackButtonTintColorFocused`              | Supported                                    | —                                     | Yes: Screens 5 adds this Android API                                |
| `headerScrollFlagScroll`                        | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `headerScrollFlagEnterAlways`                   | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `headerScrollFlagEnterAlwaysCollapsed`          | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `headerScrollFlagExitUntilCollapsed`            | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `headerScrollFlagSnap`                          | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `unstable_headerToolbarMenu`                    | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `unstable_headerToolbarMenuGroupDividerEnabled` | Supported                                    | —                                     | Yes: Screens 5 adds this API                                        |
| `headerLargeTitleEnabled`                       | —                                            | Supported                             | No                                                                  |
| `headerLargeSubtitle`                           | —                                            | Supported: string and custom, iOS 26+ | Yes: Screens 5 adds this API                                        |
| `unstable_headerLeftItems`                      | —                                            | Partial: core item types and actions  | Yes: some stable item options are missing or not mapped             |
| `unstable_headerRightItems`                     | —                                            | Partial: core item types and actions  | Yes: some stable item options are missing or not mapped             |

### Form sheets

| Option or event                   | Android                                           | iOS                                            | Different from stable native-stack                      |
| --------------------------------- | ------------------------------------------------- | ---------------------------------------------- | ------------------------------------------------------- |
| `sheetAllowedDetents`             | Partial: at most 3 detents                        | Supported                                      | No                                                      |
| `sheetGrabberVisible`             | Supported: documented as iOS-only                 | Supported                                      | No                                                      |
| `sheetInitialDetentIndex`         | No API                                            | Supported                                      | Yes: Screens 5 supports this only on iOS                |
| `sheetLargestUndimmedDetentIndex` | No API                                            | Supported                                      | Yes: Screens 5 supports this only on iOS                |
| `sheetCornerRadius`               | Partial: API level 33+                            | Supported                                      | No                                                      |
| `sheetExpandsWhenScrolledToEdge`  | No API                                            | Supported                                      | No                                                      |
| `contentStyle`                    | Supported                                         | Supported                                      | No                                                      |
| `usePreventRemove`                | No API                                            | Supported                                      | Yes: Screens 5 supports protected dismissal only on iOS |
| `gestureEnabled`                  | No API                                            | No API                                         | Yes: stable supports it on iOS                          |
| `sheetElevation`                  | No API                                            | —                                              | Yes: stable supports it on Android                      |
| `sheetShouldOverflowTopInset`     | No API                                            | —                                              | Yes: stable supports it on Android                      |
| `sheetResizeAnimationEnabled`     | No API                                            | —                                              | Yes: stable supports it on Android                      |
| `unstable_sheetFooter`            | No API                                            | —                                              | Yes: stable supports it on Android                      |
| `transitionStart`                 | Supported                                         | Supported                                      | No                                                      |
| `transitionEnd`                   | Supported                                         | Supported                                      | No                                                      |
| `sheetDetentChange`               | Partial: emits only `stable: true` after settling | Supported: emits `stable: true` after settling | Yes: Screens 5 does not report Android drag updates     |

## Missing Screens APIs and unmapped options

This table separates options that need a new Screens 5 API from options that
Screens 5 already exposes. Deprecated options are excluded.

Unmapped presentation values currently use card behavior.

| Area                     | Options or capabilities                                                                                                                                                                                                                                                                                                                                                                | Screens 5 API status                       |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ |
| Presentations            | `modal`, `containedModal`, `fullScreenModal`, `transparentModal`, `containedTransparentModal`, `pageSheet`                                                                                                                                                                                                                                                                             | Missing in Screens 5                       |
| Screen and system UI     | `autoHideHomeIndicator`, `navigationBarHidden`, `statusBarAnimation`, `statusBarHidden`, `statusBarStyle`, `orientation`, `scrollEdgeEffects`, `keyboardHandlingEnabled`, `gestureResponseDistance`                                                                                                                                                                                    | Missing in Screens 5                       |
| Animations and gestures  | `animation`, `animationDuration`, `animationTypeForReplace`, `animationMatchesGesture`, `gestureDirection`, `gestureEnabled`, `fullScreenGestureEnabled`                                                                                                                                                                                                                               | Missing in Screens 5                       |
| Header appearance        | `headerBackButtonMenuEnabled`, `headerBackButtonDisplayMode`, `headerBackTitleStyle`, `headerLargeStyle`, `headerLargeTitleShadowVisible`, `headerLargeTitleStyle`, `headerStyle`, `headerShadowVisible`, `headerBlurEffect`, `headerLeftBackgroundVisible`, `headerRightBackgroundVisible`, `headerTitleAlign`, `headerTitleStyle`, `headerSearchBarOptions`, `unstable_headerInsets` | Missing in Screens 5                       |
| iOS native back controls | Native `headerBackTitle`, `headerBackIcon`, and `headerTintColor`; pressed and focused back-button tint                                                                                                                                                                                                                                                                                | Missing in Screens 5                       |
| iOS header item options  | Label styles and tint; disabled state; badges; item width; shared-background controls; selection state; accessibility data; action descriptions; destructive, hidden, and discoverability states; selection as the primary action                                                                                                                                                      | Missing in Screens 5                       |
| iOS header item mappings | Item and menu icons; inline and palette submenu layouts; Boolean controlled menu state                                                                                                                                                                                                                                                                                                 | Available in Screens 5; not mapped by Next |
| Events and measurements  | `gestureCancel`; native large-title height changes                                                                                                                                                                                                                                                                                                                                     | Missing in Screens 5                       |

Without native large-title height updates, header height consumers and custom
iOS header backgrounds cannot follow large-title expansion.

## Upstream bugs and workarounds

| Type                | Area                                         | Problem                                                                                                      | Temporary workaround                                                                                           | Screens change needed                                             |
| ------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Regression          | Sheet replacement                            | A new sheet can appear behind the sheet that is closing.                                                     | Reject sheet-to-sheet replacement with an error.                                                               | Replace one `FormSheet` with another atomically.                  |
| Regression          | iOS `fitToContents` with nested `Stack.Host` | `Stack.Host` does not provide a useful intrinsic height, so the sheet cannot measure its content.            | The nested content must provide a measurable height.                                                           | Expose the intrinsic stack content height.                        |
| Existing constraint | Nested `Stack.Host` in Android `FormSheet`   | This composition can crash because the dialog parent is not the React root expected by the stack host.       | None.                                                                                                          | Support stack hosts and headers inside Android sheets.            |
| Screens 5 bug       | Android header icon tint                     | A state tint without a normal tint makes the normal icon transparent.                                        | Supply a normal tint when a state tint is present. Preserve each item's normal tint during imperative updates. | Preserve or derive the normal tint when state tints are supplied. |
| Screens 5 bug       | Android protected sheet dismissal            | Android ignores `FormSheet.preventNativeDismiss`. The sheet can close before navigation accepts the removal. | No complete workaround. The native sheet can close while removal is blocked.                                   | Implement `preventNativeDismiss` on Android.                      |
| Screens 5 gap       | Android sheet detent options                 | The FormSheet API supports `sheetInitialDetentIndex` and `sheetLargestUndimmedDetentIndex` only on iOS.      | None.                                                                                                          | Add and implement both options on Android.                        |
| Screens 5 bug       | Android small detents                        | Content can use the largest sheet height and be cropped when the sheet moves to a smaller detent.            | None.                                                                                                          | Lay out content at the current detent or expose its visible size. |
