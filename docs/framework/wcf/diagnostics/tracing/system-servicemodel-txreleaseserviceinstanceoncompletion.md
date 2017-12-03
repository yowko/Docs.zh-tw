---
title: System.ServiceModel.TxReleaseServiceInstanceOnCompletion
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e167bad3-861f-43e4-9e78-9c275cf64a29
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2242d0aa4deccd12df257cffcc1137fd49e2da83
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="systemservicemodeltxreleaseserviceinstanceoncompletion"></a><span data-ttu-id="f8fad-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span><span class="sxs-lookup"><span data-stu-id="f8fad-102">System.ServiceModel.TxReleaseServiceInstanceOnCompletion</span></span>
<span data-ttu-id="f8fad-103">因為 ReleaseServiceInstanceOnTransactionComplete ServiceBehaviorAttribute 設定為 true，所以交易 '{0}' 完成時會釋放服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="f8fad-103">The service instance was released on the completion of the transaction '{0}' because the ReleaseServiceInstanceOnTransactionComplete ServiceBehaviorAttribute was set to true.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f8fad-104">描述</span><span class="sxs-lookup"><span data-stu-id="f8fad-104">Description</span></span>  
 <span data-ttu-id="f8fad-105">在因為目前的現用交易完成、且 ReleaseServiceInstanceOnTransactionComplete 設定為 `true` 的情況下釋放或處置現行服務執行個體時，就會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="f8fad-105">Traced when the current service instance is released or disposed due to the completion of the current active transaction and ReleaseServiceInstanceOnTransactionComplete is set to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8fad-106">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8fad-106">See Also</span></span>  
 [<span data-ttu-id="f8fad-107">追蹤</span><span class="sxs-lookup"><span data-stu-id="f8fad-107">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="f8fad-108">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="f8fad-108">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="f8fad-109">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="f8fad-109">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
