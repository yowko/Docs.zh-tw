---
title: System.ServiceModel.Channels.ConnectionPoolCloseException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8358898e-129e-4fac-a6bf-bf3aa4293ae2
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4e8eee0ebc3702445b41d1f81742d18dfa98d44
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodelchannelsconnectionpoolcloseexception"></a><span data-ttu-id="dad11-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span><span class="sxs-lookup"><span data-stu-id="dad11-102">System.ServiceModel.Channels.ConnectionPoolCloseException</span></span>
<span data-ttu-id="dad11-103">關閉此連線集區中的連線時發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="dad11-103">An exception occurred while closing the connections in this connection pool.</span></span>  
  
## <a name="description"></a><span data-ttu-id="dad11-104">描述</span><span class="sxs-lookup"><span data-stu-id="dad11-104">Description</span></span>  
 <span data-ttu-id="dad11-105">這個錯誤層級追蹤指出，在關閉由 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 的連接共用功能所使用的連線集區時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="dad11-105">This error level trace indicates that an error has occurred while closing the connection pools used by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]’s connection pooling feature.</span></span> <span data-ttu-id="dad11-106">可能是因為 CloseTimeout 內的某個共用連線或某組共用連線未成功關閉。</span><span class="sxs-lookup"><span data-stu-id="dad11-106">One possible reason for this is an unsuccessful closure of a pooled connection, or a set of pooled connections within the CloseTimeout.</span></span> <span data-ttu-id="dad11-107">擲回此例外狀況時，同集區內其餘未關閉的連線都會中止，其他集區內未關閉的連線則會被放棄。</span><span class="sxs-lookup"><span data-stu-id="dad11-107">When this exception is thrown, any remaining unclosed connections within that pool are aborted; unclosed connections within other pools are abandoned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad11-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dad11-108">See Also</span></span>  
 [<span data-ttu-id="dad11-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="dad11-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="dad11-110">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="dad11-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="dad11-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="dad11-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
