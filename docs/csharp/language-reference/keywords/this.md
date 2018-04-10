---
title: this (C# 參考)
description: this 關鍵字 (C# 參考)
keywords: this (C#), this 關鍵字 (C#), this 關鍵字 (C# 參考), this 關鍵字 (C# 語言參考)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a><span data-ttu-id="61a2c-104">this (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="61a2c-104">this (C# Reference)</span></span>
<span data-ttu-id="61a2c-105">`this` 關鍵字指的是類別的目前執行個體，也用作擴充方法第一個參數的修飾詞。</span><span class="sxs-lookup"><span data-stu-id="61a2c-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61a2c-106">本文討論如何搭配使用 `this` 與類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="61a2c-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="61a2c-107">如需其在擴充方法中之用法的詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="61a2c-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="61a2c-108">下列是 `this` 的常見用法：</span><span class="sxs-lookup"><span data-stu-id="61a2c-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="61a2c-109">限定透過類似名稱所隱藏的成員，例如︰</span><span class="sxs-lookup"><span data-stu-id="61a2c-109">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="61a2c-110">傳遞物件作為其他方法的參數，例如：</span><span class="sxs-lookup"><span data-stu-id="61a2c-110">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="61a2c-111">宣告索引子，例如︰</span><span class="sxs-lookup"><span data-stu-id="61a2c-111">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="61a2c-112">靜態成員函式存在於類別層級，而不是物件的一部分，因此沒有 `this` 指標。</span><span class="sxs-lookup"><span data-stu-id="61a2c-112">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="61a2c-113">在靜態方法中參照 `this` 會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="61a2c-113">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61a2c-114">範例</span><span class="sxs-lookup"><span data-stu-id="61a2c-114">Example</span></span>  
 <span data-ttu-id="61a2c-115">在此範例中，`this` 是用來限定 `Employee` 類別成員 `name` 和 `alias`，而這些是透過類似的名稱進行隱藏。</span><span class="sxs-lookup"><span data-stu-id="61a2c-115">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="61a2c-116">它也會用來將物件傳遞給屬於另一個類別的 `CalcTax` 方法。</span><span class="sxs-lookup"><span data-stu-id="61a2c-116">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="61a2c-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="61a2c-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="61a2c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61a2c-118">See Also</span></span>  
 [<span data-ttu-id="61a2c-119">C# 參考</span><span class="sxs-lookup"><span data-stu-id="61a2c-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="61a2c-120">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="61a2c-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="61a2c-121">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="61a2c-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="61a2c-122">base</span><span class="sxs-lookup"><span data-stu-id="61a2c-122">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="61a2c-123">方法</span><span class="sxs-lookup"><span data-stu-id="61a2c-123">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
