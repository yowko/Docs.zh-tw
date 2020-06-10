---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 2c9ea77cdd76d4593c2ee5b09a4b917677b8925f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601409"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="e6dc4-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="e6dc4-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="e6dc4-103">OleTransactions 通訊協定無法完成指定的協調內容。</span><span class="sxs-lookup"><span data-stu-id="e6dc4-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="e6dc4-104">描述</span><span class="sxs-lookup"><span data-stu-id="e6dc4-104">Description</span></span>  
 <span data-ttu-id="e6dc4-105">在有 OleTx 資訊的傳入交易無法使用附加的 OleTx 資訊，而且將改用 WS-AT 時追蹤。</span><span class="sxs-lookup"><span data-stu-id="e6dc4-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="e6dc4-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="e6dc4-106">Troubleshooting</span></span>  
 <span data-ttu-id="e6dc4-107">代表機器之間的 MSDTC RPC 通訊有潛在的問題。</span><span class="sxs-lookup"><span data-stu-id="e6dc4-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="e6dc4-108">如果記錄中出現這些追蹤中的多數，可能導致效能大幅下降。</span><span class="sxs-lookup"><span data-stu-id="e6dc4-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="e6dc4-109">如果不需要 OleTx，在 WS-AT 登錄組態中將 `OleTxUpgradeEnabled` 設定為 0。</span><span class="sxs-lookup"><span data-stu-id="e6dc4-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6dc4-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="e6dc4-110">See also</span></span>

- [<span data-ttu-id="e6dc4-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="e6dc4-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="e6dc4-112">使用追蹤來疑難排解應用程式</span><span class="sxs-lookup"><span data-stu-id="e6dc4-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="e6dc4-113">系統管理與診斷</span><span class="sxs-lookup"><span data-stu-id="e6dc4-113">Administration and Diagnostics</span></span>](../index.md)
