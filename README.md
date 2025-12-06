# MythTV Comskip

A Perl script for flagging commercials in MythTV recordings using Comskip.

## Version 2.1.0

## Features

- **Unique temp directories** - Each run creates a unique temporary directory to prevent conflicts
- **Command line options** - Support for --help, --version, --noclean, and --localtime
- **Local time conversion** - Use --localtime to specify times in your local timezone
- **Modular code** - Well-organized, maintainable codebase with clear functions
- **Better error messages** - Detailed error messages for easier debugging
- **Show-based temp dirs** - Temporary directories include the show name for easy identification

## Usage

```bash
mythcomskip [OPTIONS] <JOBID> <CHANID> <STARTTIME>
```

### Options

- `--help, -h` - Display help message
- `--version, -v` - Display version information
- `--noclean` - Keep temporary files (don't delete temp directory)
- `--localtime, -l` - Interpret STARTTIME as local time (default: UTC)

### Arguments

- **JOBID** - MythTV job ID (use 0 if not running as a job)
- **CHANID** - Channel ID
- **STARTTIME** - Recording start time (UTC by default, or local with --localtime)
  - Format: YYYYMMDDhhmmss (e.g., 20231206143000)

## Examples

### Using UTC time (default)
```bash
mythcomskip 0 1203 20251204010000
```

### Using local time with conversion
```bash
mythcomskip --localtime 0 1203 20251203200000
```

### Keep temp files for debugging
```bash
mythcomskip --noclean 0 1203 20251204010000
```

## Configuration

Edit the following variables at the top of the script:

- `$myth_dir` - MythTV recordings directory (default: /mnt/mythtv)
- `$config_dir` - Comskip configuration directory (default: /home/mythtv/code/mythtv-comskip)
- `$db_name`, `$db_host`, `$db_user`, `$db_pass` - Database connection settings

## Requirements

- Perl 5
- DBI module
- File::Temp module
- Getopt::Long module
- POSIX module
- Time::Local module
- Comskip
- MythTV database access

## Installation

1. Copy the `mythcomskip` script to your desired location
2. Make it executable: `chmod +x mythcomskip`
3. Configure the script variables for your system
4. Run manually or integrate with MythTV's job queue

## Changelog

### Version 2.1.0
- Unique temp directory for each run (prevents conflicts)
- Added command line options (--help, --version, --noclean, --localtime)
- Local time to UTC conversion support
- Refactored code into modular functions
- Improved error messages
- Show title included in temp directory names
- Clean, consistent code formatting

## License

This project is provided as-is for use with MythTV.
