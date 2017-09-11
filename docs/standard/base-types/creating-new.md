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
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 793b5bc4b26967104459fa2559c6127bb82f3a9d
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="creating-new-strings"></a><span data-ttu-id="f6c3d-104">建立新字串</span><span class="sxs-lookup"><span data-stu-id="f6c3d-104">Creating new strings</span></span>

<span data-ttu-id="f6c3d-105">.NET 允許使用簡單的指派來建立字串，並且還可以多載類別建構函式，以支援使用多個不同參數來建立字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-105">.NET  allows strings to be created using simple assignment, and also overloads a class constructor to support string creation using a number of different parameters.</span></span> <span data-ttu-id="f6c3d-106">.NET 也在 [System.String](xref:System.String) 類別中提供幾個方法，藉由組合多個字串、字串陣列或物件的方式來建立新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-106">.NET also provides several methods in the [System.String](xref:System.String) class that create new string objects by combining several strings, arrays of strings, or objects.</span></span> 

## <a name="creating-strings-using-assignment"></a><span data-ttu-id="f6c3d-107">使用指派建立字串</span><span class="sxs-lookup"><span data-stu-id="f6c3d-107">Creating Strings Using Assignment</span></span>

<span data-ttu-id="f6c3d-108">建立新的 [String](xref:System.String) 物件的最簡單方式，是將字串常值直接指派給 [String](xref:System.String) 物件。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-108">The easiest way to create a new [String](xref:System.String) object is simply to assign a string literal to a [String](xref:System.String) object.</span></span> 

## <a name="creating-strings-using-a-class-constructor"></a><span data-ttu-id="f6c3d-109">使用類別建構函式建立字串</span><span class="sxs-lookup"><span data-stu-id="f6c3d-109">Creating Strings Using a Class Constructor</span></span>

<span data-ttu-id="f6c3d-110">您可以使用 [String](xref:System.String) 類別建構函式的多載，從字元陣列建立字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-110">You can use overloads of the [String](xref:System.String) class constructor to create strings from character arrays.</span></span> <span data-ttu-id="f6c3d-111">您也可以讓某個特定字元重複指定的次數，藉此建立新字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-111">You can also create a new string by duplicating a particular character a specified number of times.</span></span> 

## <a name="methods-that-return-strings"></a><span data-ttu-id="f6c3d-112">傳回字串的方法</span><span class="sxs-lookup"><span data-stu-id="f6c3d-112">Methods that Return Strings</span></span>

<span data-ttu-id="f6c3d-113">下表列出數個可傳回新字串物件的有用方法。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-113">The following table lists several useful methods that return new string objects.</span></span>

<span data-ttu-id="f6c3d-114">方法名稱</span><span class="sxs-lookup"><span data-stu-id="f6c3d-114">Method name</span></span> | <span data-ttu-id="f6c3d-115">用法</span><span class="sxs-lookup"><span data-stu-id="f6c3d-115">Use</span></span>
----------- | ---
<span data-ttu-id="f6c3d-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span><span class="sxs-lookup"><span data-stu-id="f6c3d-116">[String.Format](xref:System.String.Format(System.String,System.Object))</span></span> | <span data-ttu-id="f6c3d-117">從一組輸入物件建立格式化的字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-117">Builds a formatted string from a set of input objects.</span></span>
<span data-ttu-id="f6c3d-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span><span class="sxs-lookup"><span data-stu-id="f6c3d-118">[String.Concat](xref:System.String.Concat(System.String,System.String))</span></span> | <span data-ttu-id="f6c3d-119">從兩個或多個字串建立字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-119">Builds strings from two or more strings.</span></span>
<span data-ttu-id="f6c3d-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span><span class="sxs-lookup"><span data-stu-id="f6c3d-120">[String.Join](xref:System.String.Join(System.String,System.String[]))</span></span> |<span data-ttu-id="f6c3d-121">藉由組合字串陣列來建立新字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-121">Builds a new string by combining an array of strings.</span></span>
<span data-ttu-id="f6c3d-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span><span class="sxs-lookup"><span data-stu-id="f6c3d-122">[String.Insert](xref:System.String.Insert(System.Int32,System.String))</span></span> | <span data-ttu-id="f6c3d-123">藉由將字串插入現有字串的指定索引中來建立新字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-123">Builds a new string by inserting a string into the specified index of an existing string.</span></span>
<span data-ttu-id="f6c3d-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span><span class="sxs-lookup"><span data-stu-id="f6c3d-124">[String.CopyTo](xref:System.String.CopyTo(System.Int32,System.Char[],System.Int32,System.Int32))</span></span> | <span data-ttu-id="f6c3d-125">將字串中的指定字元複製到字元陣列中的指定位置。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-125">Copies specified characters in a string into a specified position in an array of characters.</span></span>

### <a name="format"></a><span data-ttu-id="f6c3d-126">格式</span><span class="sxs-lookup"><span data-stu-id="f6c3d-126">Format</span></span>

