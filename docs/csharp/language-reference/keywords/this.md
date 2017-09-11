---
title: "this (C# 參考)"
description: "this 關鍵字 (C# 參考)"
keywords: "this (C#), this 關鍵字 (C#), this 關鍵字 (C# 參考), this 關鍵字 (C# 語言參考)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1e764bbd85d06a3b1898f6574064b2844f6d6813
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="this-c-reference"></a><span data-ttu-id="16f12-104">this (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="16f12-104">this (C# Reference)</span></span>
<span data-ttu-id="16f12-105">`this` 關鍵字指的是類別的目前執行個體，也用作擴充方法第一個參數的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="16f12-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16f12-106">本文討論如何搭配使用 `this` 與類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="16f12-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="16f12-107">如需其在擴充方法中之用法的詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="16f12-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="16f12-108">下列是 `this` 的常見用法：</span><span class="sxs-lookup"><span data-stu-id="16f12-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="16f12-109">限定透過類似名稱所隱藏的成員，例如︰</span><span class="sxs-lookup"><span data-stu-id="16f12-109">To qualify members hidden by similar names, for example:</span></span>  
  
 <span data-ttu-id="16f12-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="16f12-110">[!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]</span></span>  
  
-   <span data-ttu-id="16f12-111">傳遞物件作為其他方法的參數，例如：</span><span class="sxs-lookup"><span data-stu-id="16f12-111">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="16f12-112">宣告索引子，例如︰</span><span class="sxs-lookup"><span data-stu-id="16f12-112">To declare indexers, for example:</span></span>  
  
 <span data-ttu-id="16f12-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="16f12-113">[!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]</span></span>  
  
 <span data-ttu-id="16f12-114">靜態成員函式存在於類別層級，而不是物件的一部分，因此沒有 `this` 指標。</span><span class="sxs-lookup"><span data-stu-id="16f12-114">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="16f12-115">在靜態方法中參照 `this` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="16f12-115">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16f12-116">範例</span><span class="sxs-lookup"><span data-stu-id="16f12-116">Example</span></span>  
 <span data-ttu-id="16f12-117">在此範例中，`this` 是用來限定 `Employee` 類別成員 `name` 和 `alias`，而這些是透過類似的名稱進行隱藏。</span><span class="sxs-lookup"><span data-stu-id="16f12-117">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="16f12-118">它也會用來將物件傳遞給屬於另一個類別的 `CalcTax` 方法。</span><span class="sxs-lookup"><span data-stu-id="16f12-118">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 <span data-ttu-id="16f12-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="16f12-119">[!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="16f12-120">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="16f12-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="16f12-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16f12-121">See Also</span></span>  
 <span data-ttu-id="16f12-122">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="16f12-122">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="16f12-123">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="16f12-123">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="16f12-124">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="16f12-124">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="16f12-125">[base](../../../csharp/language-reference/keywords/base.md) </span><span class="sxs-lookup"><span data-stu-id="16f12-125">[base](../../../csharp/language-reference/keywords/base.md) </span></span>  
 [<span data-ttu-id="16f12-126">方法</span><span class="sxs-lookup"><span data-stu-id="16f12-126">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)

