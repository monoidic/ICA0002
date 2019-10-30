# Webserver
Most of the configuration is on the git repo. The database is handled seperately.
HTML/CSS/JS/PHP/other textual content could be put in a seperate git repository for ease of backups
as well as version management, while binary content (images, fonts, PDFs etc.) would be
"backed up" by CDNs as well as on the backup server. Though this would mean that binary data
that is currently needed (some, such as the company logo, would be stored indefinitely)
would have to be seperated from binary data that is no longer in use
(and may be cleaned up after the retention period) if storage space is to be conserved.

# Database
The database could be backed up in the form of SQL dumps sent to the backup server(s).

# DNS master & slave
These do not currently have to be backed up as their configurations are managed
through ansible/git. As far as I can tell, the rndc key would only have to be backed up
if management through rndc was planned, though any changes done over it would seemingly
get overwritten by updates pushed by ansible.

# Backup server itself
The scripts/configurations that make up the backup server are stored on the git repo
and thus does not need to be backed up seperately. The backup data stored on the server
should exist on other backup servers as well to stop it from being a single point of failure,
of course.

# Ansible/other git repos
These would be maintained as full git clones from a on-site git server. Forced git pushes
may have to be eliminated to prevent issues.


All in all, textual data/configurations would be stored in the form of fully cloned git repos,
indefinitely/until the data related to the repository is deemed unneeded,
while binary data would be stored as-is.
