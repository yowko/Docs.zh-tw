---
title: ServiceDescription 與 WSDL 參考
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7eadfaaae920071092f569fe2b8882875ed9497f
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="servicedescription-and-wsdl-reference"></a>ServiceDescription 與 WSDL 參考
這個主題會描述 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 如何在 <xref:System.ServiceModel.Description.ServiceDescription> 執行個體之間對應 Web 服務描述語言 (WSDL) 文件。  
  
## <a name="how-servicedescription-maps-to-wsdl-11"></a>ServiceDescription 對應至 WSDL 1.1 的方法  
 可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，對您的服務從 <xref:System.ServiceModel.Description.ServiceDescription> 執行個體中匯出 WSDL 文件。 發行中繼資料端點時，會為您的服務自動產生 WSDL 文件。  
  
 您也可以使用 <xref:System.ServiceModel.Description.ServiceEndpoint> 型別，從 WSDL 文件中匯入 <xref:System.ServiceModel.Description.ContractDescription> 執行個體、<xref:System.ServiceModel.Channels.Binding> 執行個體和 `WsdlImporter` 執行個體。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 匯出的 WSDL 文件會從外部 XML 結構描述文件中匯入使用的 XML 結構描述定義。 將會對資料型別在服務中使用的每個目標命名空間，匯出不同的 XML 結構描述文件。 同樣地，將會對服務合約使用的每個目標命名空間，匯出不同的 WSDL 文件。  
  
### <a name="servicedescription"></a>ServiceDescription  
 <xref:System.ServiceModel.Description.ServiceDescription> 執行個體會對應至 `wsdl:service` 項目。 <xref:System.ServiceModel.Description.ServiceDescription> 執行個體包含 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體集合，其中每一個都會對應至個別 `wsdl:port` 項目。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Name`|`wsdl:service` /@name服務的值。|  
|`Namespace`|服務之 `wsdl:service` 定義的 targetNamespace。|  
|`Endpoints`|服務的 `wsdl:port` 定義。|  
  
### <a name="serviceendpoint"></a>ServiceEndpoint  
 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體會對應至 `wsdl:port` 項目。 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體中包含位址、繫結和合約。  
  
 實作 <xref:System.ServiceModel.Description.IWsdlExportExtension> 介面的端點行為可以修改所附加至端點的 `wsdl:port` 項目。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Name`|`wsdl:port` /@name端點的值和`wsdl:binding`/@name端點繫結的值。|  
|`Address`|端點之 `wsdl:port` 定義的位址。<br /><br /> 端點的傳輸會決定位址的格式。 例如，針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援的傳輸，格式可以為 SOAP 位址或端點參考。|  
|`Binding`|端點的 `wsdl:binding` 定義。<br /><br /> 和 `wsdl:binding` 定義不一樣，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的繫結不會連接至任何合約。|  
|`Contract`|端點的 `wsdl:portType` 定義。|  
|`Behaviors`|實作 <xref:System.ServiceModel.Description.IWsdlExportExtension> 介面的端點行為可以修改端點的 `wsdl:port`。|  
  
