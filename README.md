# flutter_web_example--An Amazing Flutter Project For Beginners 

🔥🚀 In This Tutorial I Will Teach you how to create your first Web App Using Flutter📲 and use GitHub Actions to automatically deploy it to GitHub Pages every time you push to the repository.


### 📚 Tutorial: https://www.youtube.com/watch?v=UAeoRJ-eTUo

### 🖥️ Demo: https://giancarlocode.github.io/flutter_web_example/#/

## Workflow

`.github/workflows/flutter_web.yaml`
```yaml
name: Flutter Web

on:
  push:
    branches:
      - master
      
jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - name: Checkout
      uses: actions/checkout@v2
      
    - name: Setup Flutter
      uses: subosito/flutter-action@v1
      with:
        channel: 'beta'
        
    - name: Enable Flutter web 
      run: flutter config --enable-web
      
    - name: Install dependencies
      run: flutter packages get
      
    - name: Build web
      run: flutter build web
      
    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        github_token: ${{ secrets.token }}
        publish_dir: ./build/web
```
