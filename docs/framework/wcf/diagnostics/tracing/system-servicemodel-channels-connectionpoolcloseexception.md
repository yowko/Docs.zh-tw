---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.date: 03/30/2017
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
ms.openlocfilehash: d8edb8e916578247e62e3a3eb3b11b80f93416cd
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286951"
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="9d3ab-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="9d3ab-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>

<span data-ttu-id="9d3ab-103">關閉此連線集區中的連線時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9d3ab-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9d3ab-104">描述</span><span class="sxs-lookup"><span data-stu-id="9d3ab-104">Description</span></span>  

 <span data-ttu-id="9d3ab-105">這個錯誤層級追蹤指出，關閉 Windows Communication Foundation (WCF) 的連接共用功能所使用的連接集區時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d3ab-105">This error level trace indicates that an error has occurred while closing the connection pools used by Windows Communication Foundation (WCF)’s connection pooling feature.</span></span> <span data-ttu-id="9d3ab-106">可能是因為 CloseTimeout 內的某個共用連線或某組共用連線未成功關閉。</span><span class="sxs-lookup"><span data-stu-id="9d3ab-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="9d3ab-107">擲回此例外狀況時，同集區內其餘未關閉的連線都會中止，其他集區內未關閉的連線則會被放棄。</span><span class="sxs-lookup"><span data-stu-id="9d3ab-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3ab-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d3ab-108">See also</span></span>

- [<span data-ttu-id="9d3ab-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="9d3ab-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="9d3ab-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="9d3ab-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9d3ab-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="9d3ab-111">Administration and Diagnostics</span></span>](../index.md)
