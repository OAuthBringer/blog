# Redux WTF? : Building Front-end Applications in React w/ Redux
I’ve been working on React w/ Redux applications at production scale for several years now and I am asked a lot of questions about patterns and practices for developing them.  Understanding Redux and the role it plays is critical for successful application development and it is one of the biggest stumbling blocks for developers new to React.

The first time you run into Redux concepts of “Action”, “Reducer”, and “Dispatch” or see big chunks of a React app dedicated to these definitions you’ll probably end up scratching your head.  The first time I stumbled onto these at a job I became incredibly frustrated because all I wanted to do was make an HTTP request and get some effing data so I could try my hand at working with react.

In fact, my introduction to Redux in the context of HTTP requests made me think Redux was some sort of stupid HTTP client. 

As it turns out that’s not at all what Redux is about.  It is playing a much more general role that turns out to be critical for large front-end applications.

So, this all leads us to the critical question -  WTF is Redux and why do we use it?

## Redux is how you manage state

1. State definition - This is surprisingly hard.
1. This is anything from user profile data, authentation state, errors, 
1. React components can manage state - Limitations 

### "The Redux Store"

1. Your state container / store is a simple JSON object
1. The state of your application changes deterministically when updated by actions.
1. Transition through immutable states is directed by actions.
1. MVP store example

```
{
    "post": {
        "id": 1, 
        title: "Redux WTF? : Building Front-end Applications in React w/ Redux", "description": "Technical writing is hard", 
        "body": "Lots of ranting would go here."
    }
}
```

### Subscribe to the store using "connect()"

1. The store allows you to connect different parts of your application to the same state.
1. It allows you to change the underlying state with actions
1. It allows you to update parts of your application that rely on state
1. Example connected component
2. 

```
// This is a pure functional, stateless component
export const Post = ({title, description, id} = {}) => {
    return (
        <div id={id}>
            <h2>{title}</h2>
            <h3>{description}</h3>
            {body}
        </div>
    )
}

// This maps the value of {post} from the redux store
const mapStateToProps = ({post}) => ({...post})
// This is the connected Component that is "subscribed" to any changes
// to "post" in the store.
export default connect(mapStateToProps)(Post)
```
### Update components by issuing actions

1. 





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
[Heading: Actionable Tips]
After presenting the main ideas and theories for your post, it’s good to leave people with a few actionable tips. For stuff that’s a bit more proprietary, present tips in the form of questions.
To make this section easier to read, add one or two paragraphs at the start of the section, then present the tips in bullet points.
A few examples for headings in this section (following the headings presented previously) could be:
What Features Should A Knowledge Library Have?
What Content Should You Include In A Knowledge Library?
After presenting your bullets, finish off this section with a brief paragraph.
[Closing Thoughts]
This section should briefly recap the main ideas of your post, but it isn’t meant to be a summary. Adding a provocative statement, your own opinion on the topic, a couple of examples (or case studies), etc., will help close of your post and make you look like a thought leader.
[List of questions]
Always close of the post with 2-3 questions the readers should think about when they leave.
[CTA]
Add some sort of call to action. If it’s a post meant to generate leads, you might want to add a button or a link to request a demo. If the post is a bit more on the thought leadership side, you might want to encourage people to leave a comment or feedback and ask them to share with colleagues.




