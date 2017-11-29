---
title: Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2194292d-bf5f-4aef-9336-cd3c4795cb71
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 88ee90abb10e9f5e09deecb3d3d66c54dc289592
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="microsofttransactionstransactionbridgepreparedmessageretry"></a>Microsoft.Transactions.TransactionBridge.PreparedMessageRetry
準備訊息重試已傳送給沒有回應的協調器。  
  
## <a name="description"></a>描述  
 追蹤本機交易管理員是否因為上層協調器未在指定時間內接收到回應，而需要重新傳送「準備」訊息給上層協調器。  
  
## <a name="troubleshooting"></a>疑難排解  
 調查讓回應無法準時傳遞的潛在網路或產品問題。  如果看到許多這類訊息，這可能表示基礎結構發生問題或回應時間異常地長。 這兩個問題都會大幅降低系統內的異動量。  
  
## <a name="see-also"></a>另請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤來疑難排解您的應用程式](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