### <a name="bindings"></a>繫結  
 `ServiceEndpoint` 執行個體的繫結執行個體會對應至 `wsdl:binding` 定義。 和必須與特定 `wsdl:binding` 定義相關聯的 `wsdl:portType` 定義不同，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結與任何合約都不相關。  
  
 繫結是由繫結項目集合所組成。 每個項目負責針對端點與用戶端通訊的方式稍加描述。 此外，繫結具有的 <xref:System.ServiceModel.Channels.MessageVersion> 會指出用於端點的 <xref:System.ServiceModel.EnvelopeVersion> 和 <xref:System.ServiceModel.Channels.AddressingVersion>。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Name`|用於端點的預設名稱，而這個繫結名稱會以底線區隔附加的合約名稱。|  
|`Namespace`|`targetNamespace` 定義的 `wsdl:binding`。<br /><br /> 在進行匯入時，如果將原則附加至 WSDL 連接埠，則匯入的繫結命名空間會對應至 `targetNamespace` 定義的 `wsdl:port` 中。|  
|`BindingElementCollection` 是由 `CreateBindingElements`() 方法所傳回|`wsdl:binding` 定義的各種網域特定延伸項目，一般來說是原則判斷提示 (Assertion)。|  
|`MessageVersion`|端點的 `EnvelopeVersion` 和 `AddressingVersion`。<br /><br /> 指定 `MessageVersion.None` 時，WSDL 繫結不含 SOAP 繫結，而 WSDL 連接埠則不含 WS-Addressing 內容。 這個設定通常會用於 Plain Old XML (POX) 端點。|  
  
#### <a name="bindingelements"></a>BindingElements  
 端點繫結的繫結項目會對應至 `wsdl:binding` 中的各種 WSDL 延伸項目，例如原則判斷提示。  
  
 繫結的 <xref:System.ServiceModel.Channels.TransportBindingElement> 會判斷 SOAP 繫結的傳輸統一資源識別碼 (URI)。  
  
#### <a name="addressingversion"></a>AddressingVersion  
 繫結上的 `AddressingVersion` 會對應至 `wsd:port` 中使用的定址版本。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援 SOAP 1.1 和 SOAP 1.2 位址，以及 WS-Addressing 08/2004 和 WS-Addressing 1.0 端點參考。  
  
#### <a name="envelopeversion"></a>EnvelopeVersion  
 繫結上的 `EnvelopeVersion` 會對應至 `wsdl:binding` 中使用的 SOAP 版本。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援 SOAP 1.1 和 SOAP 1.2 繫結。  
  
### <a name="contracts"></a>合約  
 <xref:System.ServiceModel.Description.ContractDescription> 執行個體的 `ServiceEndpoint` 執行個體會對應至 `wsdl:portType`。 `ContractDescription` 執行個體會描述所提供之合約的所有作業。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Name`|`wsdl:portType` /@name合約的值。|  
|`Namespace`|`wsdl:portType` 定義的 targetNamespace。|  
|`SessionMode`|`wsdl:portType` /@msc:usingSession合約的值。 這個屬性是 WSDL 1.1 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 延伸項目。|  
|`Operations`|合約的 `wsdl:operation` 定義。|  
  
### <a name="operations"></a>作業  
 <xref:System.ServiceModel.Description.OperationDescription>執行個體會對應至`wsdl:portType` / `wsdl:operation`。 `OperationDescription` 包含 `MessageDescription` 執行個體集合，而這些執行個體會描述作業的各種訊息。  
  
 有兩個作業行為會特別強調 `OperationDescription` 對應至 WSDL 文件的方法：`DataContractSerializerOperationBehavior` 和 `XmlSerializerOperationBehavior`。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` /@name該作業的值。|  
|`ProtectionLevel`|針對此作業，附加至 `wsdl:binding/wsdl:operation` 訊息之安全性原則中的保護判斷提示。|  
|`IsInitiating`|`wsdl:portType` / `wsdl:operation` /@msc:isInitiating該作業的值。 這個屬性是 WSDL 1.1 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 延伸項目。|  
|`IsTerminating`|`wsdl:portType` / `wsdl:operation` /@msc:isTerminating該作業的值。 這個屬性是 WSDL 1.1 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 延伸項目。|  
|`Messages`|`wsdl:portType` / `wsdl:operation` / `wsdl:input`和`wsdl:portType` / `wsdl:operation` / `wsdl:output`作業的訊息。|  
|`Faults`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault`作業定義。|  
|`Behaviors`|`DataContractSerializerOperationBehavior` 和 `XmlSerializerOperationBehavior` 會處理作業繫結和作業訊息。|  
  
#### <a name="the-datacontractserializeroperationbehavior"></a>DataContractSerializerOperationBehavior  
 作業的 `DataContractSerializerOperationBehavior` 是 `IWsdlExportExtension` 實作，會針對作業匯出 WSDL 訊息和繫結。 將會使用 `XsdDataContractExporter` 匯出 XML 結構描述型別。 `DataContractSerializerOperationBehavior` 也會判斷用於該作業的用法、樣式和結構描述匯出工具與匯入工具。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`DataContractFormatAttribute`|`Style`屬性，這個屬性會對應至`wsdl:binding` / `wsdl:operation` / `soap:operation` /@style該作業的值。<br /><br /> `DataContractSerializerOperationBehavior` 在 WSDL 中僅支援結構描述型別的原來用法。|  
  
#### <a name="the-xmlserializeroperationbehavior"></a>XmlSerializerOperationBehavior  
 作業的 `XmlSerializerOperationBehavior` 是 `IWsdlExportExtension` 實作，會針對作業匯出 WSDL 訊息和繫結。 將會使用 `XmlSchemaExporter` 匯出 XML 結構描述型別。 `XmlSerializerOperationBehavior` 也會判斷用於該作業的用法、樣式和結構描述匯出工具與匯入工具。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`XmlSerializerFormatAttribute`|`Style`屬性，這個屬性會對應至`wsdl:binding` / `wsdl:operation` / `soap:operation` /@style該作業的值。<br /><br /> `Use`屬性，這個屬性會對應至`wsdl:binding` / `wsdl:operation` / `soap:operation`/ */@use作業中的所有訊息的值。|  
  
