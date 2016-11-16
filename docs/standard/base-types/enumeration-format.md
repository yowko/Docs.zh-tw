---
title: "列舉格式字串"
description: "列舉格式字串"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/25/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 4d581898-99bc-42c3-816c-d8238f45096f
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 8cb811636ca2c7b207f7661e990567b5785bc994

---

# <a name="enumeration-format-strings"></a>列舉格式字串

您可以使用 [Enum.ToString](xref:System.Enum.ToString) 方法來建立新的字串物件，以表示列舉成員的數值、十六進位值或字串值。 這個方法會採用其中一個列舉格式字串，來指定您想要傳回的值。

下列各節列出列舉格式字串及其傳回的值。 這些格式規範不區分大小寫。

## <a name="the-g-or-g-format-strings"></a>G 或 g 格式字串

G 或 g 格式字串會盡可能以字串值來顯示列舉項目；如果不可能，則會顯示目前執行個體的整數值。 如果列舉是使用 `Flags` 屬性集來定義，每個有效項目的字串值會串連在一起，並以逗號分隔。 如果未設定 `Flags` 屬性，則會以數值項目顯示無效的值。 下列範例說明 G 格式規範。

```csharp
Console.WriteLine(ConsoleColor.Red.ToString("G"));         // Displays Red
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("G"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Red.ToString("G"))           ' Displays Red
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("G"))     ' Displays Hidden, Archive
```

## <a name="the-f-or-f-format-strings"></a>F 或 f 格式字串

F 或 f 格式字串會盡可能以字串值來顯示列舉項目。 如果此值可完整顯示為列舉中的項目總合 (即使 `Flags` 屬性不存在)，每個有效項目的字串值會串連在一起，並以逗號分隔。 如果該值不完全取決於列舉項目，則會格式化為整數值。 下列範例說明 F 格式規範。

```csharp
Console.WriteLine(ConsoleColor.Blue.ToString("F"));       // Displays Blue
FileAttributes attributes = FileAttributes.Hidden | 
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("F"));   // Displays Hidden, Archive
```

```vb
Console.WriteLine(ConsoleColor.Blue.ToString("F"))         ' Displays Blue
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("F"))     ' Displays Hidden, Archive
```

## <a name="the-d-or-d-format-strings"></a>D 或 d 格式字串

D 或 d 格式字串會盡可能以最短的整數值表示來顯示列舉項目。 下列範例說明 D 格式規範。

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("D"));         // Displays 11
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("D"));                // Displays 34
````

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("D"))           ' Displays 11
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("D"))                  ' Displays 34 
```

## <a name="the-x-or-x-format-strings"></a>X 或 x 格式字串

X 或 x 格式字串會以十六進位值來顯示列舉項目。 該值可視需要加上前置零來表示，以確保值的長度至少有八位數。 下列範例說明 X 格式規範。

```csharp
Console.WriteLine(ConsoleColor.Cyan.ToString("X"));   // Displays 0000000B
FileAttributes attributes = FileAttributes.Hidden |
                            FileAttributes.Archive;
Console.WriteLine(attributes.ToString("X"));          // Displays 00000022
```

```vb
Console.WriteLine(ConsoleColor.Cyan.ToString("X"))     ' Displays 0000000B
Dim attributes As FileAttributes = FileAttributes.Hidden Or _
                                   FileAttributes.Archive
Console.WriteLine(attributes.ToString("X"))            ' Displays 00000022 
```

## <a name="example"></a>範例

下列範例會定義名為 `Colors` 的列舉，該列舉是由三個項目所組成︰`Red`、`Blue` 和 `Green`。

 ```csharp
 public enum Color {Red = 1, Blue = 2, Green = 3}
```

```vb
Public Enum Color
   Red = 1
   Blue = 2
   Green = 3
End Enum
```

定義列舉之後，可利用下列方式宣告執行個體。

```csharp
Color myColor = Color.Green;
```

```vb
Dim myColor As Color = Color.Green
```

然後可使用 `Color.ToString(System.String)` 方法，根據傳遞給列舉值的格式規範，以不同的方式來顯示列舉值。

```csharp
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("G"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("F"));
Console.WriteLine("The value of myColor is {0}.", 
                  myColor.ToString("D"));
Console.WriteLine("The value of myColor is 0x{0}.", 
                  myColor.ToString("X"));
// The example displays the following output to the console:
//       The value of myColor is Green.
//       The value of myColor is Green.
//       The value of myColor is 3.
//       The value of myColor is 0x00000003.
```

```vb
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("G"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("F"))
Console.WriteLine("The value of myColor is {0}.", _
                  myColor.ToString("D"))
Console.WriteLine("The value of myColor is 0x{0}.", _
                  myColor.ToString("X"))
' The example displays the following output to the console:
'       The value of myColor is Green.
'       The value of myColor is Green.
'       The value of myColor is 3.
'       The value of myColor is 0x00000003. 
```

## <a name="see-also"></a>另請參閱

[格式化類型](formatting-types.md)




<!--HONumber=Nov16_HO1-->


