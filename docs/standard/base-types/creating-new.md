---
title: "建立新字串"
description: "建立新字串"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 639397c7-e694-43e0-845b-1681c62bd9fd
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 793b5bc4b26967104459fa2559c6127bb82f3a9d
ms.lasthandoff: 03/02/2017

---

# <a name="creating-new-strings"></a>建立新字串

.NET 允許使用簡單的指派來建立字串，並且還可以多載類別建構函式，以支援使用多個不同參數來建立字串。 .NET 也在 [System.String](xref:System.String) 類別中提供幾個方法，藉由組合多個字串、字串陣列或物件的方式來建立新的字串物件。 

## <a name="creating-strings-using-assignment"></a>使用指派建立字串

建立新的 [String](xref:System.String) 物件的最簡單方式，是將字串常值直接指派給 [String](xref:System.String) 物件。 

## <a name="creating-strings-using-a-class-constructor"></a>使用類別建構函式建立字串

您可以使用 [String](xref:System.String) 類別建構函式的多載，從字元陣列建立字串。 您也可以讓某個特定字元重複指定的次數，藉此建立新字串。 

## <a name="methods-that-return-strings"></a>傳回字串的方法

下表列出數個可傳回新字串物件的有用方法。

方法名稱 | 用法
----------- | ---
[String.Format](xref:System.String.Format(System.String,System.Object)) | 從一組輸入物件建立格式化的字串。
[String.Concat](xref:System.String.Concat(System.String,System.String)) | 從兩個或多個字串建立字串。
[String.Join](xref:System.String.Join(System.String,System.String[])) |藉由組合字串陣列來建立新字串。
[String.Insert](xref:System.String.Insert(System.Int32,System.String)) | 藉由將字串插入現有字串的指定索引中來建立新字串。
[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32)) | 將字串中的指定字元複製到字元陣列中的指定位置。

### <a name="format"></a>格式

您可以使用 `String.Format` 方法，建立格式化的字串和串連代表多個物件的字串。 這個方法會自動將任何傳遞的物件轉換為字串。 例如，如果您的應用程式必須向使用者顯示 [Int32](xref:System.Int32) 值和 [DateTime](xref:System.DateTime) 值，您可以使用 `Format` 方法，輕鬆地建構出代表這些值的字串。 如需搭配此方法使用之格式慣例的資訊，請參閱[複合格式](composite-format.md)一節。

下列範例會使用 `Format` 方法來建立使用整數變數的字串。

```csharp
int numberOfFleas = 12;
string miscInfo = String.Format("Your dog has {0} fleas. " +
                                "It is time to get a flea collar. " + 
                                "The current universal date is: {1:u}.", 
                                numberOfFleas, DateTime.Now);
Console.WriteLine(miscInfo);
// The example displays the following output:
//       Your dog has 12 fleas. It is time to get a flea collar. 
//       The current universal date is: 2008-03-28 13:31:40Z.
```

```vb
Dim numberOfFleas As Integer = 12
Dim miscInfo As String = String.Format("Your dog has {0} fleas. " & _
                                       "It is time to get a flea collar. " & _ 
                                       "The current universal date is: {1:u}.", _ 
                                       numberOfFleas, Date.Now)
Console.WriteLine(miscInfo)
' The example displays the following output:
'       Your dog has 12 fleas. It is time to get a flea collar. 
'       The current universal date is: 2008-03-28 13:31:40Z.
```

在此範例中，[DateTime.Now](xref:System.DateTime.Now) 會以和目前執行緒關聯的文化特性中所指定的方式來顯示目前日期和時間。

### <a name="concat"></a>Concat

使用 `String.Concat` 方法可以輕鬆地從兩個或多個現有物件，建立新的字串物件。 它提供與語言無關的方式來串連字串。 這個方法接受衍生自 `System.Object` 的任何類別。 下列範例會從現有的兩個字串物件和一個分隔字元建立字串。

```csharp
string helloString1 = "Hello";
string helloString2 = "World!";
Console.WriteLine(String.Concat(helloString1, ' ', helloString2));
// The example displays the following output:
//      Hello World!
```

```vb
Dim helloString1 As String = "Hello"
Dim helloString2 As String = "World!"
Console.WriteLine(String.Concat(helloString1, " "c, helloString2))
' The example displays the following output:
'      Hello World!
```

### <a name="join"></a>Join

`String.Join` 方法會從字串陣列和分隔符號字串建立新的字串。 如果您想要將多個字串串連在一起，建立以逗號分隔的清單，這個方法會很有用。

下列範例會使用空格來繫結字串陣列。

```csharp
string[] words = {"Hello", "and", "welcome", "to", "my" , "world!"};
Console.WriteLine(String.Join(" ", words));
// The example displays the following output:
//      Hello and welcome to my world!
```

```vb
Dim words() As String = {"Hello", "and", "welcome", "to", "my" , "world!"}
Console.WriteLine(String.Join(" ", words))
' The example displays the following output:
'      Hello and welcome to my world!
```

### <a name="insert"></a>Insert

`String.Insert` 方法會將字串插入另一個字串中的指定位置，藉此建立新的字串。 這個方法會使用以零起始的索引。 下列範例會將字串插入 `MyString` 的第五個索引位置，並使用這個值來建立新的字串。

```csharp
string sentence = "Once a time.";   
 Console.WriteLine(sentence.Insert(4, " upon"));
 // The example displays the following output:
 //      Once upon a time.
```

```vb
Dim sentence As String = "Once a time."   
 Console.WriteLine(sentence.Insert(4, " upon"))
 ' The example displays the 
```

### <a name="copyto"></a>CopyTo

`String.CopyTo` 方法會將部分字串複製到字元陣列中。 您可以同時指定字串的開頭索引和要複製的字元數。 這個方法會使用來源索引、字元陣列、目的索引和要複製的字元數。 所有索引都是以零起始。

下列範例會使用 `CopyTo` 方法，將 "Hello" 這個字的所有字元從字串物件複製到字元陣列的第一個索引位置。

```csharp
string greeting = "Hello World!";
char[] charArray = {'W','h','e','r','e'};
Console.WriteLine("The original character array: {0}", new string(charArray));
greeting.CopyTo(0, charArray,0 ,5);
Console.WriteLine("The new character array: {0}", new string(charArray));
// The example displays the following output:
//       The original character array: Where
//       The new character array: Hello
```

```vb
Dim greeting As String = "Hello World!"
Dim charArray() As Char = {"W"c, "h"c, "e"c, "r"c, "e"c}
Console.WriteLine("The original character array: {0}", New String(charArray))
greeting.CopyTo(0, charArray,0 ,5)
Console.WriteLine("The new character array: {0}", New String(charArray))
' The example displays the following output:
'       The original character array: Where
'       The new character array: Hello
```

## <a name="see-also"></a>另請參閱

[基本字串作業](basic-string-operations.md)

[複合格式](composite-format.md)


