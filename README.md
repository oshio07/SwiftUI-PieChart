# SwiftUI-PieChart

'Swift Charts' presented at WWDC 2022 do not support pie charts. So try this one!

## Installation

### Swift Package Manager

1. File -> Add Packages... -> Search or Enter Package URL
```
https://github.com/ashleymills/Reachability.swift
```

2. Select `Up to Next Major Version` for Dependency Rule

##### OR

1. Add the following to your `Package.swift` files `dependencies` array.
```
.package(url: "https://github.com/tristanhimmelman/ObjectMapper.git", .upToNextMajor(from: "0.1.0"))
```

## Usage

### Import

 ```swift
import PieChart
```

### Examples

#### Sample Data Source

```swift
    var fruits = [
        (name: "apple", count: 10, color: Color.red),
        (name: "orange", count: 9, color: Color.orange),
        (name: "banana", count: 8, color: Color.yellow)
    ]
    
    var fruitsCountList: [Int] { fruits.map { $0.count } } // [10, 9, 8] 
```

The following numbers are tied to numbers in the image at the top.

#### 1.
```swift
    PieChart(
        // Array of Int, Double, Float, etc.
        values: fruitsCountList
    )
```

#### 2.
```swift
    PieChart(
        values: fruitsCountList,
        // Specify colors. If not specified, the default color set is applied.
        colors: [.red, .orange, .yellow]
    )

    // or    

    // Another instantiation.
    // All the same parameters can be used.
    PieChart(fruits) { fruit in
        Item(
            value: fruit.count,
            color: fruit.color
        )
    }
```

#### 3.
```swift
    PieChart(
        fruits,
        // To set the background color, use this parameter instead of the ViewModifier.
        backgroundColor: .black
    ) {
        Item(
            value: $0.count,
            color: $0.color
        )
    }
```

 #### 4.
 ```swift
    PieChart(
        values: fruitsCountList,
        // 0~1.0 Space between each slice.
        // Default value: 0
        config: Config(space: 0.5)
    )
```

####  5.
 ```swift
    PieChart(
        values: fruitsCountList,
        // 0~1.0 Donut pie chart.
        // Default value: 0
        config: Config(hole: 0.6)
    )
```

 #### 6.
 ```swift
    PieChart(
        values: fruitsCountList,
        config: Config(space: 0.5, hole: 0.6)
    )
```

 #### 7.
 ```swift
    PieChart(
        values: [Int](repeating: 1, count: 7),
        backgroundColor: .gray,
        config: Config(
            // 0~1.0 Ratio of pie chart size to View size.
            // Default value: 0.8
            pieSizeRatio: 1
        )
    )
    .border(.black, width: 1)
    .frame(width: 75, height: 75)
```

#### 8.
```swift
    PieChart(
        values: [Int](repeating: 1, count: 7),
        backgroundColor: .gray,
        config: Config(
            pieSizeRatio: 0.5
        )
    )
    .border(.black, width: 1)
    .frame(width: 150, height: 150)
```

#### 9.
```swift
    // All parameters.
    PieChart(
        values: [Int](repeating: 1, count: 7),
        colors: [.red, .orange, .yellow, .green, .cyan, .blue, .purple],
        backgroundColor: .black,
        config: Config(
            space: 0.3, hole: 0.5, pieSizeRatio: 0.7
        )
    )
    .cornerRadius(30)
    .frame(width: 150, height: 150)
```

# License
MIT
