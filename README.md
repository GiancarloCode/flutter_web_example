# flutter_web_example--An Amazing Flutter Project For Beginners 

🔥🚀 In This Tutorial I Will Teach you How To Create Your First Web App Using Flutter📲 And Use GitHub Actions To Automatically Deploy It To GitHub Pages Every Time You Push To The Repository.


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
