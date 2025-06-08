# Basic Commands

```bash
# File/Directory Information
du -h file.txt      # Check txt file size
du -sh folder       # Check folder size
ls -l file.txt      # Check file properties
ls -ld folder       # Check folder properties
ls -a foldername    # List all files includig hidden files

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
