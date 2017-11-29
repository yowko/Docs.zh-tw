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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9a459e6df0e030f4e17bb73461d8fa790a61787e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="custom-tracking-records"></a>自訂追蹤記錄
這個主題示範如何建立自訂追蹤記錄，並在其中填入發出的資料與記錄。  
  
## <a name="emitting-custom-tracking-records"></a>發出自訂追蹤記錄  
 程式碼活動可以發出自訂的追蹤記錄，如下列範例所示。  
  
```  
protected override void Execute(CodeActivityContext context)  
{  
…  
            CustomTrackingRecord customRecord = new CustomTrackingRecord("CustomEmailSentEvent");  
            customRecord.Data.Add("SendTime", sendTime);  
            context.Track(customRecord);  
}  
```  
  
 在程式碼活動中發出 <xref:System.Activities.Tracking.CustomTrackingRecord>，方法是在 <xref:System.Activities.NativeActivityContext.Track%2A> 叫用 `ActvityContext` 方法。  
  
## <a name="see-also"></a>另請參閱  
 [Windows Server App Fabric 監控](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [使用 App Fabric 監控應用程式](http://go.microsoft.com/fwlink/?LinkId=201275)
