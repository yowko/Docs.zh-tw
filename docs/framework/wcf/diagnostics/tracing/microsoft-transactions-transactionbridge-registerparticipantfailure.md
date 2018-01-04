---
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02831a83103f5a6bd83fc2aed474245bdeda65d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a>Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
WS-AT 通訊協定服務無法登錄控制通訊協定的參與者。  
  
## <a name="description"></a>描述  
 如果 MSDTC 偵測到無效的登錄要求則會進行追蹤。 這種情形可能是因為多個完成登錄要求和內部錯誤所造成。  
  
## <a name="troubleshooting"></a>疑難排解  
 請勿嘗試多次登錄完成。  同時，檢查追蹤訊息內的狀態字串，以判斷是否有任何可執行動作的項目存在。  
  
## <a name="see-also"></a>請參閱  
 [追蹤](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [使用追蹤為應用程式進行疑難排解](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [管理與診斷](../../../../../docs/framework/wcf/diagnostics/index.md)
