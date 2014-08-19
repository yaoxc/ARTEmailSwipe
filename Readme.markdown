ARTEmailSwipe
===

ARTEmailSwipe is a UIViewController container which allows you to have one view controller at the bottom, whilst keeping your main navigation seperate. This is based on the iOS 8 emails implementation where you can have your new email open at the bottom whilst still viewing all your old emails, above it. I also took a lot of insipiration from the JASidePanels project which is what this was based on. 

Demo
---
![iPhone Example](https://img.skitch.com/20120322-dx6k69577ra37wwgqgmsgksqpx.jpg)
![iPad Example](https://img.skitch.com/20120322-ttu951nfb8cpd5ti5r1ni8428y.jpg)

Example 1: Code
---

```  objc

#import "ARTEmailSwipe.h"

@implementation AppDelegate

@synthesize window = _window;
@synthesize viewController = _viewController;

- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    self.window = [[UIWindow alloc] initWithFrame:[[UIScreen mainScreen] bounds]];
	
	self.viewController = [[ARTEmailSwipe alloc] init];
  
  // you will want to use your own custom classes here, but for the example I have jsut instantiated it with the UIViewController class.
	self.viewController.centerViewController = [[UIViewController alloc] init];
	self.viewController.bottomViewController = [[UIViewController alloc] init];
  
	self.window.rootViewController = self.viewController;
    [self.window makeKeyAndVisible];
    return YES;
}

@end

```

Example 2: Storyboards
---

1. Create a subclass of `ARTEmailSwipe`. In this example we call it `ARTRootViewController`.
2. In the Storyboard designate the root view's owner as `ARTRootViewController`.
3. Make sure to `#import "ARTEmailSwipe.h"` in `ARTRootViewController.h`.
4. Add more view controllers to your Storyboard, and give them identifiers "centerViewController" and "bottomViewController".
5. Add a method `awakeFromNib` to `ARTRootViewController.m` with the following code:

```  objc

-(void) awakeFromNib
{
  [self setLeftPanel:[self.storyboard instantiateViewControllerWithIdentifier:@"centerViewController"]];
  [self setCenterPanel:[self.storyboard instantiateViewControllerWithIdentifier:@"bottomViewController"]];
}

```

Usage
---

If you are not using cocoapods yet then here is a link http://cocoapods.org.
To install using cocoapods just add the below to your Podfile,

    pod 'ARTEmailSwipe'
  
If you are not using cocoapods check out that link again :)
Or just add ARTEmailSwipe class and UIViewController+ARTEmailSwipe category to your project.


Requirements
---

ARTEmailSwipe requires iOS 7.0+ and Xcode 4.3+ The projects uses ARC, but it may be used with non-ARC projects by setting the: ` -fobjc-arc ` compiler flag on ` ARTEmailSwipe.m `. You can set this flag under Target -> Build Phases -> Compile Sources

License
---

```

 Permission is hereby granted, free of charge, to any person obtaining a copy of
 this software and associated documentation files (the "Software"), to deal in
 the Software without restriction, including without limitation the rights to
 use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
 of the Software, and to permit persons to whom the Software is furnished to do
 so, subject to the following conditions:
 
 The above copyright notice and this permission notice shall be included in all
 copies or substantial portions of the Software.
 
 If you happen to meet one of the copyright holders in a bar you are obligated
 to buy them one pint of beer.
 
 THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
 AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
 SOFTWARE.
 
 ```

Insipiration
---
A big shout has to go to the JASidePanels project which is what I based this on.

* JASidePanels - [https://github.com/gotosleep/JASidePanels](https://github.com/gotosleep/JASidePanels)