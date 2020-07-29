# SFTP vs. HTTPS - What they are, and why ThreatSwitch only uses HTTPS

**Brief Intro**

In my role as Head of Engineering at ThreatSwitch I find myself working with customers on topics such as Single Sign On (SSO) and "integrations" on a regular basis.  From my vantage it is clear various SSO protocols, mostly SAML, but some OIDC as well have gained traction at the enterprise level. However, the issue of data integrations, especially in the context of REST APIs is still unfamiliar terittory for many of our customers.

This is problematic as a common request we are hearing is the issue of syncing HR data to ThreatSwitch's database on a recurring basis.  For customers with thousands of employees keeping critical information about their status is a mission critical problem with particular sensitivity in the Industrial Security industry that ThreatSwitch operates in **Could elaborate here, also, bad sentence **.

In recent conversations with customers we've learned that standard practice for data transfer is "SFTP w/ PGP encryption". blah blah blah

## SFTP

Secure File Transfer Protocol
From the 90s
Specific to Files
Uses SSH 
Allows transfer of any file to a remote server via SSH.

Creates problems of data in transfer
Issues of permissions, logging, failover, access monitoring, data isolation, and transfer all arise
Effectively creates a backdoor into ThreatSwitch

Mostly authenticated via username and password.

SFTP w/ PGP is most appropriate for transfering files between parties in one off transfers, but for regularly occurring 

## HTTPS

HTTP is the protocol of the internet.  HTTPS is the way to do it securely.

HTTPS is not limited to file transfers, files are simply data represented in a particular format.  If you exist in the world of HTTPS you can handle data transfer of any type, including absolutely massive "data firehouses".  HTTPS effectively makes SFTP irrelevant in a modern Web Application perspective.

HTTPS is the only protocol supported by ThreatSwitch by design and we are proud of that fact.  443 is the only port open on all of ThreatSwitch's production servers.  

We don't even allow SSH into our production servers as we 

In this section, write a few sentences that will set the tone and direction for your post. For example, your draft intro could look something like this:
The way we communicate has changed. Now, conversations start around content.
Find Altimeter Group quote about Culture of Content
Find Social Media usage stats
By empowering employees to share content strategically, you’re investing in your employees, your brand, and consumer trust.
Add a few more thoughts…
Finish off the intro section with a question. This will help frame the next point.

## [Header #1: First Point]

This is your first segway into the hard-hitting point of your blog. After prefacing the post with your intro, use this section to write an initial point that leads to the meat of the article.
For example, after writing an introduction centered around content strategy across the enterprise, a first point might be something like “Content Serves A Purpose.” You would then proceed to write a couple paragraphs about how and why content serves a purpose.
Your last sentence should lead into your next post. Sometimes it’s easier to finish a section with a thought-provoking question.
[Header #2-4: Body]
The next few headers should lead readers through your different arguments that support the statements you make in your intro and first header. For example, if we continue with the flow of the intro and header #1 of “Content Serves A Purpose,” the following could be headers that would lead readers through a story:
Data Is Your Knowledge Source For Content
Sharing Knowledge And Insights With Your Team
Proceed with the same as your first point, and fill out the sections with a few paragraphs.
[Next Header: Main Point/Hitting Point]
This is the section of your body where you hit the readers with the main idea behind your post. This section is usually where you would add a bit of a soft sales pitch, or add something highly controversial. You want readers to react at to this point (think of it as an AHA! moment).
An example heading could be “The Knowledge Library – A Tool Designed For Your Employees.” This would be the main selling point of the article, based on the intro and headings presented above.
At the end of this section, finish off with a statement that reinforces the readers that they now understand the value behind your idea, but how do they do it. E.g. “Now you understand the value content can bring to your organization and employees. But what features would a Knowledge Library need?”

## [Heading: Actionable Tips]
After presenting the main ideas and theories for your post, it’s good to leave people with a few actionable tips. For stuff that’s a bit more proprietary, present tips in the form of questions.
To make this section easier to read, add one or two paragraphs at the start of the section, then present the tips in bullet points.
A few examples for headings in this section (following the headings presented previously) could be:
What Features Should A Knowledge Library Have?
What Content Should You Include In A Knowledge Library?
After presenting your bullets, finish off this section with a brief paragraph.

## [Closing Thoughts]
This section should briefly recap the main ideas of your post, but it isn’t meant to be a summary. Adding a provocative statement, your own opinion on the topic, a couple of examples (or case studies), etc., will help close of your post and make you look like a thought leader.

## [List of questions]
Always close of the post with 2-3 questions the readers should think about when they leave.

## [CTA]
Add some sort of call to action. If it’s a post meant to generate leads, you might want to add a button or a link to request a demo. If the post is a bit more on the thought leadership side, you might want to encourage people to leave a comment or feedback and ask them to share with colleagues.



