---
title: Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted
ms.date: 03/30/2017
ms.assetid: 8193027e-9db2-4af9-a072-27300cd24330
ms.openlocfilehash: ad9d82162313e46626e5e2fa6f4ef99bf0139162
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599642"
---
# <a name="microsofttransactionstransactionbridgeregistrationcoordinatorfaulted"></a><span data-ttu-id="b1985-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span><span class="sxs-lookup"><span data-stu-id="b1985-102">Microsoft.Transactions.TransactionBridge.RegistrationCoordinatorFaulted</span></span>
<span data-ttu-id="b1985-103">WS-AT 通訊協定服務已從協調器接收到回應登錄訊息的錯誤。</span><span class="sxs-lookup"><span data-stu-id="b1985-103">The WS-AT protocol service received a fault from its coordinator in response to a Register message.</span></span>  
  
## <a name="description"></a><span data-ttu-id="b1985-104">描述</span><span class="sxs-lookup"><span data-stu-id="b1985-104">Description</span></span>  
 <span data-ttu-id="b1985-105">如果本機 TransactionManager 因為傳回的錯誤而無法向它的上層 TransactionManager 登錄，則會進行追蹤。</span><span class="sxs-lookup"><span data-stu-id="b1985-105">Traced if the local TransactionManager is not able to Register with its superior TransactionManager due to a fault being returned.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="b1985-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="b1985-106">Troubleshooting</span></span>  
 <span data-ttu-id="b1985-107">針對傳回的錯誤檢查追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="b1985-107">Inspect the trace message for the fault returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1985-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="b1985-108">See also</span></span>

- [<span data-ttu-id="b1985-109">追蹤</span><span class="sxs-lookup"><span data-stu-id="b1985-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="b1985-110">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="b1985-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="b1985-111">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="b1985-111">Administration and Diagnostics</span></span>](../index.md)
