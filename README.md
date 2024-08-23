# IPA Keyboard Website
This is the website that allows you to type the IPA characters.

## Usage of the Program/Website
### With Client [Outdated Tutorial Video](https://youtu.be/Dq0mX-xQkGM)
Note: This only works when BOTH DEVICES are connected to a UD network (i.e. on-campus or connected to the [UD VPN](https://udeploy.udel.edu/software/anyconnect-vpn/)).
- Download the appropriate executable file (do this on the computer that you want the characters to be sent to).
- You can find all of the releases [here](https://github.com/codeBodger/IPA_Keyboard_Client_with_Robot/releases).
- Click on the first release in the list (this is the newest) and download the appropriate file:
  - For Windows: download the Windows executable file and run it.
  - For MacOS: download the MacOS executable file and run it.
  - For Linux: sorry, this isn't supported yet.&nbsp; You'll need to download the source and get all of the dependencies yourself.&nbsp; The information in the release should be helpful.
- Run the executable.
- Go to the [login page](https://phonetics.ling.udel.edu/login) on the device that you want to type on.
- Enter the linking code that was generated when you ran the program or clicked `Get New Linking Code` into the text box and click `Login`.
- The program should be working now!&nbsp; Simply click the buttons and the characters should appear on the computer that you ran the executable on.
- After an hour of inactivity, you will be timed out.
  - To reactivate the existing link(s), simply press `Renew` on the Client.
- If you want to type from multiple devices onto one computer:
  - Press `Get New Linking Code` on the Client, and type it into the [login page](https://phonetics.ling.udel.edu/login) as previously.
- Whenever you close (or `Stop`) and reopen/rerun the Client, you will have to `Logout` and re`Login` on the website in all locations.
### Copy and Paste (without Client / on one Device)
- Go to either [phonetics.ling.udel.edu](https://phonetics.ling.udel.edu/) or [codeBodger.github.io/IPA_Keyboard_Website](https://codebodger.github.io/IPA_Keyboard_Website/).
- Click `Logout` if necessary.
- Click the buttons and the characters should appear in the text box.
- Then click `Copy` to copy them to your clipboard.
### General Usage Information
- You can use the purple buttons above the chart to select only certain sub&#x2011;charts.&nbsp; You may want to do this if your screen is particularly small.
- The slider directly above the chart can be used to adjust the scaling of the chart.&nbsp; This is helpful if your screen has a different aspect ratio.

## Questions, Comments, and Issues
- Queries and comments can be directed to [rnackerm+ipa@udel.edu](rnackerm+ipa@udel.edu).
- Additionally, I'll try to regularly check the [Issues](https://github.com/codeBodger/IPA_Keyboard_Client_with_Robot/issues) on [my GitHub](https://github.com/codeBodger), so if you have an acutal issue, I suggest this.
[comment]: Make sure to update this everywhere.
- Alternatively, if you're in LING 202 with me (you probably know if you are), you can stop me after class, and I'll try to answer your questions then.

## Technical Details
This is the Website that users will use to type.&nbsp; After inputting the linking-code generated by the [Client](https://github.com/codeBodger/IPA_Keyboard_Client_with_Robot?tab=readme-ov-file#readme) into the login page of this website on their secondary device, the user can tap/click the buttons on the chart to type the characters.&nbsp; If the user inputs an invalid linking-code, they are alerted.&nbsp; After the linking-code is input successfully, the long-code that was generated when the [Client](https://github.com/codeBodger/IPA_Keyboard_Client_with_Robot?tab=readme-ov-file#readme) was run is sent from the [Router Server](https://github.com/codeBodger/IPA_Keyboard_Router_Server?tab=readme-ov-file#readme) to this Website, completing the linking. 

If the user does not have a secondary device, they can also copy and paste the symbols directly from this Website. 

When the user presses a button (and is logged in), this Website sends data containing the key-code for the button pressed and the long-code to the [Backend](https://github.com/codeBodger/IPA_Keyboard_Website_Backend?tab=readme-ov-file#readme).&nbsp; If the user is not “logged in”, this will not be sent, so as not to send unnecessary data.

Whenever any data is sent from this Website, it is prepended by a string describing the activity, which the [Backend](https://github.com/codeBodger/IPA_Keyboard_Website_Backend?tab=readme-ov-file#readme) uses to determine what to do with the data (either treat it like a linking-code or like a key-code followed by a long-code).&nbsp; The activity is separated from the data with a backslash.

### Definitions
|               |                                                                                        |
| ------------- | -------------------------------------------------------------------------------------- |
| Key‑code:     | the three digit<sub>10</sub> (000-164) code representing a single IPA character        |
| Key‑byte:     | the key-code as a single byte (typically implicitly casted to `int`)                   |
| Long‑code:    | the 18 digit<sub>64</sub> code to indicate which client a key-byte needs to be sent to |
| Linking‑code: | the six digit<sub>10</sub> code to get the long-code from Router Server to Website     |
