---
title: "修剪和移除字串中的字元"
description: "修剪和移除字串中的字元"
keywords: .NET, .NET Core
author: stevehoag
manager: wpickett
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 95d818bc-2661-43f6-adb8-13b53abf9682
translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 96cf08c0de8ba73d931d561187369ccf8b091651

---

# <a name="trimming-and-removing-characters-from-strings"></a>修剪和移除字串中的字元

如果您將句子剖析成個別文字，最後可能會得到許多文字，但文字任一端有空格 (也稱為空白字元)。 在這種情況下，您可以使用 [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) 類別中的其中一個 Trim 方法，從字串中的指定位置移除任意數目的空格或其他字元。 下表描述可用的 Trim 方法。

方法名稱 | 用法
----------- | ---
[String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) | 將字元陣列中字串開頭和結尾指定的空格或空白字元移除。
[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) | 從字串尾端移除字元陣列中指定的字元。
[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) | 從字串開頭移除字元陣列中指定的字元。
[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) | 從字串中指定的索引位置移除指定的字元數。


## <a name="trim"></a>Trim

您可以使用 [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) 方法，輕鬆地移除字串頭尾的空格，如下列範例所示。

```csharp
string MyString = " Big   ";
Console.WriteLine("Hello{0}World!", MyString);
string TrimString = MyString.Trim();
Console.WriteLine("Hello{0}World!", TrimString);
//       The example displays the following output:
//             Hello Big   World!
//             HelloBigWorld!
```

```vb
Dim MyString As String = " Big   "
Console.WriteLine("Hello{0}World!", MyString)
Dim TrimString As String = MyString.Trim()
Console.WriteLine("Hello{0}World!", TrimString)
' The example displays the following output:
'       Hello Big   World!
'       HelloBigWorld!
```

您也可以將字元陣列中字串開頭和結尾指定的字元移除。 下列範例將會移除空白字元、句號和星號。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String header = "* A Short String. *";
      Console.WriteLine(header);
      Console.WriteLine(header.Trim( new Char[] { ' ', '*', '.' } ));
   }
}
// The example displays the following output:
//       * A Short String. *
//       A Short String
```

```vb
Module Example
   Public Sub Main()
      Dim header As String = "* A Short String. *"
      Console.WriteLine(header)
      Console.WriteLine(header.Trim( { " "c, "*"c, "."c } ))
   End Sub
End Module
' The example displays the following output:
'       * A Short String. *
'       A Short String
```

## <a name="trimend"></a>TrimEnd

[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 方法會從字串結尾移除字元，並建立新的字串物件。 系統會將字元陣列傳遞給這個方法，以指定要移除的字元。 字元陣列中的項目順序不會影響修剪作業。 一旦找到陣列中未指定的字元時，修剪作業就會停止。

下列範例會使用 TrimEnd 方法，移除字串的最後一個字母。 在此範例中，`'r'` 字元和 `'W'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。 請注意，此程式碼會移除 `MyString` 的最後一個字以及第一個字的一部分。

```csharp
string MyString = "Hello World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

此程式碼會讓主控台顯示 `He`。

下列範例會使用 [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 方法，移除字串的最後一個文字。 在這個程式碼中，`Hello` 文字後接一個逗號，不過由於要修剪的字元陣列中未指定逗號，因此修剪作業會在逗號處停止。

```csharp
string MyString = "Hello, World!";
char[] MyChar = {'r','o','W','l','d','!',' '};
string NewString = MyString.TrimEnd(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello, World!"
Dim MyChar() As Char = {"r","o","W","l","d","!"," "}
Dim NewString As String = MyString.TrimEnd(MyChar)
Console.WriteLine(NewString)
```

此程式碼會讓主控台顯示 `Hello,`。

## <a name="trimstart"></a>TrimStart

[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) 方法與 [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 方法類似，只是它會移除現有字串物件開頭的字元以建立新字串。 系統會將字元陣列傳遞給 [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) 方法，以指定要移除的字元。 使用 [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 時，字元陣列中的項目順序不會影響修剪作業。 一旦找到陣列中未指定的字元時，修剪作業就會停止。

下列範例會移除字串的第一個文字。 在此範例中，`'l'` 字元和 `'H'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。

```csharp
string MyString = "Hello World!";
char[] MyChar = {'e', 'H','l','o',' ' };
string NewString = MyString.TrimStart(MyChar);
Console.WriteLine(NewString);
```

```vb
Dim MyString As String = "Hello World!"
Dim MyChar() As Char = {"e","H","l","o"," " }
Dim NewString As String = MyString.TrimStart(MyChar)
Console.WriteLine(NewString)
```

此程式碼會讓主控台顯示 `World!`。

## <a name="remove"></a>移除

[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) 方法會從現有字串中的指定位置開始，移除指定的字元數。 這個方法會假設以零為起始的索引。

下列範例會於字串中以零為起始之索引的位置五開始，從字串中移除 10 個字元。

```csharp
string MyString = "Hello Beautiful World!";
Console.WriteLine(MyString.Remove(5,10));
// The example displays the following output:
//         Hello World!  
```

```vb
Dim MyString As String = "Hello Beautiful World!"
Console.WriteLine(MyString.Remove(5,10))
' The example displays the following output:
'         Hello World!
```

您也可以從字串中移除指定的字元或子字串，方法是呼叫 [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) 方法並指定空字串 ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) 做為取代。 下列範例將會從字串中移除所有逗號。

```csharp
using System;

public class Example
{
   public static void Main()
   {
      String phrase = "a cold, dark night";
      Console.WriteLine("Before: {0}", phrase);
      phrase = phrase.Replace(",", "");
      Console.WriteLine("After: {0}", phrase);
   }
}
// The example displays the following output:
//       Before: a cold, dark night
//       After: a cold dark night
```

```vb
Module Example
   Public Sub Main()
      Dim phrase As String = "a cold, dark night"
      Console.WriteLine("Before: {0}", phrase)
      phrase = phrase.Replace(",", "")
      Console.WriteLine("After: {0}", phrase)
   End Sub
End Module
' The example displays the following output:
'       Before: a cold, dark night
'       After: a cold dark night
```

## <a name="see-also"></a>另請參閱

[基本字串作業](basic-string-operations.md)




<!--HONumber=Nov16_HO1-->


