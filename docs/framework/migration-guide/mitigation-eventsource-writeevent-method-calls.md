---
title: "緩和：EventSource.WriteEvent 方法呼叫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 270f89183bced5d07598b1731f18acf90ec9715a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-eventsourcewriteevent-method-calls"></a><span data-ttu-id="4b711-102">緩和：EventSource.WriteEvent 方法呼叫</span><span class="sxs-lookup"><span data-stu-id="4b711-102">Mitigation: EventSource.WriteEvent Method Calls</span></span>
<span data-ttu-id="4b711-103">[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 強制在類別中的 ETW 事件方法間遵循協定，此類別是從其基底類別的 <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> 及 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法取得。</span><span class="sxs-lookup"><span data-stu-id="4b711-103">The [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] enforces a contract between an ETW event method in a class that is derived from <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> and  the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method of its base class.</span></span> <span data-ttu-id="4b711-104">ETW 事件方法必須對 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法傳遞事件 ID，後面跟著傳遞至此事件方法的相同引數。</span><span class="sxs-lookup"><span data-stu-id="4b711-104">The ETW event method must pass the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method the event ID followed by the same arguments that were passed to the event method.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="4b711-105">影響</span><span class="sxs-lookup"><span data-stu-id="4b711-105">Impact</span></span>  
 <span data-ttu-id="4b711-106">以下列方式定義的 ETW 事件方法會中斷協定：</span><span class="sxs-lookup"><span data-stu-id="4b711-106">An ETW event method defined in the following way breaks the contract:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message, "-");  
}  
```  
  
 <span data-ttu-id="4b711-107">當違反本協定時，如果 <xref:System.IndexOutOfRangeException> 物件在程序中讀取 <xref:System.Diagnostics.Tracing.EventListener> 資料， <xref:System.Diagnostics.Tracing.EventSource> 就會在執行階段擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4b711-107">When this contract is violated, an <xref:System.IndexOutOfRangeException> exception is thrown at run time if an <xref:System.Diagnostics.Tracing.EventListener> object reads <xref:System.Diagnostics.Tracing.EventSource> data in process.</span></span>  
  
 <span data-ttu-id="4b711-108">這個 ETW 事件方法的定義應該遵循這個模式：</span><span class="sxs-lookup"><span data-stu-id="4b711-108">The definition for this ETW event method should follow this pattern:</span></span>  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message);  
}  
```  
  
## <a name="mitigation"></a><span data-ttu-id="4b711-109">緩和</span><span class="sxs-lookup"><span data-stu-id="4b711-109">Mitigation</span></span>  
 <span data-ttu-id="4b711-110">您必須修改現有的程式碼，以符合所需的模式。</span><span class="sxs-lookup"><span data-stu-id="4b711-110">You must modify existing code to conform to the required pattern.</span></span>  
  
 <span data-ttu-id="4b711-111">您必須定義兩個用於呼叫 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法的方法，將需要變更的程式碼數量降到最低，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4b711-111">You can minimize the amount of code that you have to change by defining two methods for calling the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method, as follows:</span></span>  
  
```  
[NonEvent]  
public void Info2(string message)  
{  
   Info2Internal(message, "-");  
}  
  
public void Info2Internal(string message, string prefix)  
{  
   WriteEvent(2, message, prefix);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4b711-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b711-112">See Also</span></span>  
 [<span data-ttu-id="4b711-113">執行階段變更</span><span class="sxs-lookup"><span data-stu-id="4b711-113">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

