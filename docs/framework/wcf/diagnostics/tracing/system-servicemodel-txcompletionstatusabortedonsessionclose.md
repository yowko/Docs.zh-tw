---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e9ab5af359b833452664f534e3627f477246fa6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="2576c-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="2576c-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="2576c-103">指定的異動已中止，因為當工作階段關閉時，異動未完成，並且 TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="2576c-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2576c-104">描述</span><span class="sxs-lookup"><span data-stu-id="2576c-104">Description</span></span>  
 <span data-ttu-id="2576c-105">如果目前使用中的工作階段已關閉，且交易尚未完成，加上 TransactionAutoCompleteOnSessionClose 設定為 `false`，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="2576c-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2576c-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="2576c-106">Troubleshooting</span></span>  
 <span data-ttu-id="2576c-107">這個追蹤表示存在應該進行調查的潛在應用程式 Bug。</span><span class="sxs-lookup"><span data-stu-id="2576c-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2576c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2576c-108">See Also</span></span>  
 [<span data-ttu-id="2576c-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="2576c-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="2576c-110">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="2576c-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="2576c-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="2576c-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
