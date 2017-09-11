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
ms.translationtype: Human Translation
ms.sourcegitcommit: fb00da6505c9edb6a49d2003ae9bcb8e74c11d6c
ms.openlocfilehash: 96cf08c0de8ba73d931d561187369ccf8b091651
ms.contentlocale: zh-tw
ms.lasthandoff: 11/05/2016

---

# <a name="trimming-and-removing-characters-from-strings"></a><span data-ttu-id="3b958-104">修剪和移除字串中的字元</span><span class="sxs-lookup"><span data-stu-id="3b958-104">Trimming and removing characters from strings</span></span>

<span data-ttu-id="3b958-105">如果您將句子剖析成個別文字，最後可能會得到許多文字，但文字任一端有空格 (也稱為空白字元)。</span><span class="sxs-lookup"><span data-stu-id="3b958-105">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="3b958-106">在這種情況下，您可以使用 [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) 類別中的其中一個 Trim 方法，從字串中的指定位置移除任意數目的空格或其他字元。</span><span class="sxs-lookup"><span data-stu-id="3b958-106">In this situation, you can use one of the trim methods in the [System.String](https://docs.microsoft.com/dotnet/core/api/System.String) class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="3b958-107">下表描述可用的 Trim 方法。</span><span class="sxs-lookup"><span data-stu-id="3b958-107">The following table describes the available trim methods.</span></span>

<span data-ttu-id="3b958-108">方法名稱</span><span class="sxs-lookup"><span data-stu-id="3b958-108">Method name</span></span> | <span data-ttu-id="3b958-109">用法</span><span class="sxs-lookup"><span data-stu-id="3b958-109">Use</span></span>
----------- | ---
[<span data-ttu-id="3b958-110">String.Trim</span><span class="sxs-lookup"><span data-stu-id="3b958-110">String.Trim</span></span>](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) | <span data-ttu-id="3b958-111">將字元陣列中字串開頭和結尾指定的空格或空白字元移除。</span><span class="sxs-lookup"><span data-stu-id="3b958-111">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>
<span data-ttu-id="3b958-112">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[]))</span><span class="sxs-lookup"><span data-stu-id="3b958-112">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[]))</span></span> | <span data-ttu-id="3b958-113">從字串尾端移除字元陣列中指定的字元。</span><span class="sxs-lookup"><span data-stu-id="3b958-113">Removes characters specified in an array of characters from the end of a string.</span></span>
<span data-ttu-id="3b958-114">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[]))</span><span class="sxs-lookup"><span data-stu-id="3b958-114">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[]))</span></span> | <span data-ttu-id="3b958-115">從字串開頭移除字元陣列中指定的字元。</span><span class="sxs-lookup"><span data-stu-id="3b958-115">Removes characters specified in an array of characters from the beginning of a string.</span></span>
<span data-ttu-id="3b958-116">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="3b958-116">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32))</span></span> | <span data-ttu-id="3b958-117">從字串中指定的索引位置移除指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="3b958-117">Removes a specified number of characters from a specified index position in a string.</span></span>


## <a name="trim"></a><span data-ttu-id="3b958-118">Trim</span><span class="sxs-lookup"><span data-stu-id="3b958-118">Trim</span></span>

