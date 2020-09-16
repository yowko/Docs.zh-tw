---
title: 自訂追蹤記錄
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: e0bbb9d57290b072d834f0b8bc0815dfe265e72a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543897"
---
# <a name="custom-tracking-records"></a><span data-ttu-id="a15e4-102">自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="a15e4-102">Custom Tracking Records</span></span>

<span data-ttu-id="a15e4-103">這個主題示範如何建立自訂追蹤記錄，並在其中填入發出的資料與記錄。</span><span class="sxs-lookup"><span data-stu-id="a15e4-103">This topic demonstrates how to create custom tracking records and populate them with data to be emitted along with the records.</span></span>

## <a name="emitting-custom-tracking-records"></a><span data-ttu-id="a15e4-104">發出自訂追蹤記錄</span><span class="sxs-lookup"><span data-stu-id="a15e4-104">Emitting Custom Tracking Records</span></span>

<span data-ttu-id="a15e4-105">程式碼活動可以發出自訂的追蹤記錄，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a15e4-105">Custom tracking records can be emitted from a code activity as shown in the following example.</span></span>

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

<span data-ttu-id="a15e4-106">在程式碼活動中發出 <xref:System.Activities.Tracking.CustomTrackingRecord>，方法是在 <xref:System.Activities.NativeActivityContext.Track%2A> 叫用 `ActivityContext` 方法。</span><span class="sxs-lookup"><span data-stu-id="a15e4-106">A <xref:System.Activities.Tracking.CustomTrackingRecord> is emitted in a code activity by invoking the <xref:System.Activities.NativeActivityContext.Track%2A> method on the `ActivityContext`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a15e4-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a15e4-107">See also</span></span>

- <span data-ttu-id="a15e4-108">[Windows Server App Fabric 監視](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a15e4-108">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="a15e4-109">[使用 App Fabric 監視應用程式](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="a15e4-109">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
