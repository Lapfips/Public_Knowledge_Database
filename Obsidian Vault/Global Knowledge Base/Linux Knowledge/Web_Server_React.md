# Web server procedure

## Configrue Apache

- Install Apache2 packages

```bash
sudo apt install apache2
```

- Check Apache2 service status

```bash
sudo systemctl status apache2.service
```

- Try to connect with IP address

```http
http://<your_ip_address>
```

- Install ssh

```bash
sudo apt install ssh
```

- Set your own website -> Connected on ssh transfert the built website

```bash
scp <path_to_your_website> <server_username>@<server_IP_address>:/var/www/html<path_your_want_to_specified>
```

## Configure MariaDB

- Create a specific user to acces the database

```bash
adduser DATABASE_ACCES
```

# Automated script :

```bash
sudo apt install apache2 -y
sudo apt install ssh -y
sudo apt install git -y

ssh-keygen -t ed25510

cat ~/.ssh/id_ed25519.pub

echo "Pass this key on github -> github.com/settings/keys"

read -p "Enter your built website github repository link:" WEBSITE_GITHUB_REPO

read -p "Where do you want to implement this website ? ( press enter for default /var/www/html ) " WEBSITE_LOCAL_PATH

if [[ ! -z $WEBSITE_LOCAL_PATH ]]; then
    WEBSITE_LOCAL_PATH="/var/www/html"
    rm -rf /var/www/html
fi

git clone $WEBSITE_GITHUB_REPO $WEBSITE_LOCAL_PATH

```
