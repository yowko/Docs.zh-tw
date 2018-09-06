---
title: ServiceModel 中繼資料公用程式工具 (Svcutil.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], building
- endpoints [WCF]
- Svcutil.exe
- clients [WCF], consuming services
ms.assetid: 1abf3d9f-b420-46f1-b628-df238751f308
ms.openlocfilehash: 4c47013ebc84c6006d65a89e57217ce1c720b45a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802518"
---
# <a name="servicemodel-metadata-utility-tool-svcutilexe"></a>ServiceModel 中繼資料公用程式工具 (Svcutil.exe)

ServiceModel Metadata Utility 工具用來從中繼資料文件，並從服務模型程式碼的中繼資料文件產生服務模型程式碼。

## <a name="svcutilexe"></a>SvcUtil.exe

ServiceModel Metadata Utility Tool 位於 Windows SDK 安裝位置，特別 *%ProgramFiles%\Microsoft SDKs\Windows\v6.0\Bin*。

### <a name="functionalities"></a>功能

下表摘要說明這項工具，以及對應的主題討論如何使用它所提供的各種功能：

|工作|主題|
|----------|-----------|
|從執行中服務或靜態中繼資料文件產生程式碼。|[從服務中繼資料產生 WCF 用戶端](../../../docs/framework/wcf/feature-details/generating-a-wcf-client-from-service-metadata.md)|
|從編譯的程式碼匯出中繼資料文件。|[如何：使用 Svcutil.exe 來匯出已編譯服務程式碼的中繼資料](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-export-metadata-from-compiled-service-code.md)|
|驗證編譯的服務程式碼。|[如何：使用 Svcutil.exe 來驗證已編譯服務程式碼](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)|
|從執行中服務下載中繼資料文件。|[如何：使用 Svcutil.exe 來下載中繼資料文件](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)|
|產生序列化程式碼。|[如何：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)|

> [!CAUTION]
> 如果提供作為參數的名稱相同，Svcutil 會覆寫磁碟上的現有檔案。 這可能包括程式碼檔案、 設定或中繼資料檔案。 為了在產生程式碼和組態檔時避免這種情況，請使用 `/mergeConfig` 參數。
>
> 颾魤 ㄛ`/r`和`/ct`的參考型別參數可用於產生資料合約。 使用 XmlSerializer 時，這些參數不會運作。

### <a name="timeout"></a>等候逾時

擷取中繼資料時，此工具會有五分鐘的逾時。 這個逾時只適用於在網路上擷取中繼資料， 不適用於該中繼資料的任何處理。

### <a name="multi-targetting"></a>多目標

這個工具不支援多目標。 如果您想要產生從.NET 4 成品*svcutil.exe*，使用*svcutil.exe*從.NET 4 SDK。 若要產生 .NET 3.5 成品，請使用 .NET 3.5 SDK 中的可執行檔。

### <a name="accessing-wsdl-documents"></a>存取 WSDL 文件

使用 Svcutil 存取參考安全性權杖服務 (STS) 的 WSDL 文件時，Svcutil 會對 STS 進行 WS-MetadataExchange 呼叫。 不過，服務可以使用 WS-MetadataExchange 或 HTTP GET 來公開 WSDL 文件。 因此，如果 STS 使用 HTTP GET 只公開 WSDL 文件時，寫入 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] 中的用戶端將失敗。 撰寫的用戶端的[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]，Svcutil 會嘗試使用 Ws-metadataexchange 和 HTTP GET 取得 STS WSDL。

## <a name="using-svcutilexe"></a>使用 SvcUtil.exe

### <a name="common-usages"></a>常見使用方式

下表顯示一些常用選項這項工具：

|選項|描述|
|------------|-----------------|
|/ 目錄：\<目錄 >|要建立檔案的目錄。<br /><br /> 預設：目前的目錄。<br /><br /> 簡短形式：`/d`|
|/help|顯示工具的命令語法和選項。<br /><br /> 簡短形式：`/?`|
|/noLogo|隱藏版權和橫幅訊息。|
|/svcutilConfig:\<configFile>|指定要取代 App.config 檔所使用的自訂組態檔。 指定的組態檔可用來註冊 system.serviceModel 副檔名，而不會變更工具的組態檔。|
|/target:\<輸出類型 >|指定要由工具產生的輸出。<br /><br /> 有效值為 code、metadata 或 xmlSerializer。<br /><br /> 簡短形式：`/t`|

