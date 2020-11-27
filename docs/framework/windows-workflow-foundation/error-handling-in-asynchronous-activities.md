---
title: 非同步活動中的錯誤處理
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 2c214ce1d0f435cda79deb6976ca9196a5d7aee1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280256"
---
# <a name="error-handling-in-asynchronous-activities"></a>非同步活動中的錯誤處理

提供 <xref:System.Activities.AsyncCodeActivity> 中的錯誤處理包含在活動回呼系統中路由錯誤。 此主題描述如何使用 SendMail 活動範例取得在非同步作業中擲回主機的錯誤。  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a>傳回在非同步作業中擲回主機的錯誤。  

 在 SendMail 活動範例中路由在非同步作業中擲回主機的錯誤，包含下列步驟：  
  
- 將例外狀況屬性加入至 `SendMailAsyncResult` 類別。  
  
- 將擲回錯誤複製到 `SendCompleted` 事件處理常式的該屬性。  
  
- 在 `EndExecute` 事件處理常式中擲回例外狀況。  
  
 產生的程式碼如下所示。  
  
```csharp  
class SendMailAsyncResult : IAsyncResult  
        {  
            …  
            public Exception Error { get; set; }
            …  
            void SendCompleted(object sender, AsyncCompletedEventArgs e)  
            {  
                Error = e.Error;  
                this.asyncWaitHandle.Set();  
                callback(this);  
            }  
         }  
  
    public sealed class SendMail: AsyncCodeActivity  
    {  
         …  
        protected override void EndExecute(AsyncCodeActivityContext context, IAsyncResult result)  
        {  
            SendMailAsyncResult sendMailResult = result as SendMailAsyncResult;  
            if (sendMailResult != null && sendMailResult.Error != null)  
                throw sendMailResult.Error;
        }  
    }  
```
