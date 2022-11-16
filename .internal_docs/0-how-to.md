
## Making Updates

1. create new post, and edit from ATOM
```
hugo new posts/postname.md
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