<span data-ttu-id="3b958-119">您可以使用 [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) 方法，輕鬆地移除字串頭尾的空格，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="3b958-119">You can easily remove white spaces from both ends of a string by using the [String.Trim](https://docs.microsoft.com/dotnet/core/api/System.String.Trim) method, as shown in the following example.</span></span>

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

<span data-ttu-id="3b958-120">您也可以將字元陣列中字串開頭和結尾指定的字元移除。</span><span class="sxs-lookup"><span data-stu-id="3b958-120">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="3b958-121">下列範例將會移除空白字元、句號和星號。</span><span class="sxs-lookup"><span data-stu-id="3b958-121">The following example removes white-space characters, periods, and asterisks.</span></span>

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

## <a name="trimend"></a><span data-ttu-id="3b958-122">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="3b958-122">TrimEnd</span></span>

<span data-ttu-id="3b958-123">[String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 方法會從字串結尾移除字元，並建立新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="3b958-123">The [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="3b958-124">系統會將字元陣列傳遞給這個方法，以指定要移除的字元。</span><span class="sxs-lookup"><span data-stu-id="3b958-124">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="3b958-125">字元陣列中的項目順序不會影響修剪作業。</span><span class="sxs-lookup"><span data-stu-id="3b958-125">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="3b958-126">一旦找到陣列中未指定的字元時，修剪作業就會停止。</span><span class="sxs-lookup"><span data-stu-id="3b958-126">The trim stops when a character not specified in the array is found.</span></span>

<span data-ttu-id="3b958-127">下列範例會使用 TrimEnd 方法，移除字串的最後一個字母。</span><span class="sxs-lookup"><span data-stu-id="3b958-127">The following example removes the last letters of a string using the TrimEnd method.</span></span> <span data-ttu-id="3b958-128">在此範例中，`'r'` 字元和 `'W'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="3b958-128">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="3b958-129">請注意，此程式碼會移除 `MyString` 的最後一個字以及第一個字的一部分。</span><span class="sxs-lookup"><span data-stu-id="3b958-129">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>

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

<span data-ttu-id="3b958-130">此程式碼會讓主控台顯示 `He`。</span><span class="sxs-lookup"><span data-stu-id="3b958-130">This code displays `He` to the console.</span></span>

<span data-ttu-id="3b958-131">下列範例會使用 [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 方法，移除字串的最後一個文字。</span><span class="sxs-lookup"><span data-stu-id="3b958-131">The following example removes the last word of a string using the [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method.</span></span> <span data-ttu-id="3b958-132">在這個程式碼中，`Hello` 文字後接一個逗號，不過由於要修剪的字元陣列中未指定逗號，因此修剪作業會在逗號處停止。</span><span class="sxs-lookup"><span data-stu-id="3b958-132">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>

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

<span data-ttu-id="3b958-133">此程式碼會讓主控台顯示 `Hello,`。</span><span class="sxs-lookup"><span data-stu-id="3b958-133">This code displays `Hello,` to the console.</span></span>

## <a name="trimstart"></a><span data-ttu-id="3b958-134">TrimStart</span><span class="sxs-lookup"><span data-stu-id="3b958-134">TrimStart</span></span>

<span data-ttu-id="3b958-135">[String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) 方法與 [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 方法類似，只是它會移除現有字串物件開頭的字元以建立新字串。</span><span class="sxs-lookup"><span data-stu-id="3b958-135">The [String.TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) method is similar to the [String.TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="3b958-136">系統會將字元陣列傳遞給 [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) 方法，以指定要移除的字元。</span><span class="sxs-lookup"><span data-stu-id="3b958-136">An array of characters is passed to the [TrimStart](https://docs.microsoft.com/dotnet/core/api/System.String.TrimStart(System.Char[])) method to specify the characters to be removed.</span></span> <span data-ttu-id="3b958-137">使用 [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) 時，字元陣列中的項目順序不會影響修剪作業。</span><span class="sxs-lookup"><span data-stu-id="3b958-137">As with the [TrimEnd](https://docs.microsoft.com/dotnet/core/api/System.String.TrimEnd(System.Char[])) method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="3b958-138">一旦找到陣列中未指定的字元時，修剪作業就會停止。</span><span class="sxs-lookup"><span data-stu-id="3b958-138">The trim stops when a character not specified in the array is found.</span></span>

<span data-ttu-id="3b958-139">下列範例會移除字串的第一個文字。</span><span class="sxs-lookup"><span data-stu-id="3b958-139">The following example removes the first word of a string.</span></span> <span data-ttu-id="3b958-140">在此範例中，`'l'` 字元和 `'H'` 字元的位置顛倒，用以說明字元陣列中的順序並不重要。</span><span class="sxs-lookup"><span data-stu-id="3b958-140">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>

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

<span data-ttu-id="3b958-141">此程式碼會讓主控台顯示 `World!`。</span><span class="sxs-lookup"><span data-stu-id="3b958-141">This code displays `World!` to the console.</span></span>

## <a name="remove"></a><span data-ttu-id="3b958-142">移除</span><span class="sxs-lookup"><span data-stu-id="3b958-142">Remove</span></span>

<span data-ttu-id="3b958-143">[String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) 方法會從現有字串中的指定位置開始，移除指定的字元數。</span><span class="sxs-lookup"><span data-stu-id="3b958-143">The [String.Remove](https://docs.microsoft.com/dotnet/core/api/System.String.Remove(System.Int32)) method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="3b958-144">這個方法會假設以零為起始的索引。</span><span class="sxs-lookup"><span data-stu-id="3b958-144">This method assumes a zero-based index.</span></span>

<span data-ttu-id="3b958-145">下列範例會於字串中以零為起始之索引的位置五開始，從字串中移除 10 個字元。</span><span class="sxs-lookup"><span data-stu-id="3b958-145">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>

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

<span data-ttu-id="3b958-146">您也可以從字串中移除指定的字元或子字串，方法是呼叫 [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) 方法並指定空字串 ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) 做為取代。</span><span class="sxs-lookup"><span data-stu-id="3b958-146">You can also remove a specified character or substring from a string by calling the [String.Replace(String, String)](https://docs.microsoft.com/dotnet/core/api/System.String.Replace(System.String,System.String)) method and specifying an empty string ([String.Empty](https://docs.microsoft.com/dotnet/core/api/System.String.Empty)) as the replacement.</span></span> <span data-ttu-id="3b958-147">下列範例將會從字串中移除所有逗號。</span><span class="sxs-lookup"><span data-stu-id="3b958-147">The following example removes all commas from a string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3b958-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b958-148">See Also</span></span>

[<span data-ttu-id="3b958-149">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="3b958-149">Basic string operations</span></span>](basic-string-operations.md)


