# Solution (Jolly CI/CD)

The following is to be done on the *Jolly CI/CD* terminal beside **Rippin Proudboot**.  

When talking to **Tinsel Upatree** after completing *[Prison Escape](./Prison_Escape.md)*, he mentioned the following mistake he made in a git commit on the following git repository:  
**http://gitlab.flag.net.internal/rings-of-powder/wordpress.flag.net.internal.git**

![](./res/jolly_tinsel_commit.png)

Enter the terminal and run the following git command to clone the repository:  
`git clone http://gitlab.flag.net.internal/rings-of-powder/wordpress.flag.net.internal.git` -- if it does not work, wait a few more minutes before trying again.

![](./res/jolly_git_clone.png)

go into the repository and check the git log:  
```
cd workpress.flag.net.internal/
git log
```

![](./res/jolly_git_log.png)

We see a commit saying **whoops**, that hinted that **Tinsel Upatree** used this commit to fix the mistake he made in the previous commit, hence we search the log in the previous commit:  
`git diff abdea0ebb21b156c01f7533cea3b895c26198c98`

![](./res/jolly_ssh_key.png)


An SSH private key belonging to the author!  
Next we create a private_key file, move it into `.ssh` directory:  
```
mkdir ~/.ssh
cd ~/.ssh
cat << EOF > id_rsa
-----BEGIN OPENSSH PRIVATE KEY-----
b3BlbnNzaC1rZXktdjEAAAAABG5vbmUAAAAEbm9uZQAAAAAAAAABAAAAMwAAAAtzc2gtZW
QyNTUxOQAAACD+wLHSOxzr5OKYjnMC2Xw6LT6gY9rQ6vTQXU1JG2Qa4gAAAJiQFTn3kBU5
9wAAAAtzc2gtZWQyNTUxOQAAACD+wLHSOxzr5OKYjnMC2Xw6LT6gY9rQ6vTQXU1JG2Qa4g
AAAEBL0qH+iiHi9Khw6QtD6+DHwFwYc50cwR0HjNsfOVXOcv7AsdI7HOvk4piOcwLZfDot
PqBj2tDq9NBdTUkbZBriAAAAFHNwb3J4QGtyaW5nbGVjb24uY29tAQ==
-----END OPENSSH PRIVATE KEY-----
EOF
chmod 400 id_rsa
```

![](./res/jolly_id_rsa.png)

We then use the key with the Author's identity **sporx@kringlecon.com** to re-clone the repository:  
```
mkdir ~/new_repo
cd ~/new_repo
git clone git@gitlab.flag.net.internal:rings-of-powder/wordpress.flag.net.internal.git
```

![](./res/jolly_new_clone.png)

