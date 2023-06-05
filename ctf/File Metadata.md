## File Metadata

[What is Metadata in the real world?](https://ssd.eff.org/en/module/why-metadata-matters)
Read [this](https://ctf101.org/forensics/what-is-metadata/)

Metadata is often described as everything *except* the the content of your communications. You can think of metadata as the digital equivalent to an envelope. Some examples of metadata include:
- the subject line of your mails
- the length of your conversations
- the time frame in which a conversation took place
- your location while communicating (as well as with whom)
Services like Tor hope to limit the amount of metadata that is produced via common online communication methods.

### Metadata
Metadata is data about data. Different type of files have different metadata. The metadata on a photo could include dates, camera information, GPS location, comments etc. For music it could include the title, author track number and album.

One of the best tool to find metadata is `exiftool`

#### Timestamps
Timestamps are data that indicate the time of certain events (MAC):
- Modification: When a file was modified
- Access: When a file or entries were read or accessed.
- Creation: When files or entries were created.

**Why should we care ?**
Certain events such as creating, copying, moving, opening, editing etc. Might affect the MAC times. If the MAC timestamps can be attained, a timeline of the events could be created.

[This](http://exif.regex.info/) is a great online exiftool but is not available at the moment.

### insomni-hack-ctf-2015/forensic

We are give an image.

`exiftool` reveals it contains 4787 bytes thumbnail image. To extract it:

```bash
$ exiftool -binary -ThumbnailImage zoomIn_3a3f6e35934021eca75b0abde70333a6.jpg > thumbnail_0.jpg
```
 A further metadata inspection with `exiftool` reveals the thumbnail file itself contains a 26822 bytes thumbnail image. Extract it again
```bash
$ exiftool -binary -ThumbnailImage thumbnail_0.jpg > thumbnail_1.jpg
```
The flag is visible (mirrored) in `thumbnail_1.png`.