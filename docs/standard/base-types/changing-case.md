---
title: "變更大小寫"
description: "變更大小寫"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
ms.date: 07/26/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 646c5afd-8aec-4393-9c00-f68ad2580c68
ms.translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 023f40969095627242d3652add853eb999c30c4b
ms.contentlocale: zh-tw
ms.lasthandoff: 03/02/2017

---

# <a name="changing-case"></a><span data-ttu-id="15147-104">變更大小寫</span><span class="sxs-lookup"><span data-stu-id="15147-104">Changing case</span></span>

<span data-ttu-id="15147-105">如果您要撰寫接受使用者輸入的應用程式，則無法確定使用者輸入資料時會使用大寫或小寫。</span><span class="sxs-lookup"><span data-stu-id="15147-105">If you write an application that accepts input from a user, you can never be sure what case he or she will use to enter the data.</span></span> <span data-ttu-id="15147-106">通常，您會希望字串的大小寫一致，特別是要在使用者介面中顯示這些字串時。</span><span class="sxs-lookup"><span data-stu-id="15147-106">Often, you want strings to be cased consistently, particularly if you are displaying them in the user interface.</span></span> <span data-ttu-id="15147-107">下表描述兩種變更大小寫的方法。</span><span class="sxs-lookup"><span data-stu-id="15147-107">The following table describes two case-changing methods.</span></span>

<span data-ttu-id="15147-108">方法名稱</span><span class="sxs-lookup"><span data-stu-id="15147-108">Method name</span></span> | <span data-ttu-id="15147-109">用法</span><span class="sxs-lookup"><span data-stu-id="15147-109">Use</span></span>
----------- | ---
[<span data-ttu-id="15147-110">String.ToUpper</span><span class="sxs-lookup"><span data-stu-id="15147-110">String.ToUpper</span></span>](xref:System.String.ToUpper) | <span data-ttu-id="15147-111">將字串中的所有字元轉換成大寫。</span><span class="sxs-lookup"><span data-stu-id="15147-111">Converts all characters in a string to uppercase.</span></span>
[<span data-ttu-id="15147-112">String.ToLower</span><span class="sxs-lookup"><span data-stu-id="15147-112">String.ToLower</span></span>](xref:System.String.ToLower) | <span data-ttu-id="15147-113">將字串中的所有字元轉換成小寫。</span><span class="sxs-lookup"><span data-stu-id="15147-113">Converts all characters in a string to lowercase.</span></span>

> [!WARNING]  
> <span data-ttu-id="15147-114">請注意，您不應該使用 `String.ToUpper` 和 `String.ToLower` 方法來轉換字串，以便對字串進行比較或測試字串是否相等。</span><span class="sxs-lookup"><span data-stu-id="15147-114">Note that the `String.ToUpper` and `String.ToLower` methods should not be used to convert strings in order to compare them or test them for equality.</span></span> 

## <a name="comparing-strings-of-mixed-case"></a><span data-ttu-id="15147-115">比較混合大小寫的字串</span><span class="sxs-lookup"><span data-stu-id="15147-115">Comparing strings of mixed case</span></span>

<span data-ttu-id="15147-116">若要比較混合大小寫的字串以決定字串是否相等，請使用 *comparisonType* 參數呼叫 [String](xref:System) `Equals` 方法的其中一個多載，並為 *comparisonType* 引數提供 [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) 或 [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) 的值。</span><span class="sxs-lookup"><span data-stu-id="15147-116">To compare strings of mixed case to determine whether they are equal, their, call one of the overloads of the [String](xref:System) `Equals` method with a *comparisonType* parameter, and provide a value of either [StringComparison.CurrentCultureIgnoreCase](xref:System.StringComparison.CurrentCultureIgnoreCase) or [StringComparison.OrdinalIgnoreCase](xref:System.StringComparison.OrdinalIgnoreCase) for the *comparisonType* argument.</span></span> 

<span data-ttu-id="15147-117">如需詳細資訊，請參閱[使用字串的最佳做法](best-practices.md)。</span><span class="sxs-lookup"><span data-stu-id="15147-117">For more information, see [Best Practices for Using Strings](best-practices.md).</span></span> 

## <a name="toupper"></a><span data-ttu-id="15147-118">ToUpper</span><span class="sxs-lookup"><span data-stu-id="15147-118">ToUpper</span></span>

<span data-ttu-id="15147-119">[String.ToUpper](xref:System.String.ToUpper) 方法會將字串中的所有字元變更為大寫。</span><span class="sxs-lookup"><span data-stu-id="15147-119">The [String.ToUpper](xref:System.String.ToUpper) method changes all characters in a string to uppercase.</span></span> <span data-ttu-id="15147-120">下列範例會將字串 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="15147-120">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="15147-121">從混合大小寫轉換成大寫。</span><span class="sxs-lookup"><span data-stu-id="15147-121">from mixed case to uppercase.</span></span>

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToUpper());
// This example displays the following output:
//       HELLO WORLD!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToUpper())
' This example displays the following output:
'       HELLO WORLD!
```

## <a name="tolower"></a><span data-ttu-id="15147-122">ToLower</span><span class="sxs-lookup"><span data-stu-id="15147-122">ToLower</span></span>

<span data-ttu-id="15147-123">[String.ToLower](xref:System.String.ToLower) 方法類似於前一個方法，但會改將字串中的所有字元轉換成小寫。</span><span class="sxs-lookup"><span data-stu-id="15147-123">The [String.ToLower](xref:System.String.ToLower) method is similar to the previous method, but instead converts all the characters in a string to lowercase.</span></span> <span data-ttu-id="15147-124">下列範例會將字串 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="15147-124">The following example converts the string "Hello World!"</span></span> <span data-ttu-id="15147-125">轉換成小寫。</span><span class="sxs-lookup"><span data-stu-id="15147-125">to lowercase.</span></span>

```csharp
string properString = "Hello World!";
Console.WriteLine(properString.ToLower());
// This example displays the following output:
//       hello world!
```

```vb
Dim MyString As String = "Hello World!"
Console.WriteLine(MyString.ToLower())
' This example displays the following output:
'       hello world!
```

## <a name="see-also"></a><span data-ttu-id="15147-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15147-126">See Also</span></span>

[<span data-ttu-id="15147-127">基本字串作業</span><span class="sxs-lookup"><span data-stu-id="15147-127">Basic string operations</span></span>](basic-string-operations.md)

