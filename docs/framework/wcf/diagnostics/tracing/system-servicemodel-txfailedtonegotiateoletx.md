---
title: System.ServiceModel.TxFailedToNegotiateOleTx
ms.date: 03/30/2017
ms.assetid: 3f0f0b4b-a1ad-4704-8329-455daf54892d
ms.openlocfilehash: 6aecc8f808d42c0096f6caef0574c72db6c53079
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54528659"
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a><span data-ttu-id="04afd-102">System.ServiceModel.TxFailedToNegotiateOleTx</span><span class="sxs-lookup"><span data-stu-id="04afd-102">System.ServiceModel.TxFailedToNegotiateOleTx</span></span>
<span data-ttu-id="04afd-103">OleTransactions 通訊協定無法完成指定的協調內容。</span><span class="sxs-lookup"><span data-stu-id="04afd-103">The OleTransactions protocol negotiation failed to complete for the specified coordination context.</span></span>  
  
## <a name="description"></a><span data-ttu-id="04afd-104">描述</span><span class="sxs-lookup"><span data-stu-id="04afd-104">Description</span></span>  
 <span data-ttu-id="04afd-105">在有 OleTx 資訊的傳入交易無法使用附加的 OleTx 資訊，而且將改用 WS-AT 時追蹤。</span><span class="sxs-lookup"><span data-stu-id="04afd-105">Traced when an incoming transaction with OleTx information is unable to use the attached OleTx information, and will fall-back to using WS-AT instead.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="04afd-106">疑難排解</span><span class="sxs-lookup"><span data-stu-id="04afd-106">Troubleshooting</span></span>  
 <span data-ttu-id="04afd-107">代表機器之間的 MSDTC RPC 通訊有潛在的問題。</span><span class="sxs-lookup"><span data-stu-id="04afd-107">Indicates a potential problem with MSDTC RPC communication between the machines.</span></span> <span data-ttu-id="04afd-108">如果記錄中出現這些追蹤中的多數，可能導致效能大幅下降。</span><span class="sxs-lookup"><span data-stu-id="04afd-108">If many of these traces appear in the log, a drastic decrease in performance can result.</span></span>  <span data-ttu-id="04afd-109">如果不需要 OleTx，在 WS-AT 登錄組態中將 `OleTxUpgradeEnabled` 設定為 0。</span><span class="sxs-lookup"><span data-stu-id="04afd-109">If OleTx is not desired, set `OleTxUpgradeEnabled` to 0 in the WS-AT registry configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04afd-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04afd-110">See also</span></span>
- [<span data-ttu-id="04afd-111">追蹤</span><span class="sxs-lookup"><span data-stu-id="04afd-111">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="04afd-112">使用追蹤為應用程式進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="04afd-112">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="04afd-113">管理與診斷</span><span class="sxs-lookup"><span data-stu-id="04afd-113">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