### <a name="code-generation"></a>程式碼產生

Svcutil.exe 可從中繼資料文件產生服務合約、用戶端和資料型別的程式碼。 這些中繼資料文件可在永久性儲存裝置或線上擷取。 線上擷取會遵循 WS-Metadata Exchange 通訊協定或 DISCO 通訊協定 (如需詳細資訊，請參閱「中繼資料下載」一節)。

您可以使用*SvcUtil.exe*工具，以產生根據預先定義的 WSDL 文件的服務與資料合約。 使用 /serviceContract 參數，並指定可以下載或找到 WSDL 文件的 URL 或檔案位置。 這會產生 WSDL 文件，然後可以用來實作投訴服務中定義的服務和資料合約。 如需詳細資訊，請參閱 <<c0> [ 如何： 擷取中繼資料並實作相容服務](../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)。

含 BasicHttpContextbinding 端點，服務*Svcutil.exe*會產生 BasicHttpBinding，其`allowCookies`屬性設為`true`改。 Cookie 用於伺服器上的內容。 如果您要在服務使用 Cookie 時管理用戶端上的內容，您可以手動修改組態以使用內容繫結。

> [!CAUTION]
> Svcutil.exe 會根據 WSDL 或從服務收到的原則檔產生用戶端。 使用者主體名稱 (UPN) 藉由串連使用者名稱，產生 「\@"和完整網域名稱 (FQDN)。 但是，對於在 Active Directory 上登錄的使用者而言，這個格式無效，且此工具產生的 UPN 會造成 Kerberos 驗證失敗，並顯示「登入嘗試失敗」錯誤訊息。 若要解決這個問題，您應手動修復由這個工具產生的用戶端檔案。

`svcutil.exe [/t:code]  <metadataDocumentPath>* | <url>* | <epr>`

|引數|描述|
|--------------|-----------------|
|`epr`|XML 檔案的路徑，其中包含支援 WS-Metadata Exchange 之服務端點的 WS-Addressing EndpointReference。 如需詳細資訊，請參閱「中繼資料下載」一節。|
|`metadataDocumentPath`|中繼資料文件的路徑 (*wsdl*或是*xsd*)，其中包含要匯入程式碼 （.wsdl、.xsd、.wspolicy 或.wsmex） 的合約。<br /><br /> 如果您指定的是中繼資料的遠端 URL，Svcutil 會根據您的指定執行匯入並包含其中的內容。 但是，如果您要處理本機檔案系統上的中繼資料檔，則必須在這個引數中指定所有檔案。 如此一來，您就可以在無法取得網路相依性的建置環境中使用 Svcutil。 您可以使用萬用字元 (*.xsd， \*.wsdl) 這個引數。|
|`url`|提供中繼資料之服務端點的 URL，或裝載於線上之中繼資料文件的 URL。 如需如何擷取這些文件的詳細資訊，請參閱「中繼資料下載」一節。|

