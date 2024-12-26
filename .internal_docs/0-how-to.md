
## Making Updates

1. create new post, and edit from ATOM
```
hugo new posts/postname.md    # for papermod theme
hugo new blog/2023_mia.md     # for intro theme 
```

2. test deploy locally
```
hugo server -D
```

3. if happy, deploy to Firebase & update Git
```
hugo && firebase deploy
git add .
git commit -m "notes"
git push
```



## Issue triage

Force firebase reauth (following are terminal cli commands)
1. firebase login
2. firebase login --reauth
3. firebase projects:list
   - this last command should list ideashare site as a project
