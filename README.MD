# Project Title

## Description

A brief description of what this project does and who it's for.

## Installation

Provide step by step series of examples and explanations about how to get a development environment running.

```bash
git clone <repo>
cd <project>

Usage
Provide instructions and examples for use.

python main.py

Contributing
Instructions on how to contribute, style guide, etc.

License
Information about the license.
```

Remember to replace the placeholders with your specific information.

## Notes:

### models.js

This file defines three classes: Story, StoryList, and User, which are used to interact with a story sharing API.

The 'Story' class represents a single story in the system. It has a constructor that takes an object with properties 'storyId', 'title', 'author', 'url', 'username', and 'createdAt', and assigns these properties to the instance. There's also a 'getHostName' method, which is intended to parse the hostname out of the story's URL, but it's currently unimplemented and just returns a placeholder string.

The 'StoryList' class represents a list of 'Story' instances. It has a constructor that takes an array of stories and assigns it to the instance. The getStories static method is used to fetch a list of stories from the API, create Story instances from the returned data, and return a StoryList instance containing these stories. The addStory method is intended to add a new story to the API and the story list, but it's currently unimplemented.

The User class represents a user in the system. It has a constructor that takes an object with properties username, name, createdAt, favorites, and ownStories, and a token, and assigns these to the instance. The favorites and ownStories properties are arrays of stories, which are converted into Story instances. The signup and login static methods are used to register a new user with the API and log in an existing user, respectively. They make a request to the API, create a User instance from the returned data, and return this instance. The loginViaStoredCredentials static method is used to log in a user when their token and username are already known. It makes a request to the API, creates a User instance from the returned data, and returns this instance. If the request fails, it logs the error and returns null.

#### n.b. re: 'static' keyword

```
static async getStories() {
    const response = await axios({
        url: `${BASE_URL}/stories`,
        method: "GET",
    });
}
```

In JavaScript, the static keyword defines a static method for a class. Static methods aren't called on instances of the class. Instead, they're called on the class itself.

In the context of the getStories function in your code, the static keyword means that getStories is a method that belongs to the class it's defined in, not to any instance of that class.

This is why you can call getStories directly on the class, like so: ClassName.getStories(), without having to create an instance of the class first.

The getStories method doesn't make sense as an instance method because it's not working with an instance of the class. It's getting a list of stories, which is a general action that doesn't depend on the state of any specific instance.
