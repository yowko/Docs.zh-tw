---
title: "自訂追蹤記錄"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51c47c3b11c912c1c67fe0d9ed4960de42f8a852
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="custom-tracking-records"></a><span data-ttu-id="0f87a-102">自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="0f87a-102">Custom Tracking Records</span></span>
<span data-ttu-id="0f87a-103">這個主題示範如何建立自訂追蹤記錄，並在其中填入發出的資料與記錄。</span><span class="sxs-lookup"><span data-stu-id="0f87a-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="0f87a-104">發出自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="0f87a-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="0f87a-105">程式碼活動可以發出自訂的追蹤記錄，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="0f87a-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="0f87a-106">在程式碼活動中發出 <xref:System.Activities.Tracking.CustomTrackingRecord>，方法是在 <xref:System.Activities.NativeActivityContext.Track%2A> 叫用 `ActvityContext` 方法。</span><span class="sxs-lookup"><span data-stu-id="0f87a-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f87a-107">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f87a-107">See Also</span></span>  
 [<span data-ttu-id="0f87a-108">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="0f87a-108">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="0f87a-109">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="0f87a-109">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
