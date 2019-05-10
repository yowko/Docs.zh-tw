---
title: 非同步活動中的錯誤處理
ms.date: 03/30/2017
ms.assetid: e8f8ce2b-50c9-4e44-b187-030e0cf30a5d
ms.openlocfilehash: 7a1db144e4738870d3ff5fe68df11b2fb06ef3d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64640953"
---
# <a name="error-handling-in-asynchronous-activities"></a><span data-ttu-id="78f7d-102">非同步活動中的錯誤處理</span><span class="sxs-lookup"><span data-stu-id="78f7d-102">Error handling in asynchronous activities</span></span>
<span data-ttu-id="78f7d-103">提供 <xref:System.Activities.AsyncCodeActivity> 中的錯誤處理包含在活動回呼系統中路由錯誤。</span><span class="sxs-lookup"><span data-stu-id="78f7d-103">Providing error handling in an <xref:System.Activities.AsyncCodeActivity> involves routing the error through the activity’s callback system.</span></span> <span data-ttu-id="78f7d-104">此主題描述如何使用 SendMail 活動範例取得在非同步作業中擲回主機的錯誤。</span><span class="sxs-lookup"><span data-stu-id="78f7d-104">This topic describes how to get an error that is thrown in an asynchronous operation back to the host, using the SendMail activity sample.</span></span>  
  
## <a name="returning-an-error-thrown-in-an-asynchronous-activity-back-to-the-host"></a><span data-ttu-id="78f7d-105">傳回在非同步作業中擲回主機的錯誤。</span><span class="sxs-lookup"><span data-stu-id="78f7d-105">Returning an error thrown in an asynchronous activity back to the host</span></span>  
 <span data-ttu-id="78f7d-106">在 SendMail 活動範例中路由在非同步作業中擲回主機的錯誤，包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="78f7d-106">Routing an error in an asynchronous operation back to the host in the SendMail activity sample involves the following steps:</span></span>  
  
- <span data-ttu-id="78f7d-107">將例外狀況屬性加入至 `SendMailAsyncResult` 類別。</span><span class="sxs-lookup"><span data-stu-id="78f7d-107">Add an Exception property to the `SendMailAsyncResult` class.</span></span>  
  
- <span data-ttu-id="78f7d-108">將擲回錯誤複製到 `SendCompleted` 事件處理常式的該屬性。</span><span class="sxs-lookup"><span data-stu-id="78f7d-108">Copy the thrown error to that property in the `SendCompleted` event handler.</span></span>  
  
- <span data-ttu-id="78f7d-109">在 `EndExecute` 事件處理常式中擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="78f7d-109">Throw the exception in the `EndExecute` event handler.</span></span>  
  
 <span data-ttu-id="78f7d-110">產生的程式碼如下所示。</span><span class="sxs-lookup"><span data-stu-id="78f7d-110">The resulting code is as follows.</span></span>  
  
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
