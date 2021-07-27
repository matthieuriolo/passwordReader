# passwordReader

Mac OSX High Sierra has an annoying bug that passwords saved in the section "local items" cannot be exported or moved to a different keychain. The only possibility to move those passwords is over the iCloud or copy&paste them manually. And no, they cannot exported through the bash command `security` neither. 

The file local-items.txt contains an [AppleScript](https://developer.apple.com/library/archive/documentation/AppleScript/Conceptual/AppleScriptLangGuide/introduction/ASLR_intro.html) which copies all entries from the application [Keychain Access](https://support.apple.com/guide/keychain-access/what-is-keychain-access-kyca1083/mac). It was a 4 hours fun project - dont expect it to be the best solution or simply to "work"

## Usage
- Open the application [Keychain Access](https://support.apple.com/guide/keychain-access/what-is-keychain-access-kyca1083/mac)
- Select the item "Local Items" in Keychain Access
- Open the application [Script Editor](https://support.apple.com/guide/script-editor/welcome/mac)
- Copy the content of the file `local-items.txt` to the script editor
- Insert your password in the code (property definition on the first line)
- Run the code in the Script Editor
- Be patient!!! It takes like ~10 seconds for one password to be copied
- The script editor will output all the collected domain, username and passwords

## How does it work
Essentially the AppleScript does what you manually would do:
- For every table entry do the following steps
- Open information of the table entry
- Make password visible
- copy&paste the credentials

## Stability
- The code is not even close to perfect!
- Make sure to make a backup before hand (better safe than sorry).
- Some passwords cannot be copied - in my case it were the credit cards which could not been copied.
- If you have a different version of macosx you might not need to use this script or the script will not work at all
