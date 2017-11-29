---
title: "非同步活動中的錯誤處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7606aeeeb3e2e583f9a217b78bcae4aebc6d8662
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="0878a-102">非同步活動中的錯誤處理</span><span class="sxs-lookup"><span data-stu-id="0878a-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="0878a-103">提供 <xref:System.Activities.AsyncCodeActivity> 中的錯誤處理包含在活動回呼系統中路由錯誤。</span><span class="sxs-lookup"><span data-stu-id="0878a-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="0878a-104">此主題描述如何使用 SendMail 活動範例取得在非同步作業中擲回主機的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0878a-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="0878a-105">傳回在非同步作業中擲回主機的錯誤。</span><span class="sxs-lookup"><span data-stu-id="0878a-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="0878a-106">在 SendMail 活動範例中路由在非同步作業中擲回主機的錯誤，包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0878a-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="0878a-107">將例外狀況屬性加入至 `SendMailAsyncResult` 類別。</span><span class="sxs-lookup"><span data-stu-id="0878a-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="0878a-108">將擲回錯誤複製到 `SendCompleted` 事件處理常式的該屬性。</span><span class="sxs-lookup"><span data-stu-id="0878a-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="0878a-109">在 `EndExecute` 事件處理常式中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0878a-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="0878a-110">產生的程式碼如下所示。</span><span class="sxs-lookup"><span data-stu-id="0878a-110">The resulting code is as follows.</span></span>  
  
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
