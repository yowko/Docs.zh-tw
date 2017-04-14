---
title: "從服務中繼資料產生 WCF 用戶端 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# 從服務中繼資料產生 WCF 用戶端
本主題說明如何使用 Svcutil.exe 中不同的參數，從中繼資料文件中產生用戶端。  
  
 中繼資料文件可以位於永久性儲存裝置上或在線上擷取。線上擷取會遵循 WS\-MetadataExchange 通訊協定或 Microsoft Discovery \(DISCO\) 通訊協定。Svcutil.exe 會同時發出以下中繼資料要求，以擷取中繼資料：  
  
-   對所提供位址的 WS\-MetadataExchange \(MEX\) 要求。  
  
-   對附加 `/mex` 之所提供位址的 MEX 要求。  
  
-   對所提供位址的 DISCO 要求 \(使用 ASP.NET Web 服務中的 [DiscoveryClientProtocol](http://go.microsoft.com/fwlink/?LinkId=94777) \(本頁面可能為英文\)\)。  
  
 Svcutil.exe 會根據 Web 服務描述語言 \(WSDL\) 或從服務收到的原則檔產生用戶端。使用者主要名稱 \(UPN\) 是串連包含 "@" 的使用者名稱，並新增完整網域名稱 \(FQDN\) 所產生的。但是，對於在 Active Directory 上註冊的使用者而言，這個格式無效，且此工具產生的 UPN 會造成 Kerberos 驗證失敗，並顯示下列錯誤訊息： \[**登入嘗試失敗**\]。若要解決這個問題，請手動修復由此工具產生的用戶端檔案。  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## 參照與共用型別  
  
|選項|說明|  
|--------|--------|  
|**\/reference:\<file path\>**|參考指定組件中的型別。產生用戶端時，使用這個選項即可指定組件，這些組件可能包含代表匯入之中繼資料的類型。<br /><br /> 簡短形式：`/r`|  
|**\/excludeType:\<type\>**|指定要從參考的合約類型排除的完整型別名稱或組件限定型別名稱。<br /><br /> 簡短形式：`/et`|  
  
## 選擇序列化程式  
  
|選項|說明|  
|--------|--------|  
|**\/serializer:Auto**|自動選取序列化程式。這會使用 `DataContract` 序列化程式。如果這個作業失敗，則使用 `XmlSerializer`。<br /><br /> 簡短形式：`/ser:Auto`|  
|**\/serializer:DataContractSerializer**|產生使用 `DataContract` 序列化程式以進行序列化與還原序列化的資料型別。<br /><br /> 簡短形式：`/ser:DataContractSerializer`|  
|**\/serializer:XmlSerializer**|產生使用 `XmlSerializer` 以進行序列化與還原序列化的資料型別。<br /><br /> 簡短形式：`/ser:XmlSerializer`|  
|**\/importXmlTypes**|設定 `DataContract` 序列化程式將非 `DataContract` 型別匯入為 `IXmlSerializable` 型別。<br /><br /> 簡短形式：`/ixt`|  
|**\/dataContractOnly**|只產生 `DataContract` 型別的程式碼。會產生 `ServiceContract` 型別。<br /><br /> 這個選項應該只能指定本機中繼資料檔案。<br /><br /> 簡短形式：`/dconly`|  
  
## 選擇用戶端語言  
  
|選項|說明|  
|--------|--------|  
|**\/language:\<language\>**|指定要用於產生程式碼的程式語言。請提供在 Machine.config 檔案中註冊的語言名稱，或繼承自 <xref:System.CodeDom.Compiler.CodeDomProvider> 之類別的完整名稱。<br /><br /> 值：c\#、cs、csharp、vb、vbs、visualbasic、vbscript、javascript、c\+\+、mc、cpp<br /><br /> 預設：csharp<br /><br /> 簡短形式：`/l`<br /><br /> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [CodeDomProvider 類別](http://go.microsoft.com/fwlink/?LinkId=94778) \(本頁面可能為英文\)。|  
  
## 選擇用戶端命名空間  
  
|選項|說明|  
|--------|--------|  
|**\/namespace:\<string,string\>**|指定從 WSDL 或 XML 結構描述 `targetNamespace` 到 Common Language Runtime \(CLR\) 命名空間的對應。使用萬用字元 \(\*\) 做為 `targetNamespace` 會對應至所有的 `targetNamespaces`，而不會明確對應至該 CLR 命名空間。<br /><br /> 為了確保訊息合約名稱不會與作業名稱衝突，您應該以雙冒號 \(`::`\) 來限定型別參照，或確定名稱為唯一。<br /><br /> 預設：衍生自 `DataContracts` 的結構描述文件之目標命名空間。預設命名空間用於所有其他產生的型別。<br /><br /> 簡短形式：`/n`|  
  
## 選擇資料繫結  
  
|選項|說明|  
|--------|--------|  
|**\/enableDataBinding**|在所有 `DataContract` 型別上實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，以啟用資料繫結。<br /><br /> 簡短形式：`/edb`|  
  
## 產生組態  
  
|選項|說明|  
|--------|--------|  
|**\/config:\<configFile\>**|針對產生的組態檔指定檔案名稱。<br /><br /> 預設：output.config|  
|**\/mergeConfig**|將產生的組態合併至現有檔案，而非覆寫現有檔案。|  
|**\/noConfig**|不要產生組態檔。|  
  
## 請參閱  
 [使用中繼資料](../../../../docs/framework/wcf/feature-details/using-metadata.md)   
 [中繼資料架構概觀](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)