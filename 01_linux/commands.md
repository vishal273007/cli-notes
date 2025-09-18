# Basic Commands

```bash
# File/Directory Information
unzip file.zip # unzip the file in current folder
du -lh file.txt      # file size - l for long listing/foramt and h for human readable
du -sh java(folder_name)       # folder size --- s for summary
ls -l file.txt      # file properties
ls -ld folder       # folder properties
ls -a java(folder)      # List all files includig hidden files

# Multine Commands
 mv HTML 01_html && \
  mv CSS 02_css && \
  mv TEST 03_test

# File Operations
rm *.ext            # Remove all files with specific extension
mv * ~/ui 'OR' [mv .[^.]* * ~/ui]           # Move all files except hidden files to ui directory [for including hidden files as well]
echo "text" > file  # Overwrite file with text (creates if not exists)
echo "text" >> file # Append text to file
touch file1 file2   # Create multiple files simultaneously
rm file1 file2      # Delete multiple files simultaneously

# Navigation & Information
pwd                 # Print working directory
ls -a               # List all files including hidden ones
cd ../..            # Go up two directories
cat filename        # Display file contents

# Directory Operations
cd foldername       # Change directory
mkdir foldername    # Create directory
cp file.txt dest/   # Copy file
cp -r folder dest/  # Copy folder recursively
mv source dest      # Move/rename files or folders

# Useful Commands
sudo !!            # Repeat last command with sudo
Ctrl + z          # Suspend current process
Ctrl + c          # Stop current process
mv filename ..(/folder) - move file in previous folder # move file up one level
```
