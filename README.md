# MC EULA
A git repository to view Minecraft [EULA](https://www.minecraft.net/en-us/eula) and [Usage Guidelines](https://www.minecraft.net/en-us/usage-guidelines) changes in a git diff form.
To view the changes, go to the [commits tab](https://github.com/NotFrants/mc-eula/commits/main/).

## ⚠️ Important ⚠️
Commit name is the <ins><i>range of dates when the file was created/edited</i>, <b>not the range of dates when that file was on the website</b></ins>, as that simply can't be found, in the form `YYYYMMDDhhmmss`. The files include the date range in the format `MM/DD/YY hh:mm:ss`.

# General Information

All captures are from the [Wayback Machine](https://web.archive.org/), converted into plaintext, with all whitespace changes are ignored.
The first couple of lines are used for storing information about the file, like the range of dates mensioned above, shown by the

`<------------ start of file info ------------>`, and

`<------------ end of file info ------------>`.

# How its made
## Endpoints used:
`https://web.archive.org/cdx/search/cdx?url=https://www.minecraft.net/en-us/eula&output=json`, and

`https://web.archive.org/cdx/search/cdx?url=https://www.minecraft.net/en-us/usage-guidelines&output=json`

for getting all Wayback Machine captures.

`https://web.archive.org/web/{timestamp}/https://www.minecraft.net/en-us/eula`, and

`https://web.archive.org/web/{timestamp}/https://www.minecraft.net/en-us/usage-guidelines`

for getting each capture. `{timestamp}` is in the format `YYYYMMDDhhmmss`.

## Processing
Each page is downloaded, only the minecraft.net part is selected, and convert to plaintext using the `.get_text()` method in the [bs4](https://pypi.org/project/beautifulsoup4/) Python library.
If a version is different from the previous one, a new difference is created.
