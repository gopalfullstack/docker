# docker

# 0) Clean any stale creds for the root/sudo context
sudo docker logout || true
sudo rm -f /root/.docker/config.json

# 1) Login as the correct user for the sudo context
sudo docker login -u gopalazcloud
# paste your Docker Hub PAT (NOT your password if 2FA is on)

# 2) Verify login
sudo docker info | grep -i Username
# Expected: Username: gopalazcloud

# 3) Build with new version
sudo docker build -t java17-maven-gradle-git-powershell:4.0.0 .

# 4) Tag for Docker Hub
sudo docker tag java17-maven-gradle-git-powershell:4.0.0 gopalazcloud/java17-maven-gradle-git-powershell:4.0.0

# 5) Push to Docker Hub
sudo docker push gopalazcloud/java17-maven-gradle-git-powershell:4.0.0

# 💡 Optional: also tag as latest
sudo docker tag java17-maven-gradle-git-powershell:4.0.0 gopalazcloud/java17-maven-gradle-git-powershell:latest
sudo docker push gopalazcloud/java17-maven-gradle-git-powershell:latest
