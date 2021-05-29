---
title: "Streams and Files"
excerpt: ""

categories:
  - Computer
tags:
  - C
  - C89
  - C90
  - ANSI C
  - stream
  - file

use_math: true
toc: true 
toc_label: "Table of Contents" 
toc_icon: "cog"
toc_sticky: true 

last_modified_at: 2021-05-29 12:26:00 +0900
---

# §7.9.2 Streams
&nbsp;&nbsp;
Input and output, whether to or from physical devices such as terminals and tape drives, or whether to or from files supported on structured storage devices, are mapped into logical data streams, whose properties are more uniform than their various inputs and outputs. Two forms of mapping are supported, for <i>text streams</i> and for <i>binary streams</i>.<br>

&nbsp;&nbsp;
A text stream is an ordered sequence of characters composed into <i>lines</i>, each line consisting of zero or more characters plus a terminating new-line character. Whether the last line requires a terminating new-line character is implementation-defined. Characters may have to be added, altered, or deleted on input and output to conform to differing conventions for representing text in the host environment. Thus, there need not be a one-to-one correspondence between the characters in a stream and those in the external representation. Data read in from a text stream will necessarily compare equal to the data that were earlier written out to that stream only if: the data consist only of printing characters and the control characters horizontal tab and new-line; no new-line character is immediately preceded by space characters; and the last character is a new-line character. Whether space characters that are written out immediately before a new-line character appear when read in is implementation-defined.

&nbsp;&nbsp;
A binary stream is an ordered sequence of characters that can transparently record internal data. Data read in from a binary stream always equal the data that were earlier written out to that stream, under the same implementation. Such a stream may, however, have an implementation-defined number of null characters appended to the end of the stream.

## Environmental limits

&nbsp;&nbsp;
An implementation shall support text files with lines containing at least 254 characters, including the terminating new-line character. The value of the macro ```BUFSIZ``` shall be at least 256.

# §7.9.3 Files

&nbsp;&nbsp;
A stream is associated with an external file (which may be a physical device) by <i>opening</i> a file, which may involve <i>creating</i> a new file. Creating an existing file causes its former contents to be discarded, if necessary. If a file can support positioning requests (such as a disk file, as opposed to a terminal), then a <i>file position indicator</i> associated with the stream is positioned at the start (character number zero) of the file, unless the file is opened with append mode in which case it is implementation-defined whether the file position indicator is initially positioned at the beginning or the end of the file. The file position indicator is maintained by subsequent reads, writes, and positioning requests, to facilitate an orderly progression through the file. All input takes place as if characters were read by successive calls to the ```fgetc``` function; all output takes place as if characters were written by successive calls to the ```fputc``` function. 

&nbsp;&nbsp;
Binary files are not truncated, except as defined in 7.9.5.3. Whether a write on a text stream causes the associated file to be truncated beyond that point is implementation-defined. 

&nbsp;&nbsp;
When a stream is <i>unbuffered</i>, characters are intended to appear from the source or at the destination as soon as possible. Otherwise characters may be accumulated and transmitted to or from the host environment as a block. When a stream is <i>fully buffered</i>, characters are intended to be transmitted to or from the host environment as a block when a buffer is filled. When a stream is <i>line buffered</i>, characters are intended to be transmitted to or from the host environment as a block when a new-line character is encountered. Furthermore, characters are intended to be transmitted as a block to the host environment when a buffer is filled, when input is requested on an unbuffered stream, or when input is requested on a line buffered stream that requires the transmission of characters from the host environment. Support for these characteristics is 
implementation-defined, and may be affected via the ```setbuf``` and ```setvbuf``` functions. 

&nbsp;&nbsp;
A file may be disassociated from a controlling stream by <i>closing</i> the file. Output streams are flushed (any unwritten buffer contents are transmitted to the host environment) before the stream is disassociated from the file. The value of a pointer to a ```FILE``` object is indeterminate after the associated file is closed (including the standard text streams). Whether a file of zero length (on which no characters have been written by an output stream) actually exists is implementation-defined. 

&nbsp;&nbsp;
The file may be subsequently reopened, by the same or another program execution, and its contents reclaimed or modified (if it can be repositioned at its start). If the ```main``` function returns to its original caller, or if the ```exit``` function is called, all open files are closed (hence all output streams are flushed) before program termination. Other paths to program termination, such as calling the ```abort``` function, need not close all files properly. 

&nbsp;&nbsp;
The address of the ```FILE``` object used to control a stream may be significant; a copy of a ```FILE``` object may not necessarily serve in place of the original. 

&nbsp;&nbsp;
At program startup, three text streams are predefined and need not be opened explicitly —<i>standard input</i> (for reading conventional input), <i>standard output</i> (for writing conventional output), and <i>standard error</i> (for writing diagnostic output). When opened, the standard error stream is not fully buffered; the standard input and standard output streams are fully buffered if and only if the stream can be determined not to refer to an interactive device. 

&nbsp;&nbsp;
Functions that open additional (nontemporary) files require a <i>file name</i>, which is a string. The rules for composing valid file names are implementation-defined. Whether the same file can be simultaneously open multiple times is also implementation-defined. 

## Environmental limits

&nbsp;&nbsp;
The value of ```FOPEN_MAX``` shell be at least eight, including the three standard text streams.

*** 

* References: 
    * Herbert Schildt. (1990). <i>The annotated ANSI C Standard American National Standard for Programming Languages—C: ANSI/ISO 9899-1990</i>. McGraw-Hill, Inc., USA.
