# Explain Code

There are 5 steps to take whenever you instruct the reader to write some code:

1. **What and Why**: Explain **what** you are trying to accomplish, and **why** you are taking this approach.
2. **Where**: Explain **where** to add the code in detail.
3. **Code**: Put the **code** the user should add.
4. **How**: Explain **how** the code works in detail, along with commentary on why it is useful or other insight.
5. **Build & Run** \[Optional]: If possible, command the reader to build & run the project, and show a screenshot. This ends the current instruction section; now move onto the next section.

### **Comment Code Blocks**

If you have a code block that needs more than one paragraph to explain, you should comment on different lines in the code block and include an ordered list to explain the code section by section.

`import SpriteKit class GameScene: SKScene {`\
``\
&#x20; `// 1`\
``\
&#x20; `let player = SKSpriteNode(imageNamed: "player")`\
``\
&#x20; `override func didMoveToView(view: SKView) {`\
``\
&#x20;   `// 2`\
&#x20;   `backgroundColor = SKColor.whiteColor()`\
``\
&#x20;   `// 3`\
&#x20;   `player.position = CGPoint(x: size.width * 0.1, y: size.height * 0.5)`\
``\
&#x20;   `// 4`\
&#x20;   `addChild(player)`\
&#x20; `}`\
`}`

Let’s go over this step-by-step.

1. Here you declare a private constant for the player (i.e. the ninja), which is an example of a sprite. As you can see, creating a sprite is easy - simply pass in the name of the image to use.
2. Setting the background color of a scene in Sprite Kit is as simple as setting the **backgroundColor** property. Here you set it to white.
3. You position the sprite to be 10% across vertically and centered horizontally.
4. To make the sprite appear on the scene, you must add it as a child of the scene. This is similar to how you make views children of other views.

### **Include Only New Code**

Expect your readers to cut and paste your code blocks directly into their IDE.

This means you shouldn’t show existing code in the block unless you’re instructing them to replace an entire function or method. Instead, tell them exactly where to place the new code.

For example:

Add the following lines to `animateTransition(using:)`:

`guard let fromVC = transitionContext.viewController(forKey: .from),` \
`let toVC = transitionContext.viewController(forKey: .to),` \
`let snapshot = fromVC.view.snapshotView(afterScreenUpdates: false) else {`\
&#x20; `return`\
`}`

### **Use TODOs in Your Starter Project**

If the explanation for where to add the new code is too difficult or too wordy, include a comment in the starter project or an earlier code block that you can use as a signpost.

For example, the block below would go in the starter project, not the article:

`func animateTransition(using transitionContext: UIViewControllerContextTransitioning) {` \
&#x20; `// TODO: Add more here...` \
`}`

You can then instruct the readers to “Add the following to `animateTransition(using:)` after `// TODO: Add more code here...`” and then include your new block of code.
