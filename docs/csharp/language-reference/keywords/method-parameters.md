---
title: "方法參數 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 924e261cc876d2428e28ed0f490beb46b95f96e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="method-parameters-c-reference"></a><span data-ttu-id="8dca5-102">方法參數 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8dca5-102">Method Parameters (C# Reference)</span></span>
<span data-ttu-id="8dca5-103">如果針對沒有 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 的方法宣告參數，參數可以有與其建立關聯的值。</span><span class="sxs-lookup"><span data-stu-id="8dca5-103">If a parameter is declared for a method without [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md), the parameter can have a value associated with it.</span></span> <span data-ttu-id="8dca5-104">該值可以在方法中進行變更，但控制權傳回給呼叫程序時，不會保留已變更值。</span><span class="sxs-lookup"><span data-stu-id="8dca5-104">That value can be changed in the method, but the changed value will not be retained when control passes back to the calling procedure.</span></span> <span data-ttu-id="8dca5-105">使用方法參數關鍵字，即可變更此行為。</span><span class="sxs-lookup"><span data-stu-id="8dca5-105">By using a method parameter keyword, you can change this behavior.</span></span>  
  
 <span data-ttu-id="8dca5-106">本節描述在您宣告方法參數時可以使用的關鍵字：</span><span class="sxs-lookup"><span data-stu-id="8dca5-106">This section describes the keywords you can use when declaring method parameters:</span></span>  
  
-   [<span data-ttu-id="8dca5-107">params</span><span class="sxs-lookup"><span data-stu-id="8dca5-107">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
  
-   [<span data-ttu-id="8dca5-108">ref</span><span class="sxs-lookup"><span data-stu-id="8dca5-108">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
  
-   [<span data-ttu-id="8dca5-109">out</span><span class="sxs-lookup"><span data-stu-id="8dca5-109">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
  
## <a name="see-also"></a><span data-ttu-id="8dca5-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dca5-110">See Also</span></span>  
 [<span data-ttu-id="8dca5-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="8dca5-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8dca5-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="8dca5-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8dca5-113">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="8dca5-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
