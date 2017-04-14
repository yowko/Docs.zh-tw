---
title: "ServiceDescription 與 WSDL 參考 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: eedc025d-abd9-46b1-bf3b-61d2d5c95fd6
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# ServiceDescription 與 WSDL 參考
這個主題會描述 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 如何在 <xref:System.ServiceModel.Description.ServiceDescription> 執行個體之間對應 Web 服務描述語言 \(WSDL\) 文件。  
  
## ServiceDescription 對應至 WSDL 1.1 的方法  
 可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]，對您的服務從 <xref:System.ServiceModel.Description.ServiceDescription> 執行個體中匯出 WSDL 文件。  發行中繼資料端點時，會為您的服務自動產生 WSDL 文件。  
  
 您也可以使用 `WsdlImporter` 型別，從 WSDL 文件中匯入 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體、<xref:System.ServiceModel.Description.ContractDescription> 執行個體和 <xref:System.ServiceModel.Channels.Binding> 執行個體。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 匯出的 WSDL 文件會從外部 XML 結構描述文件中匯入使用的 XML 結構描述定義。  將會對資料型別在服務中使用的每個目標命名空間，匯出不同的 XML 結構描述文件。  同樣地，將會對服務合約使用的每個目標命名空間，匯出不同的 WSDL 文件。  
  
### ServiceDescription  
 <xref:System.ServiceModel.Description.ServiceDescription> 執行個體會對應至 `wsdl:service` 項目。  <xref:System.ServiceModel.Description.ServiceDescription> 執行個體包含 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體集合，其中每一個都會對應至個別 `wsdl:port` 項目。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Name`|服務的 `wsdl:service`\/@name 值。|  
|`Namespace`|服務之 `wsdl:service` 定義的 targetNamespace。|  
|`Endpoints`|服務的 `wsdl:port` 定義。|  
  
### ServiceEndpoint  
 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體會對應至 `wsdl:port` 項目。  <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體中包含位址、繫結和合約。  
  
 實作 <xref:System.ServiceModel.Description.IWsdlExportExtension> 介面的端點行為可以修改所附加至端點的 `wsdl:port` 項目。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Name`|端點的 `wsdl:port`\/@name 值以及端點繫結的 `wsdl:binding`\/@name 值。|  
|`Address`|端點之 `wsdl:port` 定義的位址。<br /><br /> 端點的傳輸會決定位址的格式。  例如，針對 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援的傳輸，格式可以為 SOAP 位址或端點參考。|  
|`Binding`|端點的 `wsdl:binding` 定義。<br /><br /> 和 `wsdl:binding` 定義不一樣，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的繫結不會連接至任何合約。|  
|`Contract`|端點的 `wsdl:portType` 定義。|  
|`Behaviors`|實作 <xref:System.ServiceModel.Description.IWsdlExportExtension> 介面的端點行為可以修改端點的 `wsdl:port`。|  
  
### 繫結  
 `ServiceEndpoint` 執行個體的繫結執行個體會對應至 `wsdl:binding` 定義。  和必須與特定 `wsdl:portType` 定義相關聯的 `wsdl:binding` 定義不同，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結與任何合約都不相關。  
  
 繫結是由繫結項目集合所組成。  每個項目負責針對端點與用戶端通訊的方式稍加描述。  此外，繫結具有的 <xref:System.ServiceModel.Channels.MessageVersion> 會指出用於端點的 <xref:System.ServiceModel.EnvelopeVersion> 和 <xref:System.ServiceModel.Channels.AddressingVersion>。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Name`|用於端點的預設名稱，而這個繫結名稱會以底線區隔附加的合約名稱。|  
|`Namespace`|`wsdl:binding` 定義的 `targetNamespace`。<br /><br /> 在進行匯入時，如果將原則附加至 WSDL 連接埠，則匯入的繫結命名空間會對應至 `wsdl:port` 定義的 `targetNamespace` 中。|  
|`BindingElementCollection` 是由 `CreateBindingElements`\(\) 方法所傳回|`wsdl:binding` 定義的各種網域特定延伸項目，一般來說是原則判斷提示 \(Assertion\)。|  
|`MessageVersion`|端點的 `EnvelopeVersion` 和 `AddressingVersion`。<br /><br /> 指定 `MessageVersion.None` 時，WSDL 繫結不含 SOAP 繫結，而 WSDL 連接埠則不含 WS\-Addressing 內容。  這個設定通常會用於 Plain Old XML \(POX\) 端點。|  
  
#### BindingElements  
 端點繫結的繫結項目會對應至 `wsdl:binding` 中的各種 WSDL 延伸項目，例如原則判斷提示。  
  
 繫結的 <xref:System.ServiceModel.Channels.TransportBindingElement> 會判斷 SOAP 繫結的傳輸統一資源識別碼 \(URI\)。  
  
#### AddressingVersion  
 繫結上的 `AddressingVersion` 會對應至 `wsd:port` 中使用的定址版本。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援 SOAP 1.1 和 SOAP 1.2 位址，以及 WS\-Addressing 08\/2004 和 WS\-Addressing 1.0 端點參考。  
  
#### EnvelopeVersion  
 繫結上的 `EnvelopeVersion` 會對應至 `wsdl:binding` 中使用的 SOAP 版本。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 支援 SOAP 1.1 和 SOAP 1.2 繫結。  
  
### 合約  
 `ServiceEndpoint` 執行個體的 <xref:System.ServiceModel.Description.ContractDescription> 執行個體會對應至 `wsdl:portType`。  `ContractDescription` 執行個體會描述所提供之合約的所有作業。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Name`|合約的 `wsdl:portType`\/@name 值。|  
