---
title: "HOW TO：建立類別或結構的基本資料合約 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "資料合約 [WCF], 為類別或結構建立"
  - "DataContractAttribute 類別"
  - "DataMemberAttribute"
ms.assetid: bc464889-3070-4a2f-91d2-e788a0f686a7
caps.latest.revision: 25
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 25
---
# HOW TO：建立類別或結構的基本資料合約
本主題將示範使用類別或結構來建立資料合約的基本步驟。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]資料合約以及如何使用的詳細資訊，請參閱 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。  
  
 如需逐步說明建立基本 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務和用戶端之步驟的教學課程，請參閱[快速入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)。  如需由基本服務和用戶端組成的工作範例應用程式，請參閱[基本資料合約](../../../../docs/framework/wcf/samples/basic-data-contract.md)。  
  
### 建立類別或結構的基本資料合約  
  
1.  請將 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性套用至類別，以宣告型別具有資料合約。  請注意，所有公用型別 \(包括不含屬性的公用型別\) 都是可序列化的。  如果沒有 <xref:System.Runtime.Serialization.DataContractAttribute> 屬性，<xref:System.Runtime.Serialization.DataContractSerializer> 會推斷資料合約。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]，請參閱 [可序列化的型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。  
  
2.  藉由將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 \(Attribute\) 套用至各個成員，定義序列化的成員 \(屬性 \(Property\)、欄位或事件\)。  這些成員稱為資料成員。  根據預設，所有公用型別都是可序列化的。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]，請參閱 [可序列化的型別](../../../../docs/framework/wcf/feature-details/serializable-types.md)。  
  
    > [!NOTE]
    >  您可以將 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至私用欄位，造成資料對他人公開。  請確定成員沒有包含敏感性資料。  
  
## 範例  
 下列範例說明如何將 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性套用至類別和其成員，以建立 `Person` 型別的資料合約。  
  
 [!code-csharp[DataContractAttribute#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#2)]
 [!code-vb[DataContractAttribute#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#2)]  
  
## 請參閱  
 <xref:System.Runtime.Serialization.DataContractAttribute>   
 <xref:System.Runtime.Serialization.DataMemberAttribute>   
 [使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)   
 [快速入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)   
 [使用者入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)