### <a name="messages"></a>訊息  
 A`MessageDescription`執行個體會對應至`wsdl:message`所參考`wsdl:portType` / `wsdl:operation` / `wsdl:input`或`wsdl:portType` / `wsdl:operation` / `wsdl:output`作業中的訊息。 `MessageDescription` 中具有本文和標頭。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Action`|訊息的 SOAP 或 WS-Addressing 動作。<br /><br /> 請注意，使用動作字串 "*" 的作業不會以 WSDL 表示。|  
|`Direction`|`MessageDirection.Input` 對應至 `wsdl:input`。<br /><br /> `MessageDirection.Output` 對應至 `wsdl:output`。|  
|`ProtectionLevel`|針對此訊息，附加至 `wsdl:message` 定義之安全性原則中的保護判斷提示。|  
|`Body`|訊息的訊息本文。|  
|`Headers`|訊息的標頭。|  
|`ContractDescription.Name`, `OperationContract.Name`|在匯出時，用來衍生`wsdl:message`/@name值。|  
  
#### <a name="message-body"></a>訊息本文  
 A`MessageBodyDescription`執行個體會對應至`wsdl:message` / `wsdl:part`定義訊息的本文。 訊息本文可以為包裝或不要包裝。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`WrapperName`|如果樣式不是 RPC，則`WrapperName`所參考的項目名稱的對應`wsdl:message` / `wsdl:part`與@name設定為 「 參數 」。|  
|`WrapperNamespace`|如果樣式不是 RPC，則`WrapperNamespace`對應項目命名空間的`wsdl:message` / `wsdl:part`與@name設定為 「 參數 」。|  
|`Parts`|此訊息本文的訊息部分。|  
|`ReturnValue`|子元素的包裝函式項目是否有包裝函式項目 （文件包裝樣式或 RPC 樣式），否則第一個`wsdl:message` / `wsdl:part`訊息中。|  
  
#### <a name="message-parts"></a>訊息部分  
 A`MessagePartDescription`執行個體會對應至`wsdl:message` / `wsdl:part`和 XML 結構描述型別或訊息部分指向之項目。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Name`|`wsd:message` / `wsdl:part` /@name訊息部分及訊息部分指向之項目的名稱值。|  
|`Namespace`|訊息部分所指向之項目的命名空間。|  
|`Index`|索引`wsdl:message` / `wsdl:part`訊息。|  
|`ProtectionLevel`|針對此訊息部分，附加至 `wsdl:message` 定義之安全性原則中的保護判斷提示。 將會參數化原則以指向特定訊息部分。|  
|`MessageType`|訊息部分指向之項目的 XML 結構描述型別。|  
  
#### <a name="message-headers"></a>訊息標頭  
 `MessageHeaderDescription` 執行個體是一種訊息部分，也會對應至訊息部分的 `soap:header` 繫結。  
  
### <a name="faults"></a>錯誤  
 A`FaultDescription`執行個體會對應至`wsdl:portType` / `wsdl:operation` / `wsdl:fault`定義以及其相關聯`wsdl:message`定義。 `wsdl:message` 會新增至相同的目標命名空間，做為相關聯的 WSDL 連接埠型別。 `wsdl:message` 具有名稱為「詳細資訊」的單一訊息部分，而這個部分會指向對應至 `DefaultType` 執行個體之 `FaultDescription` 屬性值的 XML 結構描述項目。  
  
|屬性|WSDL 對應|  
|----------------|------------------|  
|`Name`|`wsdl:portType` / `wsdl:operation` / `wsdl:fault` /@name錯誤的值。|  
|`Namespace`|錯誤詳細訊息部分所指向之 XML 結構描述項目的命名空間。|  
|`Action`|錯誤的 SOAP 或 WS-Addressing 動作。|  
|`ProtectionLevel`|針對此錯誤，附加至 `wsdl:message` 定義之安全性原則中的保護判斷提示。|  
|`DetailType`|詳細訊息部分指向之項目的 XML 結構描述型別。|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|用來衍生`wsdl:message`/@name錯誤訊息的值。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Description>
