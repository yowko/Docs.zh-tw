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

- [Windows Server App Fabric 監控](https://go.microsoft.com/fwlink/?LinkId=201273)
- [使用 App Fabric 監控應用程式](https://go.microsoft.com/fwlink/?LinkId=201275)
