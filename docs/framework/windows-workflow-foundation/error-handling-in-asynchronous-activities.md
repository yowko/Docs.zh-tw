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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7c23dec2f92ed8654d5f0460966dc19af0a8405
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="d98ac-102">非同步活動中的錯誤處理</span><span class="sxs-lookup"><span data-stu-id="d98ac-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="d98ac-103">提供 <xref:System.Activities.AsyncCodeActivity> 中的錯誤處理包含在活動回呼系統中路由錯誤。</span><span class="sxs-lookup"><span data-stu-id="d98ac-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="d98ac-104">此主題描述如何使用 SendMail 活動範例取得在非同步作業中擲回主機的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d98ac-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="d98ac-105">傳回在非同步作業中擲回主機的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d98ac-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="d98ac-106">在 SendMail 活動範例中路由在非同步作業中擲回主機的錯誤，包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d98ac-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
-   <span data-ttu-id="d98ac-107">將例外狀況屬性加入至 `SendMailAsyncResult` 類別。</span><span class="sxs-lookup"><span data-stu-id="d98ac-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
-   <span data-ttu-id="d98ac-108">將擲回錯誤複製到 `SendCompleted` 事件處理常式的該屬性。</span><span class="sxs-lookup"><span data-stu-id="d98ac-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
-   <span data-ttu-id="d98ac-109">在 `EndExecute` 事件處理常式中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d98ac-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="d98ac-110">產生的程式碼如下所示。</span><span class="sxs-lookup"><span data-stu-id="d98ac-110">The resulting code is as follows.</span></span>  
  
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