|選項|描述|
|------------|-----------------|
|/async|同時產生同步與非同步方法簽章。<br /><br /> 預設：只產生同步方法簽章。<br /><br /> 簡短形式：`/a`|
|/collectionType:\<type>|指定 WCF 用戶端的清單集合類型。<br/><br /> 預設值： 集合型別為 System.Array。 <br /><br /> 簡短形式：`/ct`|
|/config:\<configFile >|指定產生之組態檔的檔案名稱。<br /><br /> 預設：output.config|
|/dataContractOnly|只產生資料合約類型的程式碼。 不會產生「服務合約」類型。<br /><br /> 這個選項應該只能指定本機中繼資料檔案。<br /><br /> 簡短形式：`/dconly`|
|/enableDataBinding|在所有「資料合約」類型上實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面，以啟用資料繫結。<br /><br /> 簡短形式：`/edb`|
|/excludeType:\<type>|指定要從參考的合約類型排除的完整型別名稱或組件限定型別名稱。<br /><br /> 將這個參數與個別 DLL 的 `/r` 一起使用時，會參考 XSD 類別的完整名稱。<br /><br /> 簡短形式：`/et`|
|/importXmlTypes|設定資料合約序列化程式，將非資料合約類型匯入為 IXmlSerializable 類型。|
|/internal|產生標示為內部的類別。 預設：只產生公用類別。<br /><br /> 簡短形式：`/i`|
|/language:\<語言 >|指定要用於產生程式碼的程式語言。 您應該提供註冊在 Machine.config 檔案中的語言名稱或完整的名稱的類別繼承自<xref:System.CodeDom.Compiler.CodeDomProvider>。<br /><br /> 值：c#、cs、csharp、vb、visualbasic、c++、cpp<br /><br /> 預設：csharp<br /><br /> 簡短形式：`/l`|
|/mergeConfig|將產生的組態合併至現有檔案，而非覆寫現有檔案。|
|/messageContract|產生「訊息合約」類型。<br /><br /> 簡短形式：`/mc`|
|/namespace:\<字串，字串 >|指定從 WSDL 或 XML 結構描述 targetNamespace 到 CLR 命名空間的對應。 使用 '\*' 的目標命名空間對應至該 CLR 命名空間的所有的 Targetnamespace，而不明確的對應。<br /><br /> 為了確保訊息合約名稱不會與作業名稱衝突，您應該以 `::` 限定型別參考，或確定是唯一的名稱。<br /><br /> 預設：自資料合約的結構描述文件之目標命名空間衍生而來。 預設命名空間用於所有其他產生的型別。<br /><br /> 簡短形式： `/n` **附註：** 產生時要使用以 XmlSerializer 類型，支援單一命名空間對應。 所有產生的型別會在預設的命名空間或所指定的命名空間是 ' *'。|
|/noConfig|不要產生組態檔。|
|/noStdLib|不引用標準程式庫。<br /><br /> 預設：引用 Mscorlib.dll 和 System.servicemodel.dll。|
|/out:\<檔案 >|指定產生之程式碼的檔案名稱。<br /><br /> 預設：衍生自 WSDL 定義名稱、WSDL 服務名稱，或其中一個結構描述的目標命名空間。<br /><br /> 簡短形式：`/o`|
|/reference:\<檔案路徑 >|參考指定組件中的型別。 產生用戶端時，使用這個選項即可指定組件，這些組件可能包含代表匯入之中繼資料的類型。<br /><br /> 您無法使用這個參數指定訊息合約和 <xref:System.Xml.Serialization.XmlSerializer> 型別。<br /><br /> 如果已參考 <xref:System.DateTimeOffset>，則會使用這個型別，而不會產生新型別。 如果應用程式是使用 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] 撰寫的，則 SvcUtil.exe 會自動參考 <xref:System.DateTimeOffset>。<br /><br /> 簡短形式：`/r`|
|/serializable|產生已使用 Serializable 屬性標示的類別。<br /><br /> 簡短形式：`/s`|
|/serviceContract|只產生服務合約的程式碼。 不會產生用戶端類別和組態<br /><br /> 簡短形式：`/sc`|
|/serializer:Auto|自動選取序列化程式。 這會嘗試使用資料合約序列化程式，並使用 XmlSerializer，如果失敗。<br /><br /> 簡短形式：`/ser`|
|/serializer:DataContractSerializer|產生使用「資料合約序列化程式」以進行序列化與還原序列化的資料型別。<br /><br /> 簡短形式：`/ser:DataContractSerializer`|
|/serializer:XmlSerializer|產生使用 <xref:System.Xml.Serialization.XmlSerializer> 以進行序列化與還原序列化的資料型別。<br /><br /> 簡短形式：`/ser:XmlSerializer`|
|/targetClientVersion|指定設為應用程式目標的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本。 有效值為 `Version30` 和 `Version35`。 預設值是 `Version30`。<br /><br /> 簡短形式：`/tcv`<br /><br /> `Version30`：如果您正在為使用 `/tcv:Version30` 的用戶端產生程式碼，則使用 [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]。<br /><br /> `Version35`：如果您正在為使用 `/tcv:Version35` 的用戶端產生程式碼，則使用 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]。 將 `/tcv:Version35` 與 `/async` 參數一起使用時，會產生事件架構與回呼/委派架構的非同步方法。 此外，也會啟用具備 LINQ 功能的資料集和 <xref:System.DateTimeOffset> 的支援。|
|/wrapped|控制是否將特殊大小寫搭配 wrapped 參數用於文件常值樣式的文件。 使用 **/ 包裝**參數搭配[Service Model Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具來指定一般大小寫。|

> [!NOTE]
> 當服務繫結是其中一個系統提供的繫結 (請參閱[System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md))，而<xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A>屬性會設為`None`或`Sign`，Svcutil 會產生組態檔中使用[ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)元素而不是預期的系統提供項目。 例如，如果服務使用 `<wsHttpBinding>` 項目，其中 `ProtectionLevel` 設為 `Sign`，則產生的組態會在繫結區段中有 `<customBinding>`，而非 `<wsHttpBinding>`。 如需保護層級的詳細資訊，請參閱[了解保護層級](../../../docs/framework/wcf/understanding-protection-level.md)。

### <a name="metadata-export"></a>中繼資料匯出

Svcutil.exe 可匯出服務中繼資料、合約以及編譯組件中的資料型別。 若要匯出服務的中繼資料，您必須使用 `/serviceName` 選項指定要匯出的服務。 若要匯出組件內的所有資料合約類型，請使用 `/dataContractOnly` 選項。 根據預設，會匯出輸入組件中所有服務合約的中繼資料。

`svcutil.exe [/t:metadata] [/serviceName:<serviceConfigName>] [/dataContractOnly] <assemblyPath>*`

|引數|描述|
|--------------|-----------------|
|`assemblyPath`|指定包含要匯出之服務、合約或資料合約類型的組件路徑。 標準命令列萬用字元可用於提供多個檔案做為輸入。|

|選項|描述|
|------------|-----------------|
|/serviceName:\<serviceConfigName>|指定要匯出的服務其組態名稱。 如果使用這個選項，必須將可執行的組件和相關聯的組態檔當做輸入傳遞。 Svcutil.exe 會搜尋所有相關聯組態檔中的服務組態。 如果組態檔包含任何延伸型別，則包含這些型別的組件必須在 GAC 中或使用 `/reference` 選項明確地提供。|
|/reference:\<檔案路徑 >|將指定的組件新增至用於解析型別參考的組件集合中。 如果您正在匯出或驗證的服務使用的是註冊於組態中的協力廠商擴充功能 (Behavior、Binding 和 BindingElement)，請使用這個選項找出不在 GAC 中的擴充功能組件。<br /><br /> 簡短形式：`/r`|
|/dataContractOnly|只在資料合約類型上操作。 不處理服務合約。<br /><br /> 這個選項應該只能指定本機中繼資料檔案。<br /><br /> 簡短形式：`/dconly`|
|/excludeType:\<type>|指定要從匯出作業排除的型別其完整名稱或組件限定名稱。 在匯出服務中繼資料或是一組服務合約時，如果要從匯出作業排出某些型別，則可以使用這個選項。 這個選項無法與 `/dconly` 選項一起使用。<br /><br /> 當您有單一組件包含多個服務，且每個服務使用具有相同 XSD 名稱的不同類別時，在指定這個參數時應使用服務名稱而不是 XSD 類別名稱。<br /><br /> 不支援 XSD 或資料合約類型。<br /><br /> 簡短形式：`/et`|

### <a name="service-validation"></a>服務驗證

您可以使用驗證來偵測服務實作中的錯誤，而不需要裝載服務。 您必須使用 `/serviceName` 選項來指出您要驗證的服務。

`svcutil.exe /validate /serviceName:<serviceConfigName>  <assemblyPath>*`

|引數|描述|
|--------------|-----------------|
|`assemblyPath`|指定包含要驗證的服務類型之組件的路徑。 組件必須具有相關聯的組態檔，才能提供服務組態。 標準命令列萬用字元可用於提供多個組件。|

|選項|描述|
|------------|-----------------|
|/validate|驗證由 `/serviceName` 選項指定的服務實作。 如果使用這個選項，必須將可執行的組件和相關聯的組態檔當做輸入傳遞。<br /><br /> 簡短形式：`/v`|
|/serviceName:\<serviceConfigName>|指定要驗證的服務其組態名稱。 Svcutil.exe 會搜尋所有輸入組件其所有相關聯組態檔中的服務組態。 如果組態檔包含任何延伸型別，則包含這些型別的組件必須在 GAC 中或使用 `/reference` 選項明確地提供。|
|/reference:\<檔案路徑 >|將指定的組件新增至用於解析型別參考的組件集合中。 如果您正在匯出或驗證的服務使用的是註冊於組態中的協力廠商擴充功能 (Behavior、Binding 和 BindingElement)，請使用這個選項找出不在 GAC 中的擴充功能組件。<br /><br /> 簡短形式：`/r`|
|/dataContractOnly|只在資料合約類型上操作。 不處理服務合約。<br /><br /> 這個選項應該只能指定本機中繼資料檔案。<br /><br /> 簡短形式：`/dconly`|
|/excludeType:\<type>|指定要從驗證作業排除的型別其完整名稱或組件限定名稱。<br /><br /> 簡短形式：`/et`|

### <a name="metadata-download"></a>中繼資料下載

Svcutil.exe 可用於從執行中服務下載中繼資料，並將中繼資料儲存至本機檔案中。 若要下載中繼資料，您必須指定 `/t:metadata` 選項。 否則，會產生用戶端程式碼。 對於 HTTP 和 HTTPS URL 結構描述，Svcutil.exe 會嘗試使用 WS-Metadata Exchange 和 DISCO 擷取中繼資料。 對於所有其他的 URL 結構描述，Svcutil.exe 只使用 WS-Metadata Exchange。

Svcutil 會同時發出以下中繼資料要求，以擷取中繼資料。

- 對所提供位址的 MEX (WS-Transfer) 要求

- 對附加 /mex 之所提供位址的 MEX 要求

- 對所提供位址的 DISCO 要求 (使用 ASMX 中的 DiscoveryClientProtocol)。

根據預設，Svcutil.exe 會使用在 <xref:System.ServiceModel.Description.MetadataExchangeBindings> 類別中定義的繫結進行 MEX 要求。 若要設定用於 WS-Metadata Exchange 的繫結，您必須在使用 IMetadataExchange 合約的組態中定義用戶端端點。 這可在 Svcutil.exe 的組態檔中定義，或在使用 `/svcutilConfig` 選項所指定的另一個組態檔中定義。

`svcutil.exe /t:metadata  <url>* | <epr>`

|引數|描述|
|--------------|-----------------|
|`url`|提供中繼資料之服務端點的 URL，或裝載於線上之中繼資料文件的 URL。|
|`epr`|XML 檔案的路徑，其中包含支援 WS-Metadata Exchange 之服務端點的 WS-Addressing EndpointReference。|

### <a name="xmlserializer-type-generation"></a>XmlSerializer 型別產生

使用資料型別 (可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化) 的服務和用戶端應用程式會在執行階段針對這些資料型別產生和編譯序列化程式碼，這可能會導致啟動的效能變慢。

> [!NOTE]
> 預先產生的序列化程式碼只能用於用戶端應用程式中，而不能用於服務中。

Svcutil.exe 可從應用程式的已編譯組件產生必要的 C# 序列化程式碼，因此可改善這些應用程式的啟動效能。 如需詳細資訊，請參閱 <<c0> [ 如何： 改善啟動時間的 WCF 用戶端應用程式的使用 XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)。

> [!NOTE]
> Svcutil.exe 只會針對輸入組件中的服務合約所使用的型別產生程式碼。

`svcutil.exe /t:xmlSerializer  <assemblyPath>*`

|引數|描述|
|--------------|-----------------|
|`assemblyPath`|指定包含服務合約類型之組件的路徑。 會針對每個合約中的所有 Xml 可序列化型別產生序列化型別。|

|選項|描述|
|------------|-----------------|
|/reference:\<檔案路徑 >|將指定的組件新增至用於解析型別參考的組件集合中。<br /><br /> 簡短形式：`/r`|
|/excludeType:\<type>|指定要從匯出作業或驗證作業排除的型別其完整名稱或組件限定名稱。<br /><br /> 簡短形式：`/et`|
|/out:\<檔案 >|指定產生之程式碼的檔案名稱。 將多個組件做為工具的輸入傳遞時，會忽略這個選項。<br /><br /> 預設：衍生自組件名稱。<br /><br /> 簡短形式：`/o`|
|/UseSerializerForFaults|指定<!--zz <xref:System.Xml.XmlSerializer> -->`xref:System.Xml.XmlSerializer `應用於讀取和寫入錯誤，而非預設<xref:System.Runtime.Serialization.DataContractSerializer>。|

## <a name="examples"></a>範例

下列命令會從執行中服務或線上中繼資料文件產生用戶端程式碼。

`svcutil http://service/metadataEndpoint`

下列命令會從本機中繼資料文件產生用戶端程式碼。

`svcutil *.wsdl *.xsd /language:C#`

下列命令會使用 Visual Basic 從本機結構描述文件產生用戶端合約類型。

`svcutil /dconly *.xsd /language:VB`

下列命令會從執行中服務下載中繼資料文件。

`svcutil /t:metadata http://service/metadataEndpoint`

下列命令會在組件中產生服務合約和相關類型的中繼資料文件。

`svcutil myAssembly.dll`

下列命令會在組件中產生服務、所有相關服務合約和資料型別的中繼資料文件。

`svcutil myServiceHost.exe /serviceName:myServiceName`

下列命令會在組件中產生資料型別的中繼資料文件。

`svcutil myServiceHost.exe /dconly`

下列命令會驗證服務裝載。

`svcutil /validate /serviceName:myServiceName myServiceHost.exe`

下列命令會針對組件中任何服務合約所使用的 <xref:System.Xml.Serialization.XmlSerializer> 型別，產生序列化型別。

`svcutil /t:xmlserializer myContractLibrary.exe`

## <a name="maximum-nametable-character-count-quota"></a>最大名稱表格字元計數配額

使用 svcutil 產生服務中繼資料時，可能會出現下列訊息：

錯誤： 無法取得中繼資料從 http://localhost:8000/somesservice/mex讀取 XML 資料時已經超過最大名稱表格字元計數配額 (16384)。 名稱表格是一種資料結構，用來儲存在 XML 處理過程中所遇到的字串 - 具有不重複的項目名稱、屬性名稱及屬性值的冗長 XML 文件可能會觸發此配額限制。 在建立 XML 讀取器時變更 XmlDictionaryReaderQuotas 物件上使用的 MaxNameTableCharCount 屬性，便可以增加此配額。

這個錯誤可能是當您要求服務的中繼資料時，傳回大型 WSDL 檔案的服務所導致。 這時候的問題是已超過 svcutil.exe 工具的字元配額。 設定此值是為了防止阻斷服務 (DOS) 攻擊。 可對 svcutil 指定下列組態檔，增加此配額。

下列組態檔顯示如何設定 svcutil 的讀取器配額。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <system.serviceModel>
        <bindings>
            <customBinding>
                <binding name="MyBinding">
                    <textMessageEncoding>
                        <readerQuotas maxDepth="2147483647" maxStringContentLength="2147483647"
                            maxArrayLength="2147483647" maxBytesPerRead="2147483647" maxNameTableCharCount="2147483647" />
                    </textMessageEncoding>
                    <httpTransport maxReceivedMessageSize="2147483647" maxBufferSize="2147483647" />
                </binding>
            </customBinding>
        </bindings>
        <client>
            <endpoint binding="customBinding" bindingConfiguration="MyBinding"
                contract="IMetadataExchange"
                name="http" />
        </client>
    </system.serviceModel>
</configuration>
```

建立名為 svcutil.exe.config 的新檔案，並將 XML 範例程式碼複製到此檔案。 然後將檔案放置在和 svcutil.exe 相同的目錄中。 下次 svcutil.exe 執行時便會啟用新設定。

## <a name="security-concerns"></a>安全性考量

您應該使用適當的存取控制清單 (ACL) 來保護 Svcutil.exe 的安裝資料夾、Svcutil.config 和 `/svcutilConfig` 指向的檔案。 這可以防止註冊和執行惡意的延伸。

此外，將安全性遭受危害的機會降至最低，您不應該新增不受信任的擴充功能是系統的一部分，或使用 Svcutil.exe 的未受信任的程式碼提供者。

最後，您不應該在應用程式的中介層 (Middle Tier) 使用這個工具，因為它可能會對目前處理序造成阻絕服務攻擊。

## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
