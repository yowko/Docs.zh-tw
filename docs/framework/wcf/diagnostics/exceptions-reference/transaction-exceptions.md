---
title: "異動例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f13a39c251afd55dbb1f0d2dde4fc66fe38d30a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="transaction-exceptions"></a>異動例外狀況
本主題會列出 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 交易所產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|將從中繼資料匯入的原則資訊會為各種作業中的 TransactionProtocol 指定不同值。 對於每個端點都只支援單一的 TransactionProtocol。|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete 不能為 False，除非服務的 InstanceContextMode 是 PerSession。 在指定的合約與作業的實作上發現錯誤。|  
|SFxTransactionInvalidSetTransactionComplete|只有當 TransactionAutoComplete 設為 False，而且 TransactionScopeRequired 設定為 True 時，才能呼叫 SetTransactionComplete 方法。 此為無效狀況，目前異動將中止。|  
|TransactionFlowRequiredIssuedTokens|若要讓交易順利進行，必須支援流動發出的權杖。|  
|TrustDriverVersionDoesNotSupportIssuedTokens|設定的 Trust 版本不支援發出的權杖。 請使用 WSTrustFeb2005 或更新版本。|
