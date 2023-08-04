To add multiple custom repositories to the Pacman configuration file (`/etc/pacman.conf`), you can use a script that appends the repository information to the end of the configuration file. Here's a simple bash script to achieve this:




Replace the example URLs with the actual URLs of your custom repositories. Save the script to a file (e.g., `add_custom_repos.sh`), and then make the script executable:




To run the script and add the custom repositories to `pacman.conf`, execute the following command:




Please make sure to review the URLs and ensure that you trust the sources before adding them to your Pacman configuration. Adding untrusted or unknown repositories can compromise the security and stability of your system. Always use caution when adding custom repositories.