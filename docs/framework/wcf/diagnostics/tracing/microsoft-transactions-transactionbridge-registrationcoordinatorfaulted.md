---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: f634816b2459d2e0b6137e2e87fef907824af017
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61997720"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="87327-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="87327-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="87327-103">WS-AT 通訊協定服務已從協調器接收到回應登錄訊息的錯誤。</span><span class="sxs-lookup"><span data-stu-id="87327-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="87327-104">描述</span><span class="sxs-lookup"><span data-stu-id="87327-104">Description</span></span>  
 <span data-ttu-id="87327-105">如果本機 TransactionManager 因為傳回的錯誤而無法向它的上層 TransactionManager 登錄，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="87327-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="87327-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="87327-106">Troubleshooting</span></span>  
 <span data-ttu-id="87327-107">針對傳回的錯誤檢查追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="87327-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87327-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87327-108">See also</span></span>

- [<span data-ttu-id="87327-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="87327-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="87327-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="87327-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="87327-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="87327-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
