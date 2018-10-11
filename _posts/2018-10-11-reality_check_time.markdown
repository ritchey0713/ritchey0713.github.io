---
layout: post
title:      "Reality check time!"
date:       2018-10-11 10:59:10 -0400
permalink:  reality_check_time
---


Since finishing FlatIron, I have set off to build new apps, get familiar with deployment, and learn some new technologies, I have hit several snags! Although this was to be expected while out continuing my learning. It was quite a reality check to sit with errors in my code, that I thought was great to begin with, and have that feeling of not knowing where to turn. Searching high and low for similar issues, and looking through documentation to make sure I hadn't miscalled something I was so stumped! in one year I went from not knowing what Ruby, or React was let a long what a framework was to building a full blown app, and yet, here I was staring at a blank page that should be rendering some data. I have found sometimes sitting there going over the code, and logic doesn't always help to figure out a solution, while going on a brisk walk, it was almost as if someone hit me on the head with a mallet. Not once did I even bother to build a test, nor did I check returns from my fetch promises surely that was the issue!

```

export const grabUser = (userName, platform, history) => {
  console.log("API KEY - ", API_KEY)
  // debugger;
  return dispatch => {
    return fetch(`${API_URL}/SearchDestinyPlayer/${platform}/${userName}`, {
      method: "GET",
      headers: new Headers({
        'Content-Type': 'application/json, charset=utf-8',
        'Origin': '*',
        "X-API-Key": API_KEY
      }),
      mode: 'cors'
    })
      .then(response => response.json())
      // .then(user => {
      //   dispatch(getUser(user))
      // })
      .then(response => {
        dispatch(setUserName(userName))
        dispatch(getProfile(response.Response[0]))
      })
      .then(history.push('/profile'))
      .catch(err => console.log(err))

  }
}

const getProfile = (user) => {
  // /Destiny2/{membershipType}/Profile/{destinyMembershipId}/?components=???
  // https://www.bungie.net/Platform/Destiny2/2/Profile/4611686018475843998/?components=200
  console.log(user)
  let membershipId = parseInt(user.membershipId)
  //debugger;
  return dispatch => {
    return fetch(`${API_URL}/${user.membershipType}/Profile/${user.membershipId}/?components=200`, {
      method: "GET",
      headers: new Headers({
        'Content-Type': 'application/json, charset=utf-8',
        'Origin': '*',
        "X-API-Key": API_KEY
      }),
      mode: 'cors'
    })
      .then(response => response.json())
      .then(user => {
        let characters = []
        let data = user.Response["characters"]["data"]
        for (let character in data) {
          characters.push(data[character])
        }
        dispatch(getUser(characters))
      })
      .catch(err => console.log(err))
  }
}
```
I had a lot going on in here, and I forgot something i learned which was very important, never assume data is what you expect. After many, many console.logs, and debugger sessions, I nailed it, i needed to chain my fetches together inside an action, not string them along in a compoment! Huzzah! To some this may seem like a silly issue to have, but this has been my first wake up call since being ready to start networking to kick off my career, I hope if you are reading this, you never ever take using your debugging tools for granted like i had been!
