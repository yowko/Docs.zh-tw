---
title: "HOW TO：控制服務執行個體 | Microsoft Docs"
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
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# HOW TO：控制服務執行個體
設定服務的執行個體模式，可讓您指定 <xref:System.ServiceModel.InstanceContext?displayProperty=fullName> \(及其相關之使用者定義的服務物件\) 建立的時機。  如需可能的模式，請參閱 <xref:System.ServiceModel.InstanceContextMode> 列舉。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]行為的詳細資訊，請參閱 [使用行為來設定與擴充執行階段](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  如需實用範例，請參閱[行為](../../../../docs/framework/wcf/samples/behaviors.md)。  
  
### 使用程式碼控制服務執行個體存留期  
  
1.  將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 套用至服務類別。  
  
2.  將 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性設定為下列其中一值：<xref:System.ServiceModel.InstanceContextMode>、<xref:System.ServiceModel.InstanceContextMode> 或 <xref:System.ServiceModel.InstanceContextMode>。  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## 範例  
 下列程式碼範例會將 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性 \(Attribute\) 的 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性 \(Property\) 設定為 <xref:System.ServiceModel.InstanceContextMode>。  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## 請參閱  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>   
 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>   
 <xref:System.ServiceModel.InstanceContextMode>   
 [Service: Behaviors Samples](http://msdn.microsoft.com/zh-tw/4e3c6513-a7ff-4b35-8dcf-b5506c6f39a7)