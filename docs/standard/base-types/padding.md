---
title: "填補字串"
description: "填補字串"
keywords: ".NET、.NET Core"
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 1c8b3b44-d370-49e1-90b5-64ac81c02ae91c8b3b44-d370-49e1-90b5-64ac81c02ae9
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: bc3cc9028b232cc2ba6ca3130c4bdb261c4a0a42
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="padding-strings"></a><span data-ttu-id="8bdb0-104">填補字串</span><span class="sxs-lookup"><span data-stu-id="8bdb0-104">Padding strings</span></span>

<span data-ttu-id="8bdb0-105">使用下列 [System.String](xref:System.String) 方法之一建立由原始字串所組成的新字串，此原始字串填補的前置或後置字元是指定的總長度。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-105">Use one of the following [System.String](xref:System.String) methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="8bdb0-106">填補字元可以是空格或指定的字元，最後要靠右或靠左對齊。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-106">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>

<span data-ttu-id="8bdb0-107">方法名稱</span><span class="sxs-lookup"><span data-stu-id="8bdb0-107">Method name</span></span> | <span data-ttu-id="8bdb0-108">用法</span><span class="sxs-lookup"><span data-stu-id="8bdb0-108">Use</span></span>
----------- | ---
<span data-ttu-id="8bdb0-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8bdb0-109">[String.PadLeft](xref:System.String.PadLeft(System.Int32))</span></span> | <span data-ttu-id="8bdb0-110">以指定總長度的前置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-110">Pads a string with leading characters to a specified total length.</span></span>
<span data-ttu-id="8bdb0-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="8bdb0-111">[String.PadRight](xref:System.String.PadRight(System.Int32))</span></span> | <span data-ttu-id="8bdb0-112">以指定總長度的後置字元填補字串。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-112">Pads a string with trailing characters to a specified total length.</span></span>

## <a name="padleft"></a><span data-ttu-id="8bdb0-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="8bdb0-113">PadLeft</span></span>

<span data-ttu-id="8bdb0-114">[String.PadLeft](xref:System.String.PadLeft(System.Int32)) 方法是將足夠的前置填補字元串連到原始字串，達到指定的總長度，來建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-114">The [String.PadLeft](xref:System.String.PadLeft(System.Int32)) method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="8bdb0-115">[String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) 方法使用空白字元作為填補字元，而 [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) 方法則讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-115">The [String.PadLeft(Int32)](xref:System.String.PadLeft(System.Int32)) method uses white space as the padding character and the [String.PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="8bdb0-116">下列程式碼範例使用 [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) 方法建立長度為&20; 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-116">The following code example uses the [PadLeft(Int32, Char)](xref:System.String.PadLeft(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="8bdb0-117">此範例會在主控台顯示 "`--------Hello World!`"。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-117">The example displays "`--------Hello World!`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadLeft(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadLeft(20, "-"c))
```

## <a name="padright"></a><span data-ttu-id="8bdb0-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="8bdb0-118">PadRight</span></span>

<span data-ttu-id="8bdb0-119">[String.PadRight](xref:System.String.PadRight(System.Int32)) 方法是將足夠的後置填補字元串連到原始字串，達到指定的總長度，來建立新的字串。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-119">The [String.PadRight](xref:System.String.PadRight(System.Int32)) method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="8bdb0-120">[String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) 方法使用空白字元作為填補字元，而 [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) 方法則讓您指定自己的填補字元。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-120">The [String.PadRight(Int32)](xref:System.String.PadRight(System.Int32)) method uses white space as the padding character and the [String.PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method enables you to specify your own padding character.</span></span>

<span data-ttu-id="8bdb0-121">下列程式碼範例使用 [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) 方法建立長度為&20; 個字元的新字串。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-121">The following code example uses the [PadRight(Int32, Char)](xref:System.String.PadRight(System.Int32,System.Char)) method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="8bdb0-122">此範例會在主控台顯示 "`Hello World!--------`"。</span><span class="sxs-lookup"><span data-stu-id="8bdb0-122">The example displays "`Hello World!--------`" to the console.</span></span>

```csharp
string MyString = "Hello World!";
Console.WriteLine(MyString.PadRight(20, '-'));
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.PadRight(20, "-"c))
```

## <a name="see-also"></a><span data-ttu-id="8bdb0-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8bdb0-123">See Also</span></span>

[<span data-ttu-id="8bdb0-124">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="8bdb0-124">Basic string operations</span></span>](basic-string-operations.md)


