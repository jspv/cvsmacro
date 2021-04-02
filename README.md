# CVS Vaccine Finder ui.vision RPA Example

This is a modified macro demonstrating how to use ui.vision to periodically check for local COVID19 vaccine availability at CVS locations.  The macro checks the CVS website for availability for a configurable number of locations.  If availability is found, it will force Chrome into focus, sound an alarm, and send a push notification by Pushover.

## Installation and Use

This was built using the UI.Vision Chrome extension and can be imported using the "Import JSON or .Zip" option in the UI.Vision GUI (folder with '+' sign logo)

### Customize appropriately

The macro is set for the current (as of 3/28/2001) Massachusetts form and chooses options for someone with two qualifying medical conditions; obviously this may need to be changed.  

The macro uses Pushover to send a notification when availability is found; if you don't use Pushover, go ahead and remove the two lines which send the pushover messages.

Variables to set:

  * PUSHOVERTOKEN: replace with your pushover token (or remove the line)

  * PUSHOVERUSER: replace with your pushover id (or remove the line)

  * ZIP1,ZIP2,ZIP3: replace with zip codes to check, feel free to add/remove zip codes into the array

  * AGE: replace with your age

### Flow

The macro has a main loop that resets the browser and fully reloads the webpages, the main loop has a 60 second pause between each run to ensure we're being friendly to CVS.  

Each main loop has a sub-loop which checks each zip code for availability and watches for either the scheduling form or the no-availably response; if neither response is received after a few sections, the loop is aborted and the main loop reloaded.  

### Disclaimers

I did this to experiment with UI.Vision after watching a family member constantly checking the website; I had absolutely no experience Selenium/UI.Vision and put this together in about an hour.  Undoubtably there are much more efficient ways to do this.  

## License

[MIT](https://choosealicense.com/licenses/mit/)

This project is licensed under the MIT License.

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
