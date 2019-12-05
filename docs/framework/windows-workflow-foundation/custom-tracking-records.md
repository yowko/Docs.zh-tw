---
title: 自訂追蹤記錄
ms.date: 03/30/2017
ms.assetid: 24284565-c68b-40bf-b7f1-e148d151a6fc
ms.openlocfilehash: 986f0350c24414d0ff960474445adf6ac3f39734
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802618"
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

## <a name="see-also"></a>請參閱

- [Windows Server App Fabric 監視](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [使用 App Fabric 監視應用程式](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