<span data-ttu-id="f6c3d-127">您可以使用 `String.Format` 方法，建立格式化的字串和串連代表多個物件的字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-127">You can use the `String.Format` method to create formatted strings and concatenate strings representing multiple objects.</span></span> <span data-ttu-id="f6c3d-128">這個方法會自動將任何傳遞的物件轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-128">This method automatically converts any passed object into a string.</span></span> <span data-ttu-id="f6c3d-129">例如，如果您的應用程式必須向使用者顯示 [Int32](xref:System.Int32) 值和 [DateTime](xref:System.DateTime) 值，您可以使用 `Format` 方法，輕鬆地建構出代表這些值的字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-129">For example, if your application must display an [Int32](xref:System.Int32) value and a [DateTime](xref:System.DateTime) value to the user, you can easily construct a string to represent these values using the `Format` method.</span></span> <span data-ttu-id="f6c3d-130">如需搭配此方法使用之格式慣例的資訊，請參閱[複合格式](composite-format.md)一節。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-130">For information about formatting conventions used with this method, see the section on [composite formatting](composite-format.md).</span></span>

<span data-ttu-id="f6c3d-131">下列範例會使用 `Format` 方法來建立使用整數變數的字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-131">The following example uses the `Format` method to create a string that uses an integer variable.</span></span>

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

<span data-ttu-id="f6c3d-132">在此範例中，[DateTime.Now](xref:System.DateTime.Now) 會以和目前執行緒關聯的文化特性中所指定的方式來顯示目前日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-132">In this example, [DateTime.Now](xref:System.DateTime.Now) displays the current date and time in a manner specified by the culture associated with the current thread.</span></span>

### <a name="concat"></a><span data-ttu-id="f6c3d-133">Concat</span><span class="sxs-lookup"><span data-stu-id="f6c3d-133">Concat</span></span>

<span data-ttu-id="f6c3d-134">使用 `String.Concat` 方法可以輕鬆地從兩個或多個現有物件，建立新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-134">The `String.Concat` method can be used to easily create a new string object from two or more existing objects.</span></span> <span data-ttu-id="f6c3d-135">它提供與語言無關的方式來串連字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-135">It provides a language-independent way to concatenate strings.</span></span> <span data-ttu-id="f6c3d-136">這個方法接受衍生自 `System.Object` 的任何類別。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-136">This method accepts any class that derives from `System.Object`.</span></span> <span data-ttu-id="f6c3d-137">下列範例會從現有的兩個字串物件和一個分隔字元建立字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-137">The following example creates a string from two existing string objects and a separating character.</span></span>

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

### <a name="join"></a><span data-ttu-id="f6c3d-138">Join</span><span class="sxs-lookup"><span data-stu-id="f6c3d-138">Join</span></span>

<span data-ttu-id="f6c3d-139">`String.Join` 方法會從字串陣列和分隔符號字串建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-139">The `String.Join` method creates a new string from an array of strings and a separator string.</span></span> <span data-ttu-id="f6c3d-140">如果您想要將多個字串串連在一起，建立以逗號分隔的清單，這個方法會很有用。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-140">This method is useful if you want to concatenate multiple strings together, making a list perhaps separated by a comma.</span></span>

<span data-ttu-id="f6c3d-141">下列範例會使用空格來繫結字串陣列。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-141">The following example uses a space to bind a string array.</span></span>

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

### <a name="insert"></a><span data-ttu-id="f6c3d-142">Insert</span><span class="sxs-lookup"><span data-stu-id="f6c3d-142">Insert</span></span>

<span data-ttu-id="f6c3d-143">`String.Insert` 方法會將字串插入另一個字串中的指定位置，藉此建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-143">The `String.Insert` method creates a new string by inserting a string into a specified position in another string.</span></span> <span data-ttu-id="f6c3d-144">這個方法會使用以零起始的索引。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-144">This method uses a zero-based index.</span></span> <span data-ttu-id="f6c3d-145">下列範例會將字串插入 `MyString` 的第五個索引位置，並使用這個值來建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-145">The following example inserts a string into the fifth index position of `MyString` and creates a new string with this value.</span></span>

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

### <a name="copyto"></a><span data-ttu-id="f6c3d-146">CopyTo</span><span class="sxs-lookup"><span data-stu-id="f6c3d-146">CopyTo</span></span>

<span data-ttu-id="f6c3d-147">`String.CopyTo` 方法會將部分字串複製到字元陣列中。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-147">The `String.CopyTo` method copies portions of a string into an array of characters.</span></span> <span data-ttu-id="f6c3d-148">您可以同時指定字串的開頭索引和要複製的字元數。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-148">You can specify both the beginning index of the string and the number of characters to be copied.</span></span> <span data-ttu-id="f6c3d-149">這個方法會使用來源索引、字元陣列、目的索引和要複製的字元數。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-149">This method takes the source index, an array of characters, the destination index, and the number of characters to copy.</span></span> <span data-ttu-id="f6c3d-150">所有索引都是以零起始。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-150">All indexes are zero-based.</span></span>

<span data-ttu-id="f6c3d-151">下列範例會使用 `CopyTo` 方法，將 "Hello" 這個字的所有字元從字串物件複製到字元陣列的第一個索引位置。</span><span class="sxs-lookup"><span data-stu-id="f6c3d-151">The following example uses the `CopyTo` method to copy the characters of the word "Hello" from a string object to the first index position of an array of characters.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f6c3d-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6c3d-152">See Also</span></span>

[<span data-ttu-id="f6c3d-153">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="f6c3d-153">Basic string operations</span></span>](basic-string-operations.md)

[<span data-ttu-id="f6c3d-154">複合格式</span><span class="sxs-lookup"><span data-stu-id="f6c3d-154">Composite formatting</span></span>](composite-format.md)


