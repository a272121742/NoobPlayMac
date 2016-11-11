MacOS下删除自带英文输入法
==

# 适用环境

0. Yosemite（10.10）、El Capitan（10.11）、Sierra（10.12）均支持
0. 10.10以下系统版本理论上支持，不需要改动苹果安全级别

# 操作

## 1. 备份输入法文件

`⇧⌘G`（shfit+command+G）打开`~/Library/Preferences`，备份里面的`com.apple.HIToolbox.plist`文件。

## 2. 修改输入法配置

使用能打开和修改plist文件的软件，将文件修改如下

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>AppleCurrentKeyboardLayoutInputSourceID</key>
  <string>com.apple.keylayout.PinyinKeyboard</string>
  <key>AppleEnabledInputSources</key>
  <array>
    <dict>
      <key>Bundle ID</key>
      <string>com.apple.inputmethod.EmojiFunctionRowItem</string>
      <key>InputSourceKind</key>
      <string>Non Keyboard Input Method</string>
    </dict>
    <dict>
      <key>Bundle ID</key>
      <string>com.apple.inputmethod.SCIM</string>
      <key>InputSourceKind</key>
      <string>Keyboard Input Method</string>
    </dict>
    <dict>
      <key>Bundle ID</key>
      <string>com.apple.inputmethod.SCIM</string>
      <key>Input Mode</key>
      <string>com.apple.inputmethod.SCIM.ITABC</string>
      <key>InputSourceKind</key>
      <string>Input Mode</string>
    </dict>
  </array>
  <key>AppleHandwritingDisabledInputSources</key>
  <array>
    <string>com.apple.inputmethod.SCIM</string>
  </array>
  <key>AppleInputSourceHistory</key>
  <array>
    <dict>
      <key>Bundle ID</key>
      <string>com.apple.inputmethod.SCIM</string>
      <key>Input Mode</key>
      <string>com.apple.inputmethod.SCIM.ITABC</string>
      <key>InputSourceKind</key>
      <string>Input Mode</string>
    </dict>
  </array>
  <key>AppleSelectedInputSources</key>
  <array>
    <dict>
      <key>Bundle ID</key>
      <string>com.apple.inputmethod.EmojiFunctionRowItem</string>
      <key>InputSourceKind</key>
      <string>Non Keyboard Input Method</string>
    </dict>
    <dict>
      <key>Bundle ID</key>
      <string>com.apple.inputmethod.SCIM</string>
      <key>Input Mode</key>
      <string>com.apple.inputmethod.SCIM.ITABC</string>
      <key>InputSourceKind</key>
      <string>Input Mode</string>
    </dict>
  </array>
</dict>
</plist>
```

## 注意事项

- 10.10及其高版本系统需要关闭苹果的内核保护再操作（`csrutil disable`），操作完后再恢复（不要完全恢复，使用`csrutil enable --without debug`即可）
- 10.10以下的低版本不需要额外的步骤
