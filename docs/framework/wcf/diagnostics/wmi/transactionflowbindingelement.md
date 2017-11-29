---
title: TransactionFlowBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4c65eb1689d1411cb9083967b9a29c946b7568b7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transactionflowbindingelement"></a>TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## <a name="syntax"></a>語法  
  
```  
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
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定所發行安全性權杖標頭 (WS-Trust 的 IssuedTokens) 的需求。  
  
### <a name="transactionprotocol"></a>TransactionProtocol  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務用來使交易流動的交易通訊協定。  
  
### <a name="transactions"></a>異動  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否支援傳入交易。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
