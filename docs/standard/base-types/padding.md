---
title: "填補字串"
description: "填補字串"
keywords: ".NET、.NET Core"
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 73452c1f432fb8cb50a36e739fb91962693f8e51

---

# <a name="padding-strings"></a>填補字串

使用下列 [System.String](xref:System.String) 方法之一建立由原始字串所組成的新字串，此原始字串填補的前置或後置字元是指定的總長度。 填補字元可以是空格或指定的字元，最後要靠右或靠左對齊。

方法名稱 | 用法
----------- | ---
[String.PadLeft](xref:System.String.PadLeft(System.Int32)) | 以指定總長度的前置字元填補字串。
[String.PadRight](xref:System.String.PadRight(System.Int32)) | 以指定總長度的後置字元填補字串。

## <a name="padleft"></a>PadLeft

[String.PadLeft](xref:System.String.PadLeft(System.Int32)) 方法是將足夠的前置填補字元串連到原始字串，達到指定的總長度，來建立新的字串。 [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) 方法使用空白字元作為填補字元，而 [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) 方法則讓您指定自己的填補字元。

下列程式碼範例使用 [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) 方法建立長度為 20 個字元的新字串。 此範例會在主控台顯示 "`--------Hello World!`"。

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a>PadRight

[String.PadRight](xref:System.String.PadRight(System.Int32)) 方法是將足夠的後置填補字元串連到原始字串，達到指定的總長度，來建立新的字串。 [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) 方法使用空白字元作為填補字元，而 [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) 方法則讓您指定自己的填補字元。

下列程式碼範例使用 [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) 方法建立長度為 20 個字元的新字串。 此範例會在主控台顯示 "`Hello World!--------`"。

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a>另請參閱

[基本字串作業](basic-string-operations.md)




<!--HONumber=Nov16_HO1-->


