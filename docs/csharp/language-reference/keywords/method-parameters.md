---
title: 方法參數 (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: 8
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 35d96066deb866e02f6bf624121376fe3ae94373
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="8d65f-102">方法參數 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8d65f-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="8d65f-103">為沒有 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 的方法宣告之參數，會以值的方式傳遞到呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="8d65f-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="8d65f-104">該值可以在方法中進行變更，但控制權傳回給呼叫程序時，不會保留已變更值。</span><span class="sxs-lookup"><span data-stu-id="8d65f-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="8d65f-105">使用方法參數關鍵字，即可變更此行為。</span><span class="sxs-lookup"><span data-stu-id="8d65f-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="8d65f-106">本節描述在您宣告方法參數時可以使用的關鍵字：</span><span class="sxs-lookup"><span data-stu-id="8d65f-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="8d65f-107">[params](../../../csharp/language-reference/keywords/params.md) 指定這個參數可以接受可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="8d65f-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="8d65f-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) 指定這個參數是傳址方式傳遞，但只會由所呼叫的方法讀取。</span><span class="sxs-lookup"><span data-stu-id="8d65f-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="8d65f-109">[ref](../../../csharp/language-reference/keywords/ref.md) 指定這個參數是傳址方式傳遞，且可以由所呼叫的方法讀取或寫入。</span><span class="sxs-lookup"><span data-stu-id="8d65f-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="8d65f-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 指定這個參數是傳址方式傳遞，且由所呼叫的方法寫入。</span><span class="sxs-lookup"><span data-stu-id="8d65f-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8d65f-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d65f-111">See Also</span></span>  
 [<span data-ttu-id="8d65f-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8d65f-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8d65f-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8d65f-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8d65f-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8d65f-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
