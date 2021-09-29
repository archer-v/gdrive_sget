# gdrive_sget
Simple Unix utility to download public shared files from google drive by file URL or file ID. 
You can't dowload files from Google Drive just using wget or curl.This is a bash script using curl and some additional logic to automate cookies and errors processing while downloading

You can use it to download public Google Drive's shared files without Google Drive API usage and OAuth tokens

### Usage
**./gdrive_sget (URL|fileID) [filename_write_to]**

### Examples
```
    ./gdrive_sget 1eyNA5oZNFhDUzft3Bo-Ud9XR8GAiENXd
    ./gdrive_sget https://drive.google.com/file/d/1eyNA5oZNFhDUzft3Bo-Ud9XR8GAiENXd/view?usp=sharing
    ./gdrive_sget 1eyNA5oZNFhDUzft3Bo-Ud9XR8GAiENXd ./result
```

On succes exit code is 0, curl error codes are passed to the output as is

### Output example:
```
Trying to download the file with id 1eyNA5oZNFhDUzft3Bo-Ud9XR8GAiENXd
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   408    0   408    0     0    495      0 --:--:-- --:--:-- --:--:--   494
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
  0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
100 40.5M    0 40.5M    0     0  7181k      0 --:--:--  0:00:05 --:--:-- 10.7M
200,image/tiff,42514153,test.dump
```
The last line is the status line with the format: HTTP_CODE, MIME-TYPE, DOWLOADED_SIZE, FILE_NAME

### Limitation
Google restricts direct downloading files of some mime-types and with the resourcekey parameter in the download URL. Use utilities interacting with Google Drive API to download these files.
