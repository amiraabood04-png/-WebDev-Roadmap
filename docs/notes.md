
# Technical Notes

## Biggest Docker Challenge

During this assignment, I faced a dependency synchronization
problem while building the Docker image.

The Docker build failed at the `npm ci` step because
`package-lock.json` was missing the required yaml@2.9.1
dependency.

I solved this by updating the lockfile using the Node.js
environment inside Docker, then rebuilding the image.

After the fix, the Docker image built successfully and
the container started on port 8080.

## Most Important Git/GitHub Lesson

The most important lesson I learned was understanding
the difference between git add, git commit, and git push.

- git add prepares changes for the next commit.
- git commit saves a snapshot of the changes locally.
- git push uploads commits to GitHub.

I also learned how to use meaningful commit messages
to document project progress professionally.
