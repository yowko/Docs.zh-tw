---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: f634816b2459d2e0b6137e2e87fef907824af017
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163029"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="4df87-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="4df87-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="4df87-103">WS-AT 通訊協定服務已從協調器接收到回應登錄訊息的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4df87-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4df87-104">描述</span><span class="sxs-lookup"><span data-stu-id="4df87-104">Description</span></span>  
 <span data-ttu-id="4df87-105">如果本機 TransactionManager 因為傳回的錯誤而無法向它的上層 TransactionManager 登錄，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="4df87-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4df87-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4df87-106">Troubleshooting</span></span>  
 <span data-ttu-id="4df87-107">針對傳回的錯誤檢查追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="4df87-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4df87-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4df87-108">See also</span></span>

- [<span data-ttu-id="4df87-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="4df87-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="4df87-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="4df87-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="4df87-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="4df87-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