|`Namespace`|`wsdl:portType` 定義的 targetNamespace。|  
|`SessionMode`|合約的 `wsdl:portType`\/@msc:usingSession 值。  這個屬性是 WSDL 1.1 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 延伸項目。|  
|`Operations`|合約的 `wsdl:operation` 定義。|  
  
### 作業  
 <xref:System.ServiceModel.Description.OperationDescription> 執行個體會對應至 `wsdl:portType`\/`wsdl:operation`。  `OperationDescription` 包含 `MessageDescription` 執行個體集合，而這些執行個體會描述作業的各種訊息。  
  
 有兩個作業行為會特別強調 `OperationDescription` 對應至 WSDL 文件的方法：`DataContractSerializerOperationBehavior` 和 `XmlSerializerOperationBehavior`。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Name`|作業的 `wsdl:portType`\/`wsdl:operation`\/@name 值。|  
|`ProtectionLevel`|針對此作業，附加至 `wsdl:binding/wsdl:operation` 訊息之安全性原則中的保護判斷提示。|  
|`IsInitiating`|作業的 `wsdl:portType`\/`wsdl:operation`\/@msc:isInitiating 值。  這個屬性是 WSDL 1.1 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 延伸項目。|  
|`IsTerminating`|作業的 `wsdl:portType`\/`wsdl:operation`\/@msc:isTerminating 值。  這個屬性是 WSDL 1.1 的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 延伸項目。|  
|`Messages`|作業的 `wsdl:portType`\/`wsdl:operation`\/`wsdl:input` 和 `wsdl:portType`\/`wsdl:operation`\/`wsdl:output` 訊息。|  
|`Faults`|作業的 `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault` 定義。|  
|`Behaviors`|`DataContractSerializerOperationBehavior` 和 `XmlSerializerOperationBehavior` 會處理作業繫結和作業訊息。|  
  
#### DataContractSerializerOperationBehavior  
 作業的 `DataContractSerializerOperationBehavior` 是 `IWsdlExportExtension` 實作，會針對作業匯出 WSDL 訊息和繫結。  將會使用 `XsdDataContractExporter` 匯出 XML 結構描述型別。  `DataContractSerializerOperationBehavior` 也會判斷用於該作業的用法、樣式和結構描述匯出工具與匯入工具。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`DataContractFormatAttribute`|這個屬性 \(Attribute\) 的 `Style` 屬性會對應至作業的 `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/@style 值。<br /><br /> `DataContractSerializerOperationBehavior` 在 WSDL 中僅支援結構描述型別的原來用法。|  
  
