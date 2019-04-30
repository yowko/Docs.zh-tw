---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 7b1f6a2f4a344b566c76d0095942b84a8a4e76f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991623"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="9d18c-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="9d18c-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>
<span data-ttu-id="9d18c-103">指定的異動已中止，因為當工作階段關閉時，異動未完成，並且 TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="9d18c-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="9d18c-104">描述</span><span class="sxs-lookup"><span data-stu-id="9d18c-104">Description</span></span>  
 <span data-ttu-id="9d18c-105">如果目前使用中的工作階段已關閉，且交易尚未完成，加上 TransactionAutoCompleteOnSessionClose 設定為 `false`，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="9d18c-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="9d18c-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="9d18c-106">Troubleshooting</span></span>  
 <span data-ttu-id="9d18c-107">這個追蹤表示存在應該進行調查的潛在應用程式 Bug。</span><span class="sxs-lookup"><span data-stu-id="9d18c-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d18c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d18c-108">See also</span></span>

- [<span data-ttu-id="9d18c-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="9d18c-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="9d18c-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="9d18c-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="9d18c-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="9d18c-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
