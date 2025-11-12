# Push PR Command

Perform the following steps:

1. Read the current number from dummycommit.txt
2. Increment the number by 1
3. Write the new number back to dummycommit.txt
4. Stage and commit the changes with the message "Increment counter to [new_number]"
5. Push the changes to a new branch named "increment-[new_number]" to both GitHub and GitLab remotes
6. Create a GitHub pull request with:
   - Title: "Increment counter to [new_number]"
   - Body: "This PR increments the counter in dummycommit.txt from [old_number] to [new_number]"
   - Use the gh CLI tool
7. Create a GitLab merge request with:
   - Title: "Increment counter to [new_number]"
   - Description: "This MR increments the counter in dummycommit.txt from [old_number] to [new_number]"
   - Use the glab CLI tool

Return the URLs for both the GitHub PR and GitLab MR when complete.
