---
title: ".NET Framework 中的平行處理和並行機制"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, parallel processing
- parallel processing [.NET Framework]
- concurrency [.NET Framework]
- .NET Framework, concurrency
ms.assetid: e573faa8-0212-44b1-a850-ce85dc54f47f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ab15fd38a467eec398f8383e40067d2135c042b5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="parallel-processing-and-concurrency-in-the-net-framework"></a><span data-ttu-id="f94a3-102">.NET Framework 中的平行處理和並行機制</span><span class="sxs-lookup"><span data-stu-id="f94a3-102">Parallel Processing and Concurrency in the .NET Framework</span></span>
<span data-ttu-id="f94a3-103">.NET Framework 提供數種方式，讓您可以使用多執行緒的執行，以保持應用程式回應您的使用者，同時讓使用者電腦的效能極大化。</span><span class="sxs-lookup"><span data-stu-id="f94a3-103">The .NET Framework provides several ways for you to use multiple threads of execution to keep your application responsive to your user while maximizing the performance of your user's computer.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f94a3-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="f94a3-104">In This Section</span></span>  
 [<span data-ttu-id="f94a3-105">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="f94a3-105">Threading</span></span>](../../docs/standard/threading/index.md)  
 <span data-ttu-id="f94a3-106">描述 .NET Framework 所提供的基本並行和同步處理機制。</span><span class="sxs-lookup"><span data-stu-id="f94a3-106">Describes the basic concurrency and synchronization mechanisms provided by the .NET Framework.</span></span>  
  
 [<span data-ttu-id="f94a3-107">非同步程式設計模式</span><span class="sxs-lookup"><span data-stu-id="f94a3-107">Asynchronous Programming Patterns</span></span>](../../docs/standard/asynchronous-programming-patterns/index.md)  
 <span data-ttu-id="f94a3-108">提供 .NET Framework 所支援之三個非同步程式設計模式的簡短概觀：</span><span class="sxs-lookup"><span data-stu-id="f94a3-108">Provides a brief overview of the three asynchronous programming patterns supported in the .NET Framework:</span></span>  
  
-   <span data-ttu-id="f94a3-109">[非同步程式設計模型 (APM)](../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (舊版)</span><span class="sxs-lookup"><span data-stu-id="f94a3-109">[Asynchronous Programming Model (APM)](../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) (legacy)</span></span>  
  
-   <span data-ttu-id="f94a3-110">[事件架構非同步模式 (EAP)](../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (舊版)</span><span class="sxs-lookup"><span data-stu-id="f94a3-110">[Event-based Asynchronous Pattern (EAP)](../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) (legacy)</span></span>  
  
-   <span data-ttu-id="f94a3-111">[工作架構非同步模式 (TAP)](../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (新的開發建議)</span><span class="sxs-lookup"><span data-stu-id="f94a3-111">[Task-based Asynchronous Pattern (TAP)](../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) (recommended for new development)</span></span>  
  
 [<span data-ttu-id="f94a3-112">平行程式設計</span><span class="sxs-lookup"><span data-stu-id="f94a3-112">Parallel Programming</span></span>](../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="f94a3-113">描述工作架構程式設計模型，該模型簡化了平行開發作業，讓您能夠利用簡單常見的語法，撰寫有效率、精細且具彈性的平行程式碼，而不需要直接使用執行緒或執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="f94a3-113">Describes a task-based programming model that simplifies parallel development, enabling you to write efficient, fine-grained, and scalable parallel code in a natural idiom without having to work directly with threads or the thread pool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f94a3-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="f94a3-114">See Also</span></span>  
 [<span data-ttu-id="f94a3-115">開發指南</span><span class="sxs-lookup"><span data-stu-id="f94a3-115">Development Guide</span></span>](../../docs/framework/development-guide.md)
