guest_ip  = "192.168.0.3"
script = 
"
sudo su -
mv /etc/nginx/conf.d/petshoptomandjerry.com.conf /etc/nginx/conf.d/petshoptomandjerry.com
apt update
apt install nginx -y
rm /etc/nginx/sites-enabled/default
rm /etc/nginx/sites-available/default
rm -r /var/www/html
mv /etc/nginx/conf.d/petshoptomandjerry.com /etc/nginx/conf.d/petshoptomandjerry.com.conf
systemctl reload nginx
"

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.network "private_network", ip: guest_ip
  config.vm.synced_folder "./conf.d", "/etc/nginx/conf.d"
  config.vm.synced_folder "./www", "/var/www"
  config.vm.provision "shell", inline: script
end
