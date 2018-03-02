Git allows to "re-write" history using git rebase command. Re-writing history includes multiple operations in git world. The one I am particularyly interested in describing today is how to reorder git commits. Suppose you have two git commits which are like this 

>>git log -2 <br>
1234: "second commit message"<br>
5678: "first commit message"

Now, for some reason, you want to reorder it to look something like this. One reason why you might want to do that is because you want to push commit with id 1234 first. Git will not allow you to do that until you reorder your commits like this

>>git log -2<br>
5678: "first commit message"<br>
1234: "second commit message"

Here is what you should do

>>git rebase -i HEAD~2 <br>
pick 5678: "second commit message" <br>
pick 1234: "first commit message"

What this command will do is open an interactive mode where you will see something like this

Notice that this order is different than the order of commits shown by git log command. Now, all you have to do is move these lines in the order you want your commits to look like. Once you are done. hit save and you will exit the git editor. To see how your commits now look, hit git log -2 and you will see the right order.

For further reading - https://git-scm.com/book/en/v2/Git-Tools-Rewriting-History
