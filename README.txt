## SHttpd by Omar Al-Sakka

## Problems...
Currently breaks 1.1 compliance when running cgi(s),
will add a chomp function to cleanup entered text.

need to do many more checks, but (ref point 1).

## Required Declerations, please customize
## Those to your machine. (try whereis <bin name>).

sys_cat="/bin/cat"
root_dir="/rez/httpd/www_root"
std_index="index.html"
deny_file="deny_list"
tmp_dir="/rez/httpd/tmp"
log_dir="/rez/httpd/log"
sys_file_id="/usr/bin/file -ib"
sys_split="/usr/bin/cut"
delete_file="/bin/rm"
stat_uri="/usr/bin/stat -t"
sys_date=`/bin/date -uR`
session="$$$RANDOM"
webmaster="postmaster"

## SHttp Directory structure.
## bin/  log/  tmp/  www_root/

 bin - shttpd script resides here.
 log - logs are written here.
 tmp - temporary files are created here.
 www_root - the web server root directory.

## To Run
## Xinetd

service http
{
  disable          = no
  protocol         = tcp
  port             = 80
  flags            = REUSE
  socket_type      = stream
  wait             = no
  user             = nobody
  instances        = 128
  server           = <ENTER_DIR_HERE>/httpd/bin/httpd
  max_load         = 99
  log_on_failure  += USERID
}


