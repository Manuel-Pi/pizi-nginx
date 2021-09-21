YUM

- Install NGINX package

- Install Dev Tools to compile NGINX
sudo yum groupinstall "Development Tools"

- Install centOS dependencies
sudo yum pcre pcre-devel zlib zlib-devel openssl openssl-devel

- Configure
./configure --sbin-path=/usr/bin/nginx --conf-path=/etc/nginx/nginx.conf --error-log-path=/var/log/nginx/error.log --http-log-path=/var/log/nginx/access.log --with-pcre --pid-path=/var/run/nginx.pid --with-http_ssl_module

- Compile source
make

- install compile source
make install

- register as service
https://www.nginx.com/nginx-wiki/build/dirhtml/start/topics/examples/systemd/

- enable nginx as service to start on reboot
sudo systemctl enable nginx

- reload config
sudo systemctl daemon-reload
sudo systemctl reload nginx

LOGS

Just use the journalctl command, as in:

journalctl -u service-name.service

Or, to see only log messages for the current boot:

journalctl -u service-name.service -b

For things named <something>.service, you can actually just use <something>, as in:

journalctl -u service-name

give right to user for caching
sudo chown -R ec2-user:ec2-user /var/lib/nginx/