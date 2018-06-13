---
title: 方法參數 (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 8a8d300661eec42030900dd9ee85a17e66aa0922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269342"
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="bbf8a-102">方法參數 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bbf8a-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="bbf8a-103">為沒有 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 的方法宣告之參數，會以值的方式傳遞到呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="bbf8a-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="bbf8a-104">該值可以在方法中進行變更，但控制權傳回給呼叫程序時，不會保留已變更值。</span><span class="sxs-lookup"><span data-stu-id="bbf8a-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="bbf8a-105">使用方法參數關鍵字，即可變更此行為。</span><span class="sxs-lookup"><span data-stu-id="bbf8a-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="bbf8a-106">本節描述在您宣告方法參數時可以使用的關鍵字：</span><span class="sxs-lookup"><span data-stu-id="bbf8a-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   <span data-ttu-id="bbf8a-107">[params](../../../csharp/language-reference/keywords/params.md) 指定這個參數可以接受可變數目的引數。</span><span class="sxs-lookup"><span data-stu-id="bbf8a-107">[params](../../../csharp/language-reference/keywords/params.md) specifies that this parameter may take a variable number of arguments.</span></span>
  
-   <span data-ttu-id="bbf8a-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) 指定這個參數是傳址方式傳遞，但只會由所呼叫的方法讀取。</span><span class="sxs-lookup"><span data-stu-id="bbf8a-108">[in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) specifies that this parameter is passed by reference but is only read by the called method.</span></span>
  
-   <span data-ttu-id="bbf8a-109">[ref](../../../csharp/language-reference/keywords/ref.md) 指定這個參數是傳址方式傳遞，且可以由所呼叫的方法讀取或寫入。</span><span class="sxs-lookup"><span data-stu-id="bbf8a-109">[ref](../../../csharp/language-reference/keywords/ref.md) specifies that this parameter is passed by reference and may be read or written by the called method.</span></span>
  
-   <span data-ttu-id="bbf8a-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 指定這個參數是傳址方式傳遞，且由所呼叫的方法寫入。</span><span class="sxs-lookup"><span data-stu-id="bbf8a-110">[out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) specifies that this parameter is passed by reference and is written by the called method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bbf8a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf8a-111">See Also</span></span>  
 [<span data-ttu-id="bbf8a-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bbf8a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bbf8a-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bbf8a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bbf8a-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bbf8a-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
