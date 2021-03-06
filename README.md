The `format` library contains support for different file-formats for the Haxe programming language.

Formats
=======

Currently supported formats are :

  * ABC (Flash AS3 bytecode format)
  * AGAL (Adobe Shader Assembler for Stage3D - writer only atm)
  * AMF (Flash serialized object)
  * AS1 (Adobe ActionScript1-2 bytecode in SWF - reader only atm)
  * BC (LLVM Bitcode format)
  * BMP (Bitmap Image format)
  * CLASS (Java class file)
  * FLV (Flash Video)
  * GZ (compressed file)
  * JPG (Image file format - writer only atm)
  * MP3 (compressed audio)
  * NEKO (NekoVM bytecode)
  * PBJ (PixelBender Binary file)
  * PDF (only generic file structure and partial decryption)
  * PNG (image file format)
  * SWF (Flash file format)
  * TAR (Archive)
  * TGZ (TAR+GZ Archive)
  * WAV (Raw sound)
  * ZIP (Compressed Archive)

Installation
============

Available on haxelib, simply run the following command : `haxelib install format`. To use the library, simply add `-lib format` to your commandline parameters.

Package Structure
=================

Each format lies in its own package, for example `format.pdf` contains classes for PDF.

The `format.tools` package contain some tools that might be shared by several formats but don't belong to a specific one.

Each format must provide the following files :
  * one `Data.hx` file that contain only data structures / enums used by the format. If there is really a lot, they can be separated into several files, but it's often my easy for the end user to only have to do one single `import format.xxx.Data` to access to all the defined types.
  * one `Reader.hx` class which enable to read the file format from an `haxe.io.Input`
  * one `Writer.hx` class which enable to write the file format to an `haxe.io.Output`
  * some other classes that might be necessary for manipulating the data structures

It's important in particular that the data structures storing the decoded information are separated from the actual classes manipulating it. This enable full access to all the file format infos and the ability to easily write libraries that manipulate the format, even if later the Reader implementation is changed for example.
