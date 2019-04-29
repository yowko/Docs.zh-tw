---
title: 交易例外狀況
ms.date: 03/30/2017
ms.assetid: 1d27ed51-7eda-477f-9eca-94fa129f3e07
ms.openlocfilehash: 85d8d043a5610743d6cbad4d950330ed4bedb502
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936971"
---
# <a name="transaction-exceptions"></a>交易例外狀況
本主題列出 Windows Communication Foundation (WCF) 之交易所產生的所有例外狀況。  
  
## <a name="exception-list"></a>例外狀況清單  
  
|資源程式碼|資源字串|  
|-------------------|---------------------|  
|SFxCannotHaveDifferentTransactionProtocolsInOneBinding|將從中繼資料匯入的原則資訊會為各種作業中的 TransactionProtocol 指定不同值。 對於每個端點都只支援單一的 TransactionProtocol。|  
|SFxTransactionAutoCompleteFalseAndInstanceContextMode|TransactionAutoComplete 不能為 False，除非服務的 InstanceContextMode 是 PerSession。 在指定的合約與作業的實作上發現錯誤。|  
|SFxTransactionInvalidSetTransactionComplete|只有當 TransactionAutoComplete 設為 False，而且 TransactionScopeRequired 設定為 True 時，才能呼叫 SetTransactionComplete 方法。 此為無效狀況，目前異動將中止。|  
|TransactionFlowRequiredIssuedTokens|若要讓異動順利進行，必須支援流動發出的權杖。|  
|TrustDriverVersionDoesNotSupportIssuedTokens|設定的 Trust 版本不支援發出的權杖。 請使用 WSTrustFeb2005 或更新版本。|
