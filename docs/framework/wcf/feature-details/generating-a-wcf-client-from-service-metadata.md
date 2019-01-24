---
title: 從服務中繼資料產生 WCF 用戶端
ms.date: 03/30/2017
ms.assetid: 27f8f545-cc44-412a-b104-617e0781b803
ms.openlocfilehash: 3bdb283e461076ffd5c1e77963933de0e5b4bb02
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570953"
---
# <a name="generating-a-wcf-client-from-service-metadata"></a>從服務中繼資料產生 WCF 用戶端
本主題說明如何使用 Svcutil.exe 中不同的參數，從中繼資料文件中產生用戶端。  
  
 中繼資料文件可以位於永久性儲存裝置上或在線上擷取。 線上擷取會遵循 WS-MetadataExchange 通訊協定或 Microsoft Discovery (DISCO) 通訊協定。 Svcutil.exe 會同時發出以下中繼資料要求，以擷取中繼資料：  
  
-   對所提供位址的 WS-MetadataExchange (MEX) 要求。  
  
-   對附加 `/mex` 之所提供位址的 MEX 要求。  
  
-   DISCO 要求 (使用[DiscoveryClientProtocol](https://go.microsoft.com/fwlink/?LinkId=94777)從 ASP.NET Web 服務) 所提供的位址。  
  
 Svcutil.exe 會根據 Web 服務描述語言 (WSDL) 或從服務收到的原則檔產生用戶端。 使用者主體名稱 (UPN) 藉由串連使用者名稱與產生 「\@"，然後再新增一個完整網域名稱 (FQDN)。 不過，在 Active Directory 上註冊的使用者，這種格式無效，此工具會產生的 UPN 會造成 Kerberos 驗證，並出現下列錯誤訊息中的失敗：**登入嘗試失敗。** 若要解決這個問題，請手動修復由此工具產生的用戶端檔案。  
  
```  
svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>  
```  
  
## <a name="referencing-and-sharing-types"></a>參照與共用型別  
  
|選項|描述|  
|------------|-----------------|  
|**/reference:\<檔案路徑 >**|參考指定組件中的型別。 產生用戶端時，使用這個選項即可指定組件，這些組件可能包含代表匯入之中繼資料的類型。<br /><br /> 簡短形式：`/r`|  
|**/excludeType:\<type>**|指定要從參考的合約類型排除的完整型別名稱或組件限定型別名稱。<br /><br /> 簡短形式：`/et`|  
  
## <a name="choosing-a-serializer"></a>選擇序列化程式  
  
|選項|描述|  
|------------|-----------------|  
|**/serializer:Auto**|自動選取序列化程式。 這會使用 `DataContract` 序列化程式。 如果這個作業失敗，則使用 `XmlSerializer`。<br /><br /> 簡短形式：`/ser:Auto`|  
|**/serializer:DataContractSerializer**|產生使用 `DataContract` 序列化程式以進行序列化與還原序列化的資料型別。<br /><br /> 簡短形式：`/ser:DataContractSerializer`|  
|**/serializer:XmlSerializer**|產生使用 `XmlSerializer` 以進行序列化與還原序列化的資料型別。<br /><br /> 簡短形式：`/ser:XmlSerializer`|  
|**/importXmlTypes**|設定 `DataContract` 序列化程式將非 `DataContract` 型別匯入為 `IXmlSerializable` 型別。<br /><br /> 簡短形式：`/ixt`|  
|**/dataContractOnly**|只產生 `DataContract` 型別的程式碼。 會產生 `ServiceContract` 型別。<br /><br /> 這個選項應該只能指定本機中繼資料檔案。<br /><br /> 簡短形式：`/dconly`|  
  
## <a name="choosing-a-language-for-the-client"></a>選擇用戶端語言  
  
|選項|描述|  
|------------|-----------------|  
|**/language:\<language>**|指定要用於產生程式碼的程式語言。 請提供在 Machine.config 檔案中註冊的語言名稱，或繼承自 <xref:System.CodeDom.Compiler.CodeDomProvider> 之類別的完整名稱。<br /><br /> 值：c#、cs、csharp、vb、vbs、visualbasic、vbscript、javascript、c++、mc、cpp<br /><br /> 預設：csharp<br /><br /> 簡短形式：`/l`<br /><br /> 如需詳細資訊，請參閱 < [CodeDomProvider 類別](https://go.microsoft.com/fwlink/?LinkId=94778)。|  
  
## <a name="choosing-a-namespace-for-the-client"></a>選擇用戶端命名空間  
  
|選項|描述|  
|------------|-----------------|  
|**/namespace:\<string,string>**|指定從 WSDL 或 XML 結構描述 `targetNamespace` 到 Common Language Runtime (CLR) 命名空間的對應。 使用萬用字元 (*) 做為 `targetNamespace` 會對應至所有的 `targetNamespaces`，而不會明確對應至該 CLR 命名空間。<br /><br /> 為了確保訊息合約名稱不會與作業名稱衝突，您應該以雙冒號 (`::`) 來限定型別參照，或確定名稱為唯一。<br /><br /> 預設：衍生自結構描述文件的目標命名空間`DataContracts`。 預設命名空間用於所有其他產生的型別。<br /><br /> 簡短形式：`/n`|  
  
## <a name="choosing-a-data-binding"></a>選擇資料繫結  
  
|選項|描述|  
|------------|-----------------|  
|**/enableDataBinding**|在所有 <xref:System.ComponentModel.INotifyPropertyChanged> 型別上實作 `DataContract` 介面，以啟用資料繫結。<br /><br /> 簡短形式：`/edb`|  
  
## <a name="generating-configuration"></a>產生組態  
  
|選項|描述|  
|------------|-----------------|  
|**/config:\<configFile >**|針對產生的組態檔指定檔案名稱。<br /><br /> 預設：output.config|  
|**/mergeConfig**|將產生的組態合併至現有檔案，而非覆寫現有檔案。|  
|**/noConfig**|不要產生組態檔。|  
  
## <a name="see-also"></a>另請參閱
- [使用中繼資料](../../../../docs/framework/wcf/feature-details/using-metadata.md)
- [中繼資料架構概觀](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)
