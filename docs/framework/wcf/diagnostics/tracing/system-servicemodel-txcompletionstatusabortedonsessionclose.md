---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: f41fd08138591a90b6173b5e4806e5ac73ff07da
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662760"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="e3cd8-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="e3cd8-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="e3cd8-103">指定的異動已中止，因為當工作階段關閉時，異動未完成，並且 TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="e3cd8-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e3cd8-104">描述</span><span class="sxs-lookup"><span data-stu-id="e3cd8-104">Description</span></span>  
 <span data-ttu-id="e3cd8-105">如果目前使用中的工作階段已關閉，且交易尚未完成，加上 TransactionAutoCompleteOnSessionClose 設定為 `false`，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="e3cd8-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e3cd8-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e3cd8-106">Troubleshooting</span></span>  
 <span data-ttu-id="e3cd8-107">這個追蹤表示存在應該進行調查的潛在應用程式 Bug。</span><span class="sxs-lookup"><span data-stu-id="e3cd8-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3cd8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3cd8-108">See also</span></span>
- [<span data-ttu-id="e3cd8-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="e3cd8-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="e3cd8-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="e3cd8-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e3cd8-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="e3cd8-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
