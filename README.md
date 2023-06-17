# RealityKit-Gravity
SwiftUI and RealityKit 
# The first part
![IMG_0160](https://github.com/S-way520/RealityKit-Gravity/assets/95877651/ec049566-a9dc-45cf-9a95-6f41dc221ab3)
# The second part
Code file 1
```swift
import SwiftUI
@main
struct MyApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
Code file 2
```swift
import SwiftUI
import RealityKit
struct ContentView: View {
    var body: some View {
        ARViewContainer()
            .edgesIgnoringSafeArea(.all)
    }
}
struct ARViewContainer: UIViewRepresentable {
    func makeUIView(context: Context) -> ARView {
        let arView = ARView(frame: .zero)
        let anchorEntity = AnchorEntity(plane: .horizontal)
        
        let SphereEntity = ModelEntity(mesh: MeshResource.generateSphere(radius: 0.2/5), materials: [SimpleMaterial(color: .blue, isMetallic: true)])//实体2 Entity2(球体Sphere)
        SphereEntity.physicsBody = PhysicsBodyComponent(massProperties: .default, material: .default, mode: .dynamic)//物理行为
        SphereEntity.generateCollisionShapes(recursive: true)
        SphereEntity.position = simd_float3(0.2/2,0.8,0)
        
        anchorEntity.addChild(SphereEntity)
        arView.scene.addAnchor(anchorEntity)
        return arView
    }
    func updateUIView(_ uiView: ARView, context: Context) {
    }
}
```
