---
title: 合約優先工作流程服務開發
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: 244a6973dde9aba860b08177a42a2ecd64f3479c
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380197"
---
# <a name="contract-first-workflow-service-development"></a>合約優先工作流程服務開發
從.NET Framework 4.5 開始，Windows Workflow Foundation (WF) 功能更好的 web 服務與合約優先工作流程開發形式中的工作流程之間的整合。 合約優先工作流程開發工具可讓您在 Code First 中設計合約。 此工具會自動在合約中的作業工具箱內產生活動範本。 本主題提供工作流程服務概觀，說明如何將工作流程服務中的活動和屬性 (property) 對應至服務合約的屬性 (attribute)。 如需建立合約優先工作流程服務的逐步範例，請參閱[How to:建立會取用現有服務合約的工作流程服務](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)。  
  
## <a name="in-this-topic"></a>本主題內容  
  
- [將服務合約屬性對應至工作流程屬性](contract-first-workflow-service-development.md#MappingAttributes)  
  
    - [服務合約屬性](contract-first-workflow-service-development.md#ServiceContract)  
  
    - [作業合約屬性](contract-first-workflow-service-development.md#OperationContract)  
  
    - [訊息合約屬性](contract-first-workflow-service-development.md#MessageContract)  
  
    - [資料合約屬性](contract-first-workflow-service-development.md#DataContract)  
  
    - [錯誤合約屬性](contract-first-workflow-service-development.md#FaultContract)  
  
- [其他支援和實作資訊](contract-first-workflow-service-development.md#AdditionalSupport)  
  
    - [不支援的服務合約功能](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
    - [產生的設定之傳訊活動](contract-first-workflow-service-development.md#ActivityGeneration)  
  
## <a name="MappingAttributes"></a> 將服務合約屬性對應至工作流程屬性  
 下列各節中的表格會指定不同的 WCF 屬性 (attribute) 和屬性 (property)，以及其如何對應至合約優先工作流程中的傳訊活動和屬性 (property)。  
  
- [服務合約屬性](contract-first-workflow-service-development.md#ServiceContract)  
  
- [作業合約屬性](contract-first-workflow-service-development.md#OperationContract)  
  
- [訊息合約屬性](contract-first-workflow-service-development.md#MessageContract)  
  
- [資料合約屬性](contract-first-workflow-service-development.md#DataContract)  
  
- [錯誤合約屬性](contract-first-workflow-service-development.md#FaultContract)  
  
### <a name="ServiceContract"></a> 服務合約屬性  
  
|屬性名稱|支援|描述|WF 驗證|  
|-------------------|---------------|-----------------|-------------------|  
|CallbackContract|否|當合約是雙工合約時，取得或設定回呼合約的型別。|(N/A)|  
|ConfigurationName|否|取得或設定用來在應用程式組態檔中尋找服務的名稱。|(N/A)|  
|HasProtectionLevel|是|取得指出成員是否已指派保護層級的值。|Receive.ProtectionLevel 不應為 null。|  
|名稱|是|取得或設定的名稱\<連接埠類型 > 項目中 Web 服務描述語言 (WSDL)。|Receive.ServiceContractName.LocalName 應相符。|  
|命名空間|是|取得或設定的命名空間\<連接埠類型 > 項目中 Web 服務描述語言 (WSDL)。|Receive.ServiceContractName.NameSpace 應相符|  
|ProtectionLevel|是|指定合約的繫結是否必須支援 ProtectionLevel 屬性的值。|Receive.ProtectionLevel 應相符。|  
|SessionMode|否|取得或設定是否允許工作階段、不允許工作階段，或需要工作階段。|(N/A)|  
|TypeId|否|實作在衍生的類別中時，會取得此屬性的唯一識別項。 (繼承自屬性。)|(N/A)|  
  
 在此插入小節主體。  
  
### <a name="OperationContract"></a> 作業合約屬性  
  
|屬性名稱|支援|描述|WF 驗證|  
|-------------------|---------------|-----------------|-------------------|  
|動作|是|取得或設定要求訊息的 WS-Addressing 動作。|Receive.Action 應相符。|  
|AsyncPattern|否|指出作業以非同步方式開始實作\<方法名稱 > 和結束\<方法名稱 > 方法組，服務合約中的。|(N/A)|  
|HasProtectionLevel|是|取得指出此作業的訊息是否必須加密及/或簽署的值。|Receive.ProtectionLevel 不應為 null。|  
|IsInitiating|否|取得或設定值，以指出該方法是否實作可以在伺服器上初始化工作階段的作業 (若這樣的工作階段存在的話)。|(N/A)|  
|IsOneWay|是|取得或設定值，這個值會指出作業是否傳回回覆訊息。|(沒有此 Receive 的 SendReply，或者沒有此 Send 的 ReceiveReply)。|  
|IsTerminating|否|取得或設定值，這個值表示服務作業在傳送回覆訊息 (如果有的話) 之後，是否導致伺服器關閉該工作階段。|(N/A)|  
|名稱|是|取得或設定作業的名稱。|Receive.OperationName 應相符。|  
|ProtectionLevel|是|取得或設定值，此值指定某個作業的訊息是否須加密、簽署，或兩者都進行。|Receive.ProtectionLevel 應相符。|  
|ReplyAction|是|取得或設定作業之回覆訊息的 SOAP 動作值。|SendReply.Action 應相符。|  
|TypeId|否|實作在衍生的類別中時，會取得此屬性的唯一識別項。 (繼承自屬性。)|(N/A)|  
  
### <a name="MessageContract"></a> 訊息合約屬性  
  
|屬性名稱|支援|描述|WF 驗證|  
|-------------------|---------------|-----------------|-------------------|  
|HasProtectionLevel|是|取得值，這個值表示訊息是否擁有保護層級。|無驗證 (Receive.Content 和 SendReply.Content 必須符合訊息合約類型)。|  
|IsWrapped|是|取得或設定值，這個值會指定訊息本文是否有包裝函式項目。|無驗證 (Receive.Content 和 SendReply.Content 必須符合訊息合約類型)。|  
|ProtectionLevel|否|取得或設定值，這個值已指定訊息是否須經過加密、簽署，或兩者都進行。|(N/A)|  
|TypeId|是|實作在衍生的類別中時，會取得此屬性的唯一識別項。 (繼承自屬性。)|無驗證 (Receive.Content 和 SendReply.Content 必須符合訊息合約類型)。|  
|WrapperName|是|取得或設定訊息本文中包裝函式項目的名稱。|無驗證 (Receive.Content 和 SendReply.Content 必須符合訊息合約類型)。|  
|WrapperNamespace|否|取得或設定訊息本文包裝函式項目的命名空間。|(N/A)|  
  
### <a name="DataContract"></a> 資料合約屬性  
  
|屬性名稱|支援|描述|WF 驗證|  
|-------------------|---------------|-----------------|-------------------|  
|IsReference|否|取得或設定值，這個值表示是否要保留物件參考資料。|(N/A)|  
|名稱|是|取得或設定型別的資料合約名稱。|無驗證 (Receive.Content 和 SendReply.Content 必須符合訊息合約類型)。|  
|命名空間|是|取得或設定型別之資料合約的命名空間。|無驗證 (Receive.Content 和 SendReply.Content 必須符合訊息合約類型)。|  
|TypeId|否|實作在衍生的類別中時，會取得此屬性的唯一識別項。 (繼承自屬性。)|(N/A)|  
  
### <a name="FaultContract"></a> 錯誤合約屬性  
  
|屬性名稱|支援|描述|WF 驗證|  
|-------------------|---------------|-----------------|-------------------|  
|動作|是|取得或設定 SOAP 錯誤訊息的動作，此訊息指定為作業合約的一部分。|SendReply.Action 應相符。|  
|DetailType|是|取得包含錯誤資訊的可序列化物件型別。|SendReply.Content 應符合該類型|  
|HasProtectionLevel|否|取得指出 SOAP 錯誤訊息是否已指派保護層級的值。|(N/A)|  
|名稱|否|取得或設定 Web 服務描述語言 (WSDL) 中的錯誤訊息名稱。|(N/A)|  
|命名空間|否|取得或設定 SOAP 錯誤的命名空間。|(N/A)|  
|ProtectionLevel|否|指定 SOAP 錯誤從繫結要求的保護層級。|(N/A)|  
|TypeId|否|實作在衍生的類別中時，會取得此屬性的唯一識別項。 (繼承自屬性。)|(N/A)|  
  
## <a name="AdditionalSupport"></a> 其他支援和實作資訊  
  
- [不支援的服務合約功能](contract-first-workflow-service-development.md#UnsupportedFeatures)  
  
- [產生的設定之傳訊活動](contract-first-workflow-service-development.md#ActivityGeneration)  
  
### <a name="UnsupportedFeatures"></a> 不支援的服務合約功能  
  
- 在合約中不支援使用 TPL (工作平行程式庫) 工作。  
  
- 在服務合約中不支援繼承。  
  
### <a name="ActivityGeneration"></a> 產生的設定之傳訊活動  
 已將兩個公用靜態方法加入至 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動，以支援在使用合約優先工作流程服務時，產生預先設定的訊息活動。  
  
- <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>  
  
 這些方法所產生的活動應該會通過合約驗證，因此這些方法會在內部使用，以做為 <xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 驗證邏輯的一部分。 <xref:System.ServiceModel.Activities.Receive.OperationName%2A>、<xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>、<xref:System.ServiceModel.Activities.Receive.Action%2A>、<xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>、<xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> 和 <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> 全都已預先設定，以符合匯入的合約。 在工作流程設計工具中的活動的內容屬性 頁面**訊息**或是**參數**區段也已預先設定以符合合約。  
  
 WCF 錯誤合約也都由傳回一組個別的設定<xref:System.ServiceModel.Activities.SendReply>出現在錯誤的每個活動<xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>。  
  
 其他組件的<xref:System.ServiceModel.Description.OperationDescription>，不支援的 WF 目前服務 （例如 WebGet/WebInvoke 行為或自訂作業行為），API 將會忽略這些值的產生和組態的一部分。 不會擲回任何例外狀況。
