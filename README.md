
## Intro to Tape Libraries
* [Setup](#Setup)
* [Partition Creation](#Partition-Creation)
* [Host Setup](#Host-Setup)
* [Teardown](#Teardown)

#### Setup
 - [ ] Navigate to `Configuration > System` and perform some initial configuration
    * Name the library. There is likely a name printed on the side of the library however you can call it whatever you'd like.
    * Check `Enable Drive Performance Monitoring`. It gives us some fun graphs later on.
    * Go into `Network Settings` and grab the library IP. This will be helpful later, so save it somewhere handy.
    * Check that the time is set correctly.
 - [ ] On the `Configuration > System` screen, ensure the following license keys are listed. If not, add them:
    * Tape Series Partitions: `UWY GBM 8MR P9H ZDQ`
    * T950/T950e Capacity: `KMR S4C 4CH 6VL HHG`
    * BlueScale Software Support: `JPN B6Z BBF REQ 4SF`


#### Partition Creation
 - [ ] Create a partition called `LTO5-Red` and add one of the two drives to it.
    * `Configuration > Partitions > Manually create a partition > New`
    * Give the partition a name: `LTO5-Red` and ensure `LTO` is selected for the media type.
    * Choose which controller will handle robotics.
    * Do not choose any spare drives.
    * Set `Storage Chambers` to `24` and `EE Chambers` to `1`.
    * Ensure only one of the drives is selected on the `Chambers and Drives` screen.
    * For `MLM Media Verification` choose `QuickScan`.
    * Choose `Soft Addressing` on the `Fibre Channel Loop IDs` screen.
    * For `Partition Users` select `Allow All`.
    * Select `Port A` for `Robotic Path Visibility`.
    * Choose `Use Soft Address` and `Auto-negotiate` on the `Exporting F-QIP Configuration` screen.
    * There's no reason to save the Library Configuration.
    * Read over the `Save Partition` summary and ensure everything looks okay.
 - [ ] Create a partition called `LTO5-Blue` and add the other drive to it.
    * Use the same settings you did for `LTO5-Red` changing only the name.
 - [ ] Create a cleaning partition called `Mr. Clean`
    * Make sure `LTO Clean` is selected as the Media Type.
 - [ ] Import the red tapes into the `LTO5-Red` partition.
    * `General > Import/Export` - Make sure you select the right partition before beginning the import.
    * The CenterTAP will open up and stick out its tongue. Put a TeraPack magazine into the slot. The arrows on the side of the pack should point inwards and it should seat nicely into the TAP.
    * Once importing, hit continue until you are on your last TeraPack magazine. On the last one, save yourself a cycle and hit `Stop Importing` which isn't clear, but will stop the import cycle after this last magazine.
 - [ ] Import the blue tapes into the `LTO5-Blue` partition.
    * Repeat the import process for the `LTO5-Blue` partition.
 - [ ] Import the cleaning (orange) tape into the `Mr. Clean` partition.

#### Host Setup
 - [ ] Ensure there is a fiber connection between the host and the library.
 - [ ] Ensure there is a network connection to the host.
 - [ ] Log into the host: `labuser/L@buser`
 - [ ] Find the Tester application on the Desktop and launch it.
 - [ ] Perform a `Fast Scan` on the SCSI Tab. Tester should indicate that it has found both your partitions, as well as both drives. If Tester is not reporting anything found during the scan, seek help.
 - [ ] Once the scan is over, open `Library > Low-Level Library Operations > Inventory` to get a look at the library's inventory.
 - [ ] Click on `All Partitions Real World` to start up a simulation of the real world. Watch your library, it should start moving tapes around.

#### Teardown
 - [ ] Clear off the cart so there is room for several magazines.
 - [ ] Export tapes from `LTO5-Red` partition and place on cart.
 - [ ] Export tapes from `LTO5-Blue` partition and place on cart.
 - [ ] Export tape from `Cleaning` partition and place on cart.
 - [ ] `Maintainence > Utilities > Advanced > Remove All Partitions`


