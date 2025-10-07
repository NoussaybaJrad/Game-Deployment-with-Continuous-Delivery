# Build-a-Game-with-Continuous-Deployment-to-S3

## Description

This project demonstrates how to **build and deploy a game using a fully automated CI/CD pipeline** from GitHub to an AWS S3 bucket.  
The game is hosted as a static website, and every push to the GitHub repository automatically triggers deployment via **AWS CodePipeline** to S3.  

**Key AWS Services Used:**  
- **AWS S3** – Hosts the static game website  
- **AWS CodePipeline** – Automates continuous deployment from GitHub to S3  
- **GitHub** – Source repository for the game code  
- **IAM** – Provides secure permissions for CodePipeline and S3 integration  

---

## Architecture Overview

1. **S3 Bucket Creation**
   - Created a bucket named `mymemegame`.  
   - Disabled **block public access** to allow browser access.  
   - Enabled **static website hosting** on the bucket.  
   - Added a bucket policy to allow public read access to objects.

2. **GitHub Repository**
   - Game source code is stored on GitHub.  
   - Branch used for deployment: `main`.  
   - Every push to `main` triggers deployment.

3. **CodePipeline Setup**
   - Created a pipeline called `memepipeline`.  
   - Created a new **service role** to grant necessary permissions.  
   - Configured **GitHub as the source provider** and connected the repository.  
   - Set pipeline trigger on push to the `main` branch.  
   - No build provider used (direct deployment).  
   - Deployed artifacts to the `mymemegame` S3 bucket with **extract files before deploy** option enabled.

4. **Testing Deployment**
   - Opened the website hosted on S3 to verify it loads successfully.  
   - Edited `index.html` and pushed to GitHub to confirm the pipeline triggers and redeploys the updated game.

---

## Environment and Languages Used

- **AWS Console Management** (latest version)  
- **VS Code** (text editor)  
- **HTML/CSS/JavaScript** – Front-end game code  
- **GitHub** – Source control and repository  

---

## File Structure & How the Code Works

### Front-end (`index.html`)
- Contains the main game logic and UI.  
- Any edits to `index.html` automatically trigger the CI/CD pipeline to redeploy the website.

### Script (`script.js`)
- Handles game functionality and interactions.  
- Connected to `index.html` and deployed to S3 alongside HTML.  

### CI/CD Pipeline (CodePipeline)
- **Source Stage:** Monitors GitHub repository for changes.  
- **Deploy Stage:** Deploys new commits to the `mymemegame` S3 bucket.  
- Automatically overwrites previous website files when triggered.

### S3 Bucket
- Serves as the **static website host**.  
- Publicly accessible via the S3 endpoint.  
- Contains all front-end game files (HTML, CSS, JS, assets).  

---

## Full Demo & Screenshots
For a complete walkthrough, including **full-resolution screenshots and screen recordings**, visit my Google Drive folder:  
[View Project Media](https://drive.google.com/drive/folders/1E_z2Buwws95WgyFjHqdpXdyOjj-_qvtH?usp=sharing)
