The risks of single maintainer dependencies
-------------------------------------------

This will be about golang cobra package which permits creating beautiful CLI (we use it for `inspektor-gadget`).

The maintainer has all rights on the repository and can merge PR.
A "solo maintainer" is an indivual, or small group of individuals, maintaining a project with little to no support.

During the war between Internet Explorer and Netscape, occuring in 1995, the goal of Netscape was to add the Java VM to the browser.
A developper of Netscape (called Brandon) wrote the Java VM in 10 days.
Sadly, they were not a community, so the project dies.
Indeed, no one actually write Java applet.

According to the author, the maintainers **are** the secure software supplychain.

The original maintainer of the `event-stream` npm package, which is quite used, did not maintain the package anymore and gives rights to maintaining to someone who asked to get the rights.
But the new maintainer added code to mine cryptocurrency in this package...

A solo maintainer must have double factor authorization.
The speaker also advised to not be the "solo hero walking in the sunset" and to take people into.
You should write documentation in case you abandon it so someone can become new maintainer.

In the case of cobra, if the maintainer account is comprised, k8s CLI will be compromised too (as well as `inspektor-gadget`).
An incentive model is a system to encourage desired behaviour.
According to the speaker without an incentive models, everything else risks falling apart.

As a conclusion, the speaker says that: "any solo maintainer dependenciy is a risky one".
