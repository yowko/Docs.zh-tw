---
title: 自訂追蹤記錄
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: d4733b4ffc0d866cf90fd5a5e7d649de261c45fb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499117"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="2eacf-102">自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="2eacf-102">Custom Tracking Records</span></span>

<span data-ttu-id="2eacf-103">這個主題示範如何建立自訂追蹤記錄，並在其中填入發出的資料與記錄。</span><span class="sxs-lookup"><span data-stu-id="2eacf-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="2eacf-104">發出自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="2eacf-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="2eacf-105">程式碼活動可以發出自訂的追蹤記錄，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2eacf-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="2eacf-106">在程式碼活動中發出 <xref:System.Activities.Tracking.CustomTrackingRecord>，方法是在 <xref:System.Activities.NativeActivityContext.Track%2A> 叫用 `ActivityContext` 方法。</span><span class="sxs-lookup"><span data-stu-id="2eacf-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="2eacf-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2eacf-107">See also</span></span>

- [<span data-ttu-id="2eacf-108">Windows Server App Fabric 監控</span><span class="sxs-lookup"><span data-stu-id="2eacf-108">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="2eacf-109">使用 App Fabric 監控應用程式</span><span class="sxs-lookup"><span data-stu-id="2eacf-109">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
