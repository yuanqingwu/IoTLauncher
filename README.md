# IoTLauncher
面向IoT时代的桌面系统

## 方案设计

由于IOT时代，类似车机，冰箱等屏幕与手机屏幕的操作习惯不同，通常不太易于进行非常细致的近距离操作，所以希望能通过桌面透出尽量多的有用信息，并且能在桌面即可完成大部分常用设置。

当然桌面只是提供容器，这里就需要实现一套规则，能让各个应用自己实现要显示在桌面的内容，听着有点像桌面小部件（widget），是的，widget的时代来了，但是我们希望实现的是更加易于开发，更加灵活的widget。

初步设想是使用多个window实现类似WindowsPhone的效果。

参考widget的设计，会让桌面的window内容带一些快捷操作以及状态显示，原生widget会限制使用特定的控件，并且是运行在系统进程，这些限制都是需要完善拓展的。


- 借助Android freeform自由窗口机制实现

通过 config_supportsMultiWindow 标志启用多窗口模式后，设备制造商可以允许启用自由窗口。此模式在较大的设备（例如平板电脑）上最为有用。

如需支持自由窗口模式，请启用 /android/frameworks/base/core/java/android/content/pm/PackageManager.java 中的 PackageManager#FEATURE_FREEFORM_WINDOW_MANAGEMENT 系统功能，并在 config.xml. 中将 config_freeformWindowManagement 设置为 true。

- 借助TaskView实现（android 12以上）
参考CarLauncher实现。
http://aospxref.com/android-13.0.0_r3/xref/packages/apps/Car/Launcher/src/com/android/car/carlauncher/CarLauncher.java
http://aospxref.com/android-13.0.0_r3/xref/packages/apps/Car/Launcher/src/com/android/car/carlauncher/TaskViewManager.java
