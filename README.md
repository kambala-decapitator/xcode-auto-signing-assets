# xcode-auto-signing-assets
Automate creating Apple signing assets using xcodebuild

First, open `UpdateSigningAssets.xcodeproj`, click `UpdateSigingAssets` with blue icon in the top left, open `Signing & Capabilities` and select your `Team`.

- advanced users: you may pass team ID directly to the script in `DEVELOPMENT_TEAM` build setting instead

Example:
```sh
xcodebuild -target iOS PRODUCT_BUNDLE_IDENTIFIER=your.bundle.id -allowProvisioningUpdates \
  | grep --fixed-strings --after-context=2 'Signing Identity:'
```

Output:
```
Signing Identity:     "Apple Development: your@email.com (TEAMID)"
Provisioning Profile: "iOS Team Provisioning Profile: your.bundle.id"
                      (UUID-of-the-profile)
```
