---
title: "匯出 WCF 擴充的自訂中繼資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 匯出 WCF 擴充的自訂中繼資料
在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中，中繼資料匯出是一項程序，描述服務端點並將其投射至並行標準化表示法，使得用戶端了解如何使用服務。自訂中繼資料包含系統提供之中繼資料匯出工具所無法匯出的 XML 項目。通常這包括使用者定義行為的自訂 WSDL 項目和繫結項目，以及有關繫結與合約功能和需求的原則判斷提示。  
  
 本章節將說明匯出自訂 WSDL 或原則判斷提示，但重點不會放在匯出程序本身。如需如何使用可匯出與匯入中繼資料的類型 \(不管該中繼資料為自訂或系統所建構\) 詳細資訊，請參閱[匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)。  
  
## 概觀  
 使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=fullName> 發行中繼資料時會檢查 <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=fullName>，並且會針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過系統提供的屬性和繫結所支援的所有合約和繫結，產生 XSD 和 WSDL \(包括原則判斷提示\)。不過，必須支援自訂行為屬性或繫結項目，才能將它們正確匯出。  
  
 本章節內容：  
  
1.  如何實作和使用 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=fullName> 介面，該介面會在發行 WSDL 之前先對您公開 WSDL 產生的資料。  
  
2.  如何實作和使用 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=fullName> 介面，該介面會在匯出 WSDL 資料中的原則判斷提示之前先對您公開原則資料。  
  
 如需匯入自訂 WSDL 與原則判斷提示的詳細資訊，請參閱[匯入 WCF 擴充的自訂中繼資料](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)。  
  
## 匯出自訂 WSDL 項目  
 在作業行為、合約行為、端點行為或繫結項目 \(分別為 <xref:System.ServiceModel.Description.IOperationBehavior>、<xref:System.ServiceModel.Description.IContractBehavior>、<xref:System.ServiceModel.Description.IEndpointBehavior> 或 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=fullName>\) 上實作 <xref:System.ServiceModel.Description.IWsdlExportExtension>，並且將行為或繫結項目插入您嘗試匯出的服務描述中。如需插入行為的詳細資訊，請參閱[使用行為來設定與擴充執行階段](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。<xref:System.ServiceModel.Description.IWsdlExportExtension> 會針對每個端點呼叫，而且每個端點會先匯出合約 \(如果合約尚未匯出的話\)。您可以根據需要參與任一個匯出程序：  
  
-   使用 <xref:System.ServiceModel.Description.WsdlContractConversionContext> 修改 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> 方法中匯出的中繼資料。  
  
-   使用 <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> 修改 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> 方法中匯出的端點中繼資料。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> 方法會在匯出的 <xref:System.ServiceModel.Description.ContractDescription?displayProperty=fullName> 執行個體內所有 <xref:System.ServiceModel.Description.IWsdlExportExtension> 實作上呼叫。<xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> 方法會在包含匯出的 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName> 執行個體之所有 <xref:System.ServiceModel.Description.IWsdlExportExtension> 實作上呼叫。  
  
 如需詳細資訊，請參閱 [HOW TO：匯出自訂的 WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md) 及[自訂 WSDL 發行物](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)範例。  
  
## 匯出自訂原則判斷提示  
 在 <xref:System.ServiceModel.Channels.BindingElement> 上實作 <xref:System.ServiceModel.Description.IPolicyExportExtension>，並將繫結項目加入至繫結，以便將有關繫結支援和合約功能的自訂原則判斷提示寫入 WSDL。<xref:System.ServiceModel.Description.IPolicyExportExtension> 會在匯出繫結中之實作的繫結項目時呼叫一次，並且將 <xref:System.ServiceModel.Description.PolicyConversionContext> 傳遞至 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> 方法。您可以使用 <xref:System.ServiceModel.Description.PolicyConversionContext> 執行個體的方法，加入至附加於訊息、作業或端點主體之 WSDL 繫結的原則判斷提示。  
  
 如需詳細資訊，請參閱 [HOW TO：匯出自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)。  
  
## 請參閱  
 [HOW TO：匯出自訂的 WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)   
 [HOW TO：匯出自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)   
 [匯入 WCF 擴充的自訂中繼資料](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)