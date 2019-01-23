---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: 6b25c9f9aed30e06d503deb52880ef928857541a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54591042"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="d58ca-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="d58ca-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="d58ca-103">WS-AT 通訊協定服務已從協調器接收到回應登錄訊息的錯誤。</span><span class="sxs-lookup"><span data-stu-id="d58ca-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d58ca-104">描述</span><span class="sxs-lookup"><span data-stu-id="d58ca-104">Description</span></span>  
 <span data-ttu-id="d58ca-105">如果本機 TransactionManager 因為傳回的錯誤而無法向它的上層 TransactionManager 登錄，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="d58ca-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d58ca-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="d58ca-106">Troubleshooting</span></span>  
 <span data-ttu-id="d58ca-107">針對傳回的錯誤檢查追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="d58ca-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d58ca-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d58ca-108">See also</span></span>
- [<span data-ttu-id="d58ca-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="d58ca-109">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="d58ca-110">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="d58ca-110">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d58ca-111">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="d58ca-111">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
