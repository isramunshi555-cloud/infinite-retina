# Infinite Retina — Consulting & Advisory

Responsive service website based on the supplied Seven Voxels concept.

## Files
- index.html: page structure and content
- assets/styles.css: responsive design and graphics styling
- assets/app.js: service explorer, keyboard navigation, FAQ and brief builder
- deploy/nginx.conf: Nginx configuration for the supplied EC2 IP

## Run locally
Open index.html in a browser, or run `python -m http.server 8080` from this directory and visit http://localhost:8080.
No npm dependencies or build step required. Google Fonts is optional; system fonts provide fallback.

## Features
All seven service categories and their supplied subservices; custom SVG graphics; responsive layouts; accessible service tabs; FAQ; downloadable and copyable project briefs.
The brief builder runs locally and does not send enquiries. No backend or database is needed for the current scope.

## GitHub
Create a repository named infinite-retina under your account. Extract this package and run:

```bash
git init
git add .
git commit -m "Build Infinite Retina services website"
git branch -M main
git remote add origin https://github.com/isramunshi555-cloud/infinite-retina.git
git push -u origin main
```
Use GitHub's normal authentication flow when prompted.

## AWS EC2 (Ubuntu)
Connect using EC2 Instance Connect in the AWS console, then run:

```bash
sudo apt update
sudo apt install -y nginx git
```
For a public repository:

```bash
git clone https://github.com/isramunshi555-cloud/infinite-retina.git ~/infinite-retina
sudo install -d -m 755 /var/www/infinite-retina
sudo cp ~/infinite-retina/infinite-retina/index.html /var/www/infinite-retina/
sudo cp -r ~/infinite-retina/infinite-retina/assets /var/www/infinite-retina/
sudo cp ~/infinite-retina/infinite-retina/deploy/nginx.conf /etc/nginx/sites-available/infinite-retina
sudo ln -sfn /etc/nginx/sites-available/infinite-retina /etc/nginx/sites-enabled/infinite-retina
sudo nginx -t
sudo systemctl enable nginx
sudo systemctl restart nginx
curl -I -H 'Host: 16.171.39.126' http://127.0.0.1
```
For a private repository authenticate with GitHub CLI, or upload the extracted package using your own SSH connection instead of cloning anonymously.
Allow inbound TCP 80 in the EC2 security group and open http://16.171.39.126.
If UFW is active, allow Nginx HTTP through it.

The public IP can change after stopping and starting an instance. For a stable URL, use an Elastic IP and domain; update server_name and configure HTTPS for the domain.

## Update the site
```bash
cd ~/infinite-retina
git pull --ff-only
sudo cp infinite-retina/index.html /var/www/infinite-retina/
sudo cp -r infinite-retina/assets /var/www/infinite-retina/
```

## Design update
- Seven coordinated service accent colours with navy, ivory, lavender and mint surfaces.
- Interactive service constellation and seven custom concept SVG illustrations.
- Service content, colours, illustration and suggested flow update together.
- Four interactive process stages with service-specific activities, inputs and proposed outputs.
- Keyboard navigation and reduced-motion support.
- All original services, FAQs and project-brief features retained.

## Deployment status
The original site was deployed on AWS at https://16.171.39.126 with a trusted IP certificate, scheduled Certbot renewal and an Nginx reload hook. The design update requires pulling the latest source and copying the HTML and assets with the update commands above. Do not replace the existing HTTPS Nginx configuration with the original HTTP example in deploy/nginx.conf.

## Validation
JavaScript syntax, seven service renderings, all 28 service/process combinations, and brief generation passed local checks. Visual browser testing of the design update remains to be done.

