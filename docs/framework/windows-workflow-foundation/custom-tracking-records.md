---
title: 自訂追蹤記錄
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: ef3c20890f33f3ffd07a9c88de863e1ebe24851f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401247"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="e9c68-102">自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="e9c68-102">Custom Tracking Records</span></span>
<span data-ttu-id="e9c68-103">這個主題示範如何建立自訂追蹤記錄，並在其中填入發出的資料與記錄。</span><span class="sxs-lookup"><span data-stu-id="e9c68-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>  
  
## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="e9c68-104">發出自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="e9c68-104">Emitting Custom Tracking Records</span></span>  
 <span data-ttu-id="e9c68-105">程式碼活動可以發出自訂的追蹤記錄，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e9c68-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 <span data-ttu-id="e9c68-106">在程式碼活動中發出 <xref:System.Activities.Tracking.CustomTrackingRecord>，方法是在 <xref:System.Activities.NativeActivityContext.Track%2A> 叫用 `ActvityContext` 方法。</span><span class="sxs-lookup"><span data-stu-id="e9c68-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActvityContext`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9c68-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9c68-107">See Also</span></span>  
 [<span data-ttu-id="e9c68-108">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="e9c68-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="e9c68-109">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="e9c68-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
