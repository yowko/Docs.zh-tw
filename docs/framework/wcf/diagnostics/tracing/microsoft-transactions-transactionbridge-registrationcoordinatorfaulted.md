---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: 5066501faf4c336e095910e7e2d8ba1186ba3386
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251863"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="2c487-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="2c487-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>

<span data-ttu-id="2c487-103">WS-AT 通訊協定服務已從協調器接收到回應登錄訊息的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2c487-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="2c487-104">描述</span><span class="sxs-lookup"><span data-stu-id="2c487-104">Description</span></span>  

 <span data-ttu-id="2c487-105">如果本機 TransactionManager 因為傳回的錯誤而無法向它的上層 TransactionManager 登錄，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="2c487-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="2c487-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="2c487-106">Troubleshooting</span></span>  

 <span data-ttu-id="2c487-107">針對傳回的錯誤檢查追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="2c487-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c487-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c487-108">See also</span></span>

- [<span data-ttu-id="2c487-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="2c487-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="2c487-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="2c487-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="2c487-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="2c487-111">Administration and Diagnostics</span></span>](../index.md)
