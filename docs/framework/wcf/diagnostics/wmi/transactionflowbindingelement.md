---
title: TransactionFlowBindingElement
ms.date: 03/30/2017
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
ms.openlocfilehash: 577502d1cd3d81784cb9b1eb3b249376b8ffa6b8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96234891"
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement

TransactionFlowBindingElement  
  
## <a name="syntax"></a>Syntax  
  
```csharp
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## <a name="methods"></a>方法  

 TransactionFlowBindingElement 類別並未定義任何方法。  
  
## <a name="properties"></a>屬性  

 TransactionFlowBindingElement 類別具有下列屬性：  
  
### <a name="issuedtokens"></a>IssuedTokens  

 資料類型：字串  
  
 存取類型：唯讀  
  
 指定所發行安全性權杖標頭 (WS-Trust 的 IssuedTokens) 的需求。  
  
### <a name="transactionprotocol"></a>TransactionProtocol  

 資料類型：字串  
  
 存取類型：唯讀  
  
 服務用來使異動流動的異動通訊協定。  
  
### <a name="transactions"></a>交易  

 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否支援傳入異動。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
