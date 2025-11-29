# ExifTool

**ExifTool** is a powerful command-line utility for reading, writing, and editing metadata (EXIF, IPTC, XMP, etc.) in a wide variety of file types. It is an essential tool for OSINT investigations, allowing you to extract hidden data from images, documents, and other files.

This guide covers the basic workflow for using ExifTool to analyze a file for hidden intelligence.

---

## 📌 Overview

ExifTool is used for:

*   **Reading Metadata:** Viewing all metadata tags embedded in a file.
*   **Extracting Specific Information:** Filtering for specific data points like GPS coordinates, camera models, or software versions.
*   **Analyzing File History:** Finding timestamps, author information, and copyright notices.
*   **Revealing Hidden Data:** Uncovering comments or other user-added information.

---

## 1. Installation

Debian/Ubuntu:
```bash
sudo apt update && sudo apt install libimage-exiftool-perl
```

Arch:
```bash
sudo pacman -S perl-image-exiftool
```

---

## 2. Basic Usage

To read all available metadata from a file, simply provide the filename as an argument. This command will produce a clean, human-readable list of all tags and their values.

```bash
exiftool <file-name>
```

---

## 3. Example: OhSINT Room

In the OhSINT room on TryHackMe, you are given an image file, `WindowsXP.jpg`. You can use ExifTool to find critical information hidden within it.

```bash
exiftool labs/TryHackMe/rooms/OhSINT/task-files/WindowsXP.jpg
```

Look for interesting tags such as:
*   **Copyright:** May reveal a username or handle.
*   **GPS Position:** If present, provides exact coordinates where the photo was taken.

---

## 4. Common Use Cases & Flags

While the default output is useful, you can use flags to filter the results.

| Goal                                   | Command                               |
| -------------------------------------- | ------------------------------------- |
| **Extract only GPS-related tags**      | `exiftool -gps* <file-name>`          |
| **List metadata by group**             | `exiftool -g1 <file-name>`            |
| **Show tag names, not descriptions**   | `exiftool -s <file-name>`             |
| **Extract a single specific tag**      | `exiftool -Copyright <file-name>`     |

---

## 📚 Notes & Understanding

*   **Not All Files Have Metadata:** Many platforms (like Twitter and Facebook) automatically strip metadata from uploaded images for privacy reasons. A lack of metadata can be as informative as its presence.
*   **Editing and Removing Data:** ExifTool can also be used to remove metadata. For example, to strip all metadata from a file and create a new one:
    ```bash
    exiftool -all= <file-name>
    ```
*   **File Support:** ExifTool supports a huge range of files, not just images. Try it on PDFs, Word documents, and audio files.

