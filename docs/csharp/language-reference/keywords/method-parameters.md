---
title: "方法參數 (C# 參考)"
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b20d2d233350cfb9de55cbd07e722082ec311597
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="8991b-102">方法參數 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8991b-102">Method Parameters (C# Reference)</span></span>

<span data-ttu-id="8991b-103">為沒有 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 的方法宣告之參數，會以值的方式傳遞到呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="8991b-103">Parameters declared for a method without [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md), are passed to the called method by value.</span></span> <span data-ttu-id="8991b-104">該值可以在方法中進行變更，但控制權傳回給呼叫程序時，不會保留已變更值。</span><span class="sxs-lookup"><span data-stu-id="8991b-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="8991b-105">使用方法參數關鍵字，即可變更此行為。</span><span class="sxs-lookup"><span data-stu-id="8991b-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="8991b-106">本節描述在您宣告方法參數時可以使用的關鍵字：</span><span class="sxs-lookup"><span data-stu-id="8991b-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="8991b-107">params</span><span class="sxs-lookup"><span data-stu-id="8991b-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="8991b-108">in</span><span class="sxs-lookup"><span data-stu-id="8991b-108">in</span></span>](../../../csharp/language-reference/keywords/in-parameter-modifier.md)  
  
-   [<span data-ttu-id="8991b-109">ref</span><span class="sxs-lookup"><span data-stu-id="8991b-109">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="8991b-110">out</span><span class="sxs-lookup"><span data-stu-id="8991b-110">out</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
  
## <a name="see-also"></a><span data-ttu-id="8991b-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="8991b-111">See Also</span></span>  
 [<span data-ttu-id="8991b-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8991b-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8991b-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8991b-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8991b-114">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8991b-114">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