#### XmlSerializerOperationBehavior  
 作業的 `XmlSerializerOperationBehavior` 是 `IWsdlExportExtension` 實作，會針對作業匯出 WSDL 訊息和繫結。  將會使用 `XmlSchemaExporter` 匯出 XML 結構描述型別。  `XmlSerializerOperationBehavior` 也會判斷用於該作業的用法、樣式和結構描述匯出工具與匯入工具。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`XmlSerializerFormatAttribute`|這個屬性 \(Attribute\) 的 `Style` 屬性會對應至作業的 `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/@style 值。<br /><br /> 這個屬性 \(Attribute\) 的 `Use` 屬性會對應至作業中所有訊息的 `wsdl:binding`\/`wsdl:operation`\/`soap:operation`\/\*\/@use 值。|  
  
### 訊息  
 `MessageDescription` 執行個體會對應至 `wsdl:message`，而這會由作業中的 `wsdl:portType`\/`wsdl:operation`\/`wsdl:input` 或 `wsdl:portType`\/`wsdl:operation`\/`wsdl:output` 訊息所參考。  `MessageDescription` 中具有本文和標頭。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Action`|訊息的 SOAP 或 WS\-Addressing 動作。<br /><br /> 請注意，使用動作字串 "\*" 的作業不會以 WSDL 表示。|  
|`Direction`|`MessageDirection.Input` 對應至 `wsdl:input`。<br /><br /> `MessageDirection.Output` 對應至 `wsdl:output`。|  
|`ProtectionLevel`|針對此訊息，附加至 `wsdl:message` 定義之安全性原則中的保護判斷提示。|  
|`Body`|訊息的訊息本文。|  
|`Headers`|訊息的標頭。|  
|`ContractDescription.Name`, `OperationContract.Name`|在匯出時，用來衍生 `wsdl:message`\/@name 值。|  
  
#### 訊息本文  
 `MessageBodyDescription` 執行個體會對應至訊息本文的 `wsdl:message`\/`wsdl:part` 定義。  訊息本文可以為包裝或不要包裝。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`WrapperName`|如果樣式不是 RPC，則 `WrapperName` 會對應至其 @name 設定為「參數」之 `wsdl:message`\/`wsdl:part` 所參考的項目名稱。|  
|`WrapperNamespace`|如果樣式不是 RPC，則 `WrapperNamespace` 會對應至其 @name 設定為「參數」之 `wsdl:message`\/`wsdl:part` 的項目命名空間。|  
|`Parts`|此訊息本文的訊息部分。|  
|`ReturnValue`|如果有包裝函式項目時則為包裝函式項目的子項目 \(文件包裝樣式或 RPC 樣式\)，否則為訊息中的第一個 `wsdl:message`\/`wsdl:part`。|  
  
#### 訊息部分  
 `MessagePartDescription` 執行個體會對應至 `wsdl:message`\/`wsdl:part` 和 XML 結構描述型別，或者訊息部分所指向的項目。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Name`|訊息部分的 `wsd:message`\/`wsdl:part`\/@name 值，以及訊息部分所指向之項目的名稱。|  
|`Namespace`|訊息部分所指向之項目的命名空間。|  
|`Index`|訊息之 `wsdl:message`\/`wsdl:part` 的索引。|  
|`ProtectionLevel`|針對此訊息部分，附加至 `wsdl:message` 定義之安全性原則中的保護判斷提示。  將會參數化原則以指向特定訊息部分。|  
|`MessageType`|訊息部分指向之項目的 XML 結構描述型別。|  
  
#### 訊息標頭  
 `MessageHeaderDescription` 執行個體是一種訊息部分，也會對應至訊息部分的 `soap:header` 繫結。  
  
### 錯誤  
 `FaultDescription` 執行個體會對應至 `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault` 定義與其相關聯的 `wsdl:message` 定義。  `wsdl:message` 會新增至相同的目標命名空間，做為相關聯的 WSDL 連接埠型別。  `wsdl:message` 具有名稱為「詳細資訊」的單一訊息部分，而這個部分會指向對應至 `FaultDescription` 執行個體之 `DefaultType` 屬性值的 XML 結構描述項目。  
  
|屬性|WSDL 對應|  
|--------|-------------|  
|`Name`|錯誤的 `wsdl:portType`\/`wsdl:operation`\/`wsdl:fault`\/@name 值。|  
|`Namespace`|錯誤詳細訊息部分所指向之 XML 結構描述項目的命名空間。|  
|`Action`|錯誤的 SOAP 或 WS\-Addressing 動作。|  
|`ProtectionLevel`|針對此錯誤，附加至 `wsdl:message` 定義之安全性原則中的保護判斷提示。|  
|`DetailType`|詳細訊息部分指向之項目的 XML 結構描述型別。|  
|`Name, ContractDescription.Name, OperationDescription.Name,`|用於衍生錯誤訊息的 `wsdl:message`\/@name 值。|  
  
## 請參閱  
 <xref:System.ServiceModel.Description>