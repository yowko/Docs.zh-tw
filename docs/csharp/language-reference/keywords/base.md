---
title: "base (C# 參考)"
description: "了解 base 關鍵字，該關鍵字可用來存取 C# 衍生類別中基底類別的成員。"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 867f9eb286fa7ff5ef3e9167c1ab944c81161216
ms.openlocfilehash: b3a389d92373b6ba5995a7644b0440f9d8fad9ac
ms.contentlocale: zh-tw
ms.lasthandoff: 08/17/2017

---
# <a name="base-c-reference"></a><span data-ttu-id="de480-103">base (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="de480-103">base (C# Reference)</span></span>

<span data-ttu-id="de480-104">`base` 關鍵字是用來存取衍生類別中基底類別的成員︰</span><span class="sxs-lookup"><span data-stu-id="de480-104">The `base` keyword is used to access members of the base class from within a derived class:</span></span>

- <span data-ttu-id="de480-105">對已由另一個方法覆寫的基底類別來呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="de480-105">Call a method on the base class that has been overridden by another method.</span></span>

- <span data-ttu-id="de480-106">指定應該在建立衍生類別的執行個體時呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="de480-106">Specify which base-class constructor should be called when creating instances of the derived class.</span></span>

<span data-ttu-id="de480-107">僅允許在建構函式、執行個體方法或執行個體屬性存取子中進行基底類別存取。</span><span class="sxs-lookup"><span data-stu-id="de480-107">A base class access is permitted only in a constructor, an instance method, or an instance property accessor.</span></span>

<span data-ttu-id="de480-108">從靜態方法使用 `base` 關鍵字是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="de480-108">It is an error to use the `base` keyword from within a static method.</span></span>

<span data-ttu-id="de480-109">所存取的基底類別是類別宣告中所指定的基底類別。</span><span class="sxs-lookup"><span data-stu-id="de480-109">The base class that is accessed is the base class specified in the class declaration.</span></span> <span data-ttu-id="de480-110">例如，如果您指定 `class ClassB : ClassA`，則不論 ClassA 的基底類別為何，都會從 ClassB 存取 ClassA 成員。</span><span class="sxs-lookup"><span data-stu-id="de480-110">For example, if you specify `class ClassB : ClassA`, the members of ClassA are accessed from ClassB, regardless of the base class of ClassA.</span></span>

## <a name="example"></a><span data-ttu-id="de480-111">範例</span><span class="sxs-lookup"><span data-stu-id="de480-111">Example</span></span>
<span data-ttu-id="de480-112">在此範例中，基底類別 `Person` 和衍生類別 `Employee` 都會有名為 `Getinfo` 的方法。</span><span class="sxs-lookup"><span data-stu-id="de480-112">In this example, both the base class, `Person`, and the derived class, `Employee`, have a method named `Getinfo`.</span></span> <span data-ttu-id="de480-113">使用 `base` 關鍵字，即可從衍生類別對基底類別呼叫 `Getinfo` 方法。</span><span class="sxs-lookup"><span data-stu-id="de480-113">By using the `base` keyword, it is possible to call the `Getinfo` method on the base class, from within the derived class.</span></span>

<span data-ttu-id="de480-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="de480-114">[!code-cs[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]</span></span>

<span data-ttu-id="de480-115">如需其他範例，請參閱 [new](../../../csharp/language-reference/keywords/new.md)、[virtual](../../../csharp/language-reference/keywords/virtual.md) 和 [override](../../../csharp/language-reference/keywords/override.md)。</span><span class="sxs-lookup"><span data-stu-id="de480-115">For additional examples, see [new](../../../csharp/language-reference/keywords/new.md), [virtual](../../../csharp/language-reference/keywords/virtual.md), and [override](../../../csharp/language-reference/keywords/override.md).</span></span>

## <a name="example"></a><span data-ttu-id="de480-116">範例</span><span class="sxs-lookup"><span data-stu-id="de480-116">Example</span></span>
<span data-ttu-id="de480-117">這個範例示範如何指定在建立衍生類別的執行個體時呼叫的基底類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="de480-117">This example shows how to specify the base-class constructor called when creating instances of a derived class.</span></span>

<span data-ttu-id="de480-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="de480-118">[!code-cs[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="de480-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="de480-119">C# language specification</span></span>
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="de480-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="de480-120">See also</span></span>
 <span data-ttu-id="de480-121">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="de480-121">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="de480-122">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="de480-122">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="de480-123">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="de480-123">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="de480-124">this</span><span class="sxs-lookup"><span data-stu-id="de480-124">this</span></span>](../../../csharp/language-reference/keywords/this.md)
