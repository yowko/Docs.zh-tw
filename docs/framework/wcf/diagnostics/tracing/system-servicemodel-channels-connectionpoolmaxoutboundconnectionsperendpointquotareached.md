---
title: Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure
ms.date: 03/30/2017
ms.assetid: 1b9f5139-e122-4716-9ef7-2f38e1813993
ms.openlocfilehash: 4f51777ae690178b83d353f72e63a6f2958b1592
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674579"
---
# <a name="microsofttransactionstransactionbridgeenlisttransactionfailure"></a><span data-ttu-id="46ac0-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span><span class="sxs-lookup"><span data-stu-id="46ac0-102">Microsoft.Transactions.TransactionBridge.EnlistTransactionFailure</span></span>
<span data-ttu-id="46ac0-103">WS-AT 通訊協定服務無法使用所提供的協調內容登記異動。</span><span class="sxs-lookup"><span data-stu-id="46ac0-103">The WS-AT protocol service failed to enlist on a transaction using the provided coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="46ac0-104">描述</span><span class="sxs-lookup"><span data-stu-id="46ac0-104">Description</span></span>  
 <span data-ttu-id="46ac0-105">當 MSDTC 無法登記指定之 2pc 通訊協定的異動時，便會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="46ac0-105">Traced when MSDTC is unable to enlist on a transaction for a given 2pc protocol.</span></span>  <span data-ttu-id="46ac0-106">這種情況可能因為異動不再存在、不再允許登記，或是已經存在太多登記而發生。</span><span class="sxs-lookup"><span data-stu-id="46ac0-106">This can happen because the transaction no longer exists, enlisting is no longer allowed, or too many enlistments are already present.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="46ac0-107">疑難排解</span><span class="sxs-lookup"><span data-stu-id="46ac0-107">Troubleshooting</span></span>  
 <span data-ttu-id="46ac0-108">請檢查追蹤訊息內的狀態字串，以判斷是否有任何可執行動作的項目存在。</span><span class="sxs-lookup"><span data-stu-id="46ac0-108">Inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ac0-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46ac0-109">See also</span></span>
- [<span data-ttu-id="46ac0-110">追蹤</span><span class="sxs-lookup"><span data-stu-id="46ac0-110">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="46ac0-111">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="46ac0-111">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="46ac0-112">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="46ac0-112">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
