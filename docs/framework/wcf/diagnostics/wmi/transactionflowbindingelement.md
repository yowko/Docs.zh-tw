---
title: "TransactionFlowBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## 語法  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## 方法  
 TransactionFlowBindingElement 類別並未定義任何方法。  
  
## 屬性  
 TransactionFlowBindingElement 類別具有下列屬性：  
  
### IssuedTokens  
 資料型別：字串  
  
 存取類型：唯讀  
  
 指定所發行安全性權杖標頭 \(WS\-Trust 的 IssuedTokens\) 的需求。  
  
### TransactionProtocol  
 資料型別：字串  
  
 存取類型：唯讀  
  
 服務用來使交易流動的交易通訊協定。  
  
### 交易  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表是否支援傳入交易。  
  
## 需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------|  
|命名空間|於 root\\ServiceModel 中定義|  
  
## 請參閱  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>