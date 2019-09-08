---
title: 匯出 WCF 擴充的自訂中繼資料
ms.date: 03/30/2017
ms.assetid: 53c93882-f8ba-4192-965b-787b5e3f09c0
ms.openlocfilehash: 540dd9011be83d349495a0b05283b83f3d55dc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797189"
---
# <a name="exporting-custom-metadata-for-a-wcf-extension"></a>匯出 WCF 擴充的自訂中繼資料
在 Windows Communication Foundation （WCF）中，中繼資料匯出程式會描述服務端點，並將其投射至平行、標準化的標記法，以供用戶端用來瞭解如何使用服務。 自訂中繼資料包含系統提供之中繼資料匯出工具所無法匯出的 XML 項目。 通常這包括使用者定義行為的自訂 WSDL 項目和繫結程序項目，以及有關繫結程序與合約功能和需求的原則判斷提示。  
  
 本章節將說明匯出自訂 WSDL 或原則判斷提示，但重點不會放在匯出程序本身。 如需如何使用匯出和匯入中繼資料的類型（不論中繼資料是自訂或系統結構化）的詳細資訊，請參閱[匯出和匯入中繼資料](../feature-details/exporting-and-importing-metadata.md)。  
  
## <a name="overview"></a>總覽  
 使用<xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType>發行中繼資料時<xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> ，會檢查，並針對 WCF 可以使用系統提供的屬性和系結所支援的所有合約和系結，產生 XSD 和 WSDL （包括原則判斷提示）。 不過，必須支援自訂行為屬性或繫結項目，才能將它們正確匯出。  
  
 本章節內容：  
  
1. 如何實作和使用 <xref:System.ServiceModel.Description.IWsdlExportExtension?displayProperty=nameWithType> 介面，該介面會在發行 WSDL 之前先對您公開 WSDL 產生的資料。  
  
2. 如何實作和使用 <xref:System.ServiceModel.Description.IPolicyExportExtension?displayProperty=nameWithType> 介面，該介面會在匯出 WSDL 資料中的原則判斷提示之前先對您公開原則資料。  
  
 如需匯入自訂 WSDL 和原則判斷提示的詳細資訊，請參閱匯[入 WCF 延伸模組的自訂中繼資料](importing-custom-metadata-for-a-wcf-extension.md)。  
  
## <a name="exporting-custom-wsdl-elements"></a>匯出自訂 WSDL 項目  
 在作業行為、合約行為、端點行為或繫結項目 (分別為 <xref:System.ServiceModel.Description.IWsdlExportExtension>、<xref:System.ServiceModel.Description.IOperationBehavior>、<xref:System.ServiceModel.Description.IContractBehavior> 或 <xref:System.ServiceModel.Description.IEndpointBehavior>) 上實作 <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>，並且將行為或繫結項目插入您嘗試匯出的服務描述中。 （如需插入行為的詳細資訊，請參閱[使用行為設定和擴充運行](configuring-and-extending-the-runtime-with-behaviors.md)時間）。 <xref:System.ServiceModel.Description.IWsdlExportExtension> 會針對每個端點呼叫，而且每個端點會先匯出合約 (如果合約尚未匯出的話)。 您可以根據需要參與任一個匯出程序：  
  
- 使用 <xref:System.ServiceModel.Description.WsdlContractConversionContext> 修改 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> 方法中匯出的中繼資料。  
  
- 使用 <xref:System.ServiceModel.Description.WsdlEndpointConversionContext> 修改 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> 方法中匯出的端點中繼資料。  
  
 <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> 方法會在匯出的 <xref:System.ServiceModel.Description.IWsdlExportExtension> 執行個體內所有 <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> 實作上呼叫。  <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportEndpoint%2A> 方法會在包含匯出的 <xref:System.ServiceModel.Description.IWsdlExportExtension> 執行個體之所有 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 實作上呼叫。  
  
 如需詳細資訊，請參閱[如何：匯出自訂](how-to-export-custom-wsdl.md) wsdl 和範例[自訂 wsdl 發行](../samples/custom-wsdl-publication.md)集。  
  
## <a name="exporting-custom-policy-assertions"></a>匯出自訂原則判斷提示  
 在 <xref:System.ServiceModel.Description.IPolicyExportExtension><xref:System.ServiceModel.Channels.BindingElement>上實作 ，並將繫結項目加入至繫結，以便將有關繫結支援和合約功能的自訂原則判斷提示寫入 WSDL。 <xref:System.ServiceModel.Description.IPolicyExportExtension> 會在匯出繫結中之實作的繫結項目時呼叫一次，並且將 <xref:System.ServiceModel.Description.PolicyConversionContext> 傳遞至 <xref:System.ServiceModel.Description.IPolicyExportExtension.ExportPolicy%2A> 方法。 您可以使用 <xref:System.ServiceModel.Description.PolicyConversionContext> 執行個體的方法，加入至附加於訊息、作業或端點主體之 WSDL 繫結的原則判斷提示。  
  
 如需詳細資訊，請參閱[如何：匯出自訂原則](how-to-export-custom-policy-assertions.md)判斷提示。  
  
## <a name="see-also"></a>另請參閱

- [如何：匯出自訂 WSDL](how-to-export-custom-wsdl.md)
- [如何：匯出自訂原則判斷提示](how-to-export-custom-policy-assertions.md)
- [匯入 WCF 延伸模組的自訂中繼資料](importing-custom-metadata-for-a-wcf-extension.md)
