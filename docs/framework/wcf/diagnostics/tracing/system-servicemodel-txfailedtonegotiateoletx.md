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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eb632712a4f7855c16593ac313221f588040d0fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodeltxfailedtonegotiateoletx"></a>System.ServiceModel.TxFailedToNegotiateOleTx
OleTransactions 通訊協定無法完成指定的協調內容。  
  
## <a name="description"></a>描述  
 在有 OleTx 資訊的傳入交易無法使用附加的 OleTx 資訊，而且將改用 WS-AT 時追蹤。  
  
## <a name="troubleshooting"></a>疑難排解  
 代表機器之間的 MSDTC RPC 通訊有潛在的問題。 如果記錄中出現這些追蹤中的多數，可能導致效能大幅下降。  如果不需要 OleTx，在 WS-AT 登錄組態中將 `OleTxUpgradeEnabled` 設定為 0。  
  
## <a name="see-also"></a>請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
