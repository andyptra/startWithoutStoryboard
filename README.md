# startWithoutStoryboard
start xcode project without storyboard and XIB as Main Screen

## Step
- First Remove Main.storyboard
- Remove reference to Main.storyboard from Deploy Info<br/>
  At general tab -> Deploy Info -> main interface field (delete and leave blank)
- Remove  the key Storyboard Name <br/>
  At info tab -> Application Scene Manifest (expand) ->  Scene Configuration (expand) -> Application Session Role (expand) -> First Item 
- Add this code inside SceneDelegate.swift<br/> this include navigationController
```swift
   guard let windowScene = (scene as? UIWindowScene) else { return }
           window = UIWindow(frame: windowScene.coordinateSpace.bounds)
           window?.windowScene = windowScene
        let navigationController = UINavigationController(rootViewController: MainScreenViewController());
      
           window?.rootViewController = navigationController
           window?.makeKeyAndVisible()
```
Replace MainScreenViewController() to your name of XIB file<br/>
- And launch your app. 
