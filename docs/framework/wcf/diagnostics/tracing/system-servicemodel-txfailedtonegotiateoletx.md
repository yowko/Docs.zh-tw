---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61360eff4f2c403eea98bbc0a2eae36e516b3d7a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="4bc17-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="4bc17-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="4bc17-103">OleTransactions 通訊協定無法完成指定的協調內容。</span><span class="sxs-lookup"><span data-stu-id="4bc17-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="4bc17-104">描述</span><span class="sxs-lookup"><span data-stu-id="4bc17-104">Description</span></span>  
 <span data-ttu-id="4bc17-105">在有 OleTx 資訊的傳入交易無法使用附加的 OleTx 資訊，而且將改用 WS-AT 時追蹤。</span><span class="sxs-lookup"><span data-stu-id="4bc17-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="4bc17-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="4bc17-106">Troubleshooting</span></span>  
 <span data-ttu-id="4bc17-107">代表機器之間的 MSDTC RPC 通訊有潛在的問題。</span><span class="sxs-lookup"><span data-stu-id="4bc17-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="4bc17-108">如果記錄中出現這些追蹤中的多數，可能導致效能大幅下降。</span><span class="sxs-lookup"><span data-stu-id="4bc17-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="4bc17-109">如果不需要 OleTx，在 WS-AT 登錄組態中將 `OleTxUpgradeEnabled` 設定為 0。</span><span class="sxs-lookup"><span data-stu-id="4bc17-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bc17-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bc17-110">See Also</span></span>  
 [<span data-ttu-id="4bc17-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="4bc17-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="4bc17-112">使用追蹤來疑難排解您的應用程式</span><span class="sxs-lookup"><span data-stu-id="4bc17-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="4bc17-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="4bc17-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
