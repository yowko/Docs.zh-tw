---
title: "HOW TO：使用合約介面來建立服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# HOW TO：使用合約介面來建立服務
建立 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 合約的慣用方式就是使用介面。此合約可指定存取服務提供之作業時所需的訊息集合與結構。此介面可將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面，並將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到您想要公開的方法上，藉此定義輸入與輸出類型。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]服務合約的詳細資訊，請參閱[設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)。  
  
### 使用介面來建立 WCF 合約  
  
1.  使用 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]、C\# 或其他任何的 Common Language Runtime 語言來建立新的介面。  
  
2.  將 <xref:System.ServiceModel.ServiceContractAttribute> 類別套用到介面。  
  
3.  在介面中定義方法。  
  
4.  將 <xref:System.ServiceModel.OperationContractAttribute> 類別套用到每個方法 \(必須當成公開 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 合約的一部分加以公開\) 上。  
  
## 範例  
 下列程式碼範例會顯示可定義服務合約的介面。  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 已套用 <xref:System.ServiceModel.OperationContractAttribute> 類別的方法依預設會使用要求\-回覆訊息模式。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]這個訊息模式的詳細資訊，請參閱 [HOW TO：建立要求\-回覆合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)。您也可以設定屬性 \(Attribute\) 的屬性 \(Property\) 來建立並使用其他訊息模式。如需更多範例，請參閱 [HOW TO：建立單向合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)和 [HOW TO：建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)。  
  
## 請參閱  
 <xref:System.ServiceModel.ServiceContractAttribute>   
 <xref:System.ServiceModel.OperationContractAttribute>