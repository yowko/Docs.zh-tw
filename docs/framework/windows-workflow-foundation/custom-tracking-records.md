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
# <a name="custom-tracking-records"></a>自訂追蹤記錄

這個主題示範如何建立自訂追蹤記錄，並在其中填入發出的資料與記錄。

## <a name="emitting-custom-tracking-records"></a>發出自訂追蹤記錄

程式碼活動可以發出自訂的追蹤記錄，如下列範例所示。

```csharp
protected override void Execute(CodeActivityContext context)
{
…
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");
            customRecord.Data.Add("SendTime", sendTime);
            context.Track(customRecord);
}
```

在程式碼活動中發出 <xref:System.Activities.Tracking.CustomTrackingRecord>，方法是在 <xref:System.Activities.NativeActivityContext.Track%2A> 叫用 `ActivityContext` 方法。

## <a name="see-also"></a>另請參閱

- [Windows Server App Fabric 監視](/previous-versions/appfabric/ee677251(v=azure.10))
- [使用 App Fabric 監視應用程式](/previous-versions/appfabric/ee677276(v=azure.10))
