---
title: "匯出 WCF 擴充的自訂中繼資料"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dbdbef495232fb1ffaeb8d1dc739c2db1355556d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>匯出 WCF 擴充的自訂中繼資料
在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中，中繼資料匯出是一項程序，描述服務端點並將其投射至並行標準化表示法，使得用戶端了解如何使用服務。 自訂中繼資料包含系統提供之中繼資料匯出工具所無法匯出的 XML 項目。 通常這包括使用者定義行為的自訂 WSDL 項目和繫結項目，以及有關繫結與合約功能和需求的原則判斷提示。  
  
 本章節將說明匯出自訂 WSDL 或原則判斷提示，但重點不會放在匯出程序本身。 如需如何使用匯出和匯入中繼資料，不論中繼資料是自訂或系統建構的類型的詳細資訊，請參閱[匯出和匯入中繼資料](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)。  
  
## <a name="overview"></a>總覽  
 使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> 發行中繼資料時會檢查 <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType>，並且會針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 透過系統提供的屬性和繫結所支援的所有合約和繫結，產生 XSD 和 WSDL (包括原則判斷提示)。 不過，必須支援自訂行為屬性或繫結項目，才能將它們正確匯出。  
  
 本章節內容：  
  
1.  如何實作和使用 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 介面，該介面會在發行 WSDL 之前先對您公開 WSDL 產生的資料。  
  
2.  如何實作和使用 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 介面，該介面會在匯出 WSDL 資料中的原則判斷提示之前先對您公開原則資料。  
  
 如需有關匯入自訂 WSDL 和原則判斷提示的詳細資訊，請參閱[WCF 延伸模組匯入自訂中繼資料](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)。  
  
## <a name="exporting-custom-wsdl-elements"></a>匯出自訂 WSDL 項目  
 在作業行為、合約行為、端點行為或繫結項目 (分別為 <xref:System.ServiceModel.Description.IWsdlExportExtension>、<xref:System.ServiceModel.Description.IOperationBehavior>、<xref:System.ServiceModel.Description.IContractBehavior> 或 <xref:System.ServiceModel.Description.IEndpointBehavior>) 上實作 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>，並且將行為或繫結項目插入您嘗試匯出的服務描述中。 (如需插入行為的詳細資訊，請參閱[設定與擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md))。 <xref:System.ServiceModel.Description.IWsdlExportExtension> 會針對每個端點呼叫，而且每個端點會先匯出合約 (如果合約尚未匯出的話)。 您可以根據需要參與任一個匯出程序：  
  
-   使用 <xref:System.ServiceModel.Description.WsdlContractConversionContext> 修改 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> 方法中匯出的中繼資料。  
  
-   使用 <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> 修改 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> 方法中匯出的端點中繼資料。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> 方法會在匯出的 <xref:System.ServiceModel.Description.IWsdlExportExtension> 執行個體內所有 <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> 實作上呼叫。  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> 方法會在包含匯出的 <xref:System.ServiceModel.Description.IWsdlExportExtension> 執行個體之所有 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 實作上呼叫。  
  
 如需詳細資訊，請參閱[How to： 匯出自訂 WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)和範例[自訂 WSDL 發行物](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)。  
  
## <a name="exporting-custom-policy-assertions"></a>匯出自訂原則判斷提示  
 在 <xref:System.ServiceModel.Description.IPolicyExportExtension><xref:System.ServiceModel.Channels.BindingElement>上實作 ，並將繫結項目加入至繫結，以便將有關繫結支援和合約功能的自訂原則判斷提示寫入 WSDL。 <xref:System.ServiceModel.Description.IPolicyExportExtension> 會在匯出繫結中之實作的繫結項目時呼叫一次，並且將 <xref:System.ServiceModel.Description.PolicyConversionContext> 傳遞至 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> 方法。 您可以使用 <xref:System.ServiceModel.Description.PolicyConversionContext> 執行個體的方法，加入至附加於訊息、作業或端點主體之 WSDL 繫結的原則判斷提示。  
  
 如需詳細資訊，請參閱[How to： 匯出自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)。  
  
## <a name="see-also"></a>請參閱  
 [如何：匯出自訂 WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [如何：匯出自訂原則判斷提示](../../../../docs/framework/wcf/extending/how-to-export-custom-policy-assertions.md)  
 [匯入 WCF 延伸模組的自訂中繼資料](../../../../docs/framework/wcf/extending/importing-custom-metadata-for-a-wcf-extension.md)
