````markdown
# 🐧 Linux Command Cheat Sheet with Real-Time Examples

This markdown document contains categorized Linux commands with real-world usage examples. Suitable for beginners and IT students working with Linux systems.

## 📁 1. Directory and File Management

```bash
mkdir -v myproject                # Create directory and show confirmation
mkdir -p projects/webapp/logs     # Create nested folders
touch notes.txt                   # Create an empty file
ls                                # List files in current directory
ls -l                              # Long format list
ls -lh                             # Human-readable file sizes
ls -lhr                            # Reverse order by name
ls -lhrt                           # Sort by time modified (latest last)
ls -lrthi                          # Show inodes and sorted
cd projects                        # Change into 'projects' directory
cd -                               # Go back to previous directory
pwd                                # Print current directory
tree                               # Show directory tree (install with `sudo apt install tree`)
rm old.txt                         # Remove a file named old.txt
rmdir tempdir                      # Remove an empty directory
cp *.txt backup/                   # Copy all text files to backup directory
mv report.txt report-old.txt      # Rename report.txt to report-old.txt
````

---

## 📄 2. File Viewing and Editing

```bash
cat notes.txt                     # View contents of the file
cat -n notes.txt                  # View with line numbers
cat header.txt > complete.txt     # Overwrite complete.txt with header.txt
cat footer.txt >> complete.txt    # Append footer.txt to complete.txt
vi config.cfg                     # Open config.cfg in vi editor
# Press 'i' to enter insert mode
# Press 'Esc :wq' to save and quit
# Press 'Esc :q!' to quit without saving
# Type ':set nu' to enable line numbers
tail -n 10 /var/log/syslog        # View last 10 lines of syslog
head -n 10 /etc/passwd            # View first 10 lines of passwd file
```
## 👤 3. User and Permissions

```bash
whoami                            # Show current logged-in user
sudo su -                         # Switch to root user
usermod -aG docker john           # Add user 'john' to 'docker' group
```
## 🖥️ 4. Process and System Monitoring

```bash
ps                                # Show current processes for this shell
ps aux                            # Show all processes
pgrep sshd                        # Find PID of sshd service
htop                              # Interactive process monitor (install: sudo apt install htop)
ptree -p                          # Process tree with PIDs (install: sudo apt install psmisc)
free -h                           # View memory usage
df -h                             # Disk usage of all mounted filesystems
du -sh ~/Downloads                # Disk usage of Downloads folder
``

## 🌐 5. Networking and Logs

```bash
netstat -tunl                     # Show active ports and services
lsof -i :8080                     # List processes using port 8080
tcpdump -i eth0 port 443          # Capture HTTPS packets on eth0
journalctl                        # View all system logs
journalctl -u nginx.service       # Logs for NGINX service
journalctl -b                     # Logs since last system boot
```

## ⚙️ 6. System Configuration and Utilities

```bash
hostnamectl set-hostname server01   # Change hostname to server01
wget https://example.com/file.zip   # Download file from the web
tar -zxvf archive.tar.gz            # Extract archive to current directory
```

## 💡 7. Shortcuts and Tips

```bash
Ctrl+C                            # Stop a running command
Ctrl+R                            # Reverse search command history
export PS1="dev $ "              # Change shell prompt to 'dev $ '
```

📝 **Note**: Use `man <command>` to learn more about each command in your terminal.


