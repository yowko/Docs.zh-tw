---
title: "HOW TO：匯出自訂原則判斷提示 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99030386-43b0-4f7b-866d-17ea307f5cbd
caps.latest.revision: 12
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 12
---
# HOW TO：匯出自訂原則判斷提示
原則判斷提示描述服務端點的功能與需求。服務應用程式可使用服務中繼資料中的自訂原則判斷提示，與用戶端應用程式進行端點、繫結或合約自訂資訊的通訊。您可使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 附加於端點、作業或訊息物件 WSDL 繫結的原則運算式匯出判斷提示，根據您通訊的功能或要求而定。  
  
 匯出自訂原則判斷提示的方法，是實作 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> 上的 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> 介面，然後直接將繫結項目插入服務端點的繫結或將繫結項目登錄於應用程式組態檔。您的原則匯出實作應將您的自訂原則判斷提示當成 <xref:System.Xml.XmlElement?displayProperty=fullName> 執行個體新增至位於傳入 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> 方法的 <xref:System.ServiceModel.Description.PolicyConversionContext?displayProperty=fullName> 上之合適 <xref:System.ServiceModel.Description.PolicyAssertionCollection?displayProperty=fullName>。  
  
 除此之外，您還必須檢查 <xref:System.ServiceModel.Description.WsdlExporter> 類別的 <xref:System.ServiceModel.Description.MetadataExporter.PolicyVersion%2A> 屬性 \(Property\)，並且根據指定的原則版本，以正確命名空間匯出巢狀原則運算式及原則架構屬性 \(Attribute\)。  
  
 若要匯入自訂原則判斷提示，請參閱 <xref:System.ServiceModel.Description.IPolicyImportExtension?displayProperty=fullName> 及 [HOW TO：匯入自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)。  
  
### 若要匯出自訂原則判斷提示  
  
1.  實作 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> 上的 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> 介面。下列程式碼範例顯示繫結層級之自訂原則判斷提示的實作。  
  
     [!code-csharp[CustomPolicySample#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/custompolicysample/cs/policyexporter.cs#14)]
     [!code-vb[CustomPolicySample#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/custompolicysample/vb/policyexporter.vb#14)]  
  
2.  以程式設計的方式或使用應用程式組態檔將繫結項目插入端點繫結。請參閱下列程序。  
  
### 若要使用應用程式組態檔插入繫結項目  
  
1.  針對您的自訂原則判斷提示繫結項目實作 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement?displayProperty=fullName>。  
  
2.  使用 [\<bindingElementExtensions\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md) 項目新增繫結項目擴充至組態檔。  
  
3.  使用 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName> 建置自訂繫結。  
  
### 以程式設計的方式插入繫結項目  
  
1.  建立新的 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName> 並將它新增至 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>。  
  
2.  將步驟 1 中的自訂繫結加入至新服務端點並呼叫 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法，以將新服務端點加入至 <xref:System.ServiceModel.ServiceHost?displayProperty=fullName>。  
  
3.  開啟 <xref:System.ServiceModel.ServiceHost>。下列程式碼範例顯示自訂繫結的建立，以及使用程式設計方式插入繫結項目。  
  
     [!code-csharp[s_imperative#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_imperative/cs/service.cs#1)]
     [!code-vb[s_imperative#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_imperative/vb/service.vb#1)]  
  
## 請參閱  
 <xref:System.ServiceModel.Description.IPolicyImportExtension>   
 <xref:System.ServiceModel.Description.IPolicyExportExtension>   
 [HOW TO：匯入自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-import-custom-policy-assertions.md)