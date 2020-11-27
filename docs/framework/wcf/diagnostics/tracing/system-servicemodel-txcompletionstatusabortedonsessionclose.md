---
title: System.ServiceModel.TxCompletionStatusAbortedOnSessionClose
ms.date: 03/30/2017
ms.assetid: 7e142e9d-e81b-4309-974a-02e9cc064ea0
ms.openlocfilehash: 0d8c77d01351b0c62e0186e5aee69ca70aebe15e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274318"
---
# <a name="systemservicemodeltxcompletionstatusabortedonsessionclose"></a><span data-ttu-id="979b3-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="979b3-102">System.ServiceModel.TxCompletionStatusAbortedOnSessionClose</span></span>

<span data-ttu-id="979b3-103">指定的異動已中止，因為當工作階段關閉時，異動未完成，並且 TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute 設定為 false。</span><span class="sxs-lookup"><span data-stu-id="979b3-103">The specified transaction was aborted because it was uncompleted when the session was closed and the TransactionAutoCompleteOnSessionClose OperationBehaviorAttribute was set to false.</span></span>  
  
## <a name="description"></a><span data-ttu-id="979b3-104">描述</span><span class="sxs-lookup"><span data-stu-id="979b3-104">Description</span></span>  

 <span data-ttu-id="979b3-105">如果目前使用中的工作階段已關閉，且交易尚未完成，加上 TransactionAutoCompleteOnSessionClose 設定為 `false`，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="979b3-105">Traced if the current active session was closed, and the transaction was not completed, and TransactionAutoCompleteOnSessionClose is set to `false`.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="979b3-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="979b3-106">Troubleshooting</span></span>  

 <span data-ttu-id="979b3-107">這個追蹤表示存在應該進行調查的潛在應用程式 Bug。</span><span class="sxs-lookup"><span data-stu-id="979b3-107">This trace indicates a potential application bug that should be investigated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="979b3-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="979b3-108">See also</span></span>

- [<span data-ttu-id="979b3-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="979b3-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="979b3-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="979b3-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="979b3-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="979b3-111">Administration and Diagnostics</span></span>](../index.md)
