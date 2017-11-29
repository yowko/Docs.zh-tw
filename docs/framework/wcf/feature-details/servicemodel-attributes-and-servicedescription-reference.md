---
title: "ServiceModel 屬性與 ServiceDescription 參考"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ab86b17-eab9-4846-a881-0099f9a7cc64
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ba41bd63f1dc23441cc7f265a8b1339d0b1194d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="servicemodel-attributes-and-servicedescription-reference"></a>ServiceModel 屬性與 ServiceDescription 參考
*描述樹狀目錄*是類型的階層 (從<xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType>類別)，描述服務的每個層面。 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會使用描述樹狀目錄來建置有效的服務執行階段，以發行 Web 服務描述語言 (WSDL)、XML 結構描述定義語言 (XSD)，以及用戶端可用來連接和使用服務之服務的相關原則判斷提示 (中繼資料)，並產生描述樹狀目錄值的各種程式碼和組態檔表示法。  
  
 本主題說明如何從服務合約取得與合約有關的屬性，以及如何實作這些屬性並新增到描述樹狀目錄中。 在某些情況下，屬性值會轉換成行為屬性，然後行為會插入描述樹狀目錄中。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何描述樹狀目錄值會轉換成中繼資料，請參閱[ServiceDescription 與 WSDL 參考](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)。  
  
## <a name="mapping-operations-to-the-description-tree"></a>將操作對應至描述樹狀目錄  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式中，服務合約是藉由使用屬性將介面或類別及其方法標記為操作群組的介面 (或類別) 來模組化。 開啟 <xref:System.ServiceModel.ServiceHost> 類別時，會反映任何服務合約和實作並與組態資訊合併至描述樹狀目錄中。  
  
 有兩種類型的作業模式：*參數*模型和*訊息合約*模型。 參數模型使用沒有由 <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType> 類別標記的參數或傳回值類型的 Managed 方法。 在此模型中，開發人員會控制參數和傳回值的序列化，但 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會產生用於填入服務及其合約之描述樹狀目錄的值。  
  
 在組態檔中指定的繫結會直接載入至 <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A?displayProperty=nameWithType> 屬性中。  
  
|ServiceBehaviorAttribute 屬性|受影響的描述樹狀目錄值|  
|---------------------------------------|-------------------------------------|  
|名稱|<xref:System.ServiceModel.Description.ServiceDescription.Name%2A>|  
|命名空間|<xref:System.ServiceModel.Description.ServiceDescription.Namespace%2A>|  
|ConfigurationName|<xref:System.ServiceModel.Description.ServiceDescription.ConfigurationName%2A>|  
|IgnoreExtensionDataObject|為所有的操作設定 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.IgnoreExtensionDataObject%2A> 屬性。|  
|MaxItemsInObjectGraph|為所有的操作設定 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> 屬性。|  
  
|ServiceContractAttribute 屬性|受影響的描述樹狀目錄值|  
|---------------------------------------|-------------------------------------|  
|CallbackContract|<xref:System.ServiceModel.Description.ContractDescription.CallbackContractType%2A>，<xref:System.ServiceModel.Description.MessageDescription> 加入至所有操作 <xref:System.ServiceModel.Description.OperationDescription.Messages%2A> 中。|  
|ConfigurationName|<xref:System.ServiceModel.Description.ContractDescription.ConfigurationName%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.ContractDescription.ProtectionLevel%2A> 與可能的子系保護層級。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]保護層級階層，請參閱[了解保護層級](../../../../docs/framework/wcf/understanding-protection-level.md)。|  
|SessionMode|<xref:System.ServiceModel.Description.ContractDescription.SessionMode%2A>|  
  
|ServiceKnownTypesAttribute 值|受影響的描述樹狀目錄值|  
|--------------------------------------|-------------------------------------|  
|MethodName|<xref:System.ServiceModel.Description.OperationDescription.KnownTypes%2A>|  
  
|OperationContractAttribute 值|受影響的描述樹狀目錄值|  
|--------------------------------------|-------------------------------------|  
|動作|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> 用於輸出訊息或輸入訊息，視合約/回呼合約而定。|  
|AsyncPattern|如果為 true，則為 <xref:System.ServiceModel.Description.OperationDescription.BeginMethod%2A> 和 <xref:System.ServiceModel.Description.OperationDescription.EndMethod%2A>|  
|IsOneWay|對應至 <xref:System.ServiceModel.Description.MessageDescription> 中的單一 <xref:System.ServiceModel.Description.OperationDescription.Messages%2A>。|  
|IsInitiating|<xref:System.ServiceModel.Description.OperationDescription.IsInitiating%2A>|  
|IsTerminating|<xref:System.ServiceModel.Description.OperationDescription.IsTerminating%2A>|  
|名稱|<xref:System.ServiceModel.Description.OperationDescription.Name%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.OperationDescription.ProtectionLevel%2A> 與可能的子系保護層級。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]保護層級階層，請參閱[了解保護層級](../../../../docs/framework/wcf/understanding-protection-level.md)。|  
|ReplyAction|<xref:System.ServiceModel.Description.MessageDescription.Action%2A> 用於輸出訊息或輸入訊息，視合約/回呼合約而定。|  
  
|FaultContractAttribute 值|受影響的描述樹狀目錄值|  
|----------------------------------|-------------------------------------|  
|動作|<xref:System.ServiceModel.Description.FaultDescription.Action%2A>，視合約/回呼合約而定。|  
|DetailType|<xref:System.ServiceModel.Description.FaultDescription.DetailType%2A>|  
|名稱|<xref:System.ServiceModel.Description.FaultDescription.Name%2A>|  
|命名空間|<xref:System.ServiceModel.Description.FaultDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.FaultDescription.ProtectionLevel%2A>|  
  
|DataContractFormatAttribute 值|受影響的描述樹狀目錄值|  
|---------------------------------------|-------------------------------------|  
|用法|<xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> 值是在操作的 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> 上設定。|  
  
|XmlSerializerFormatAttribute 值|受影響的描述樹狀目錄值|  
|----------------------------------------|-------------------------------------|  
|樣式|此 <xref:System.ServiceModel.XmlSerializerFormatAttribute> 屬性是在操作的 <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> 上設定。|  
|用法|<xref:System.ServiceModel.XmlSerializerFormatAttribute> 是在操作的 <xref:System.ServiceModel.Description.XmlSerializerOperationBehavior> 上設定。|  
  
|TransactionFlowAttribute 值|受影響的描述樹狀目錄值|  
|------------------------------------|-------------------------------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowAttribute> 會做為操作行為新增至 <xref:System.ServiceModel.Description.OperationDescription.Behaviors%2A> 屬性。|  
  
|MessageContractAttribute 值|受影響的描述樹狀目錄值|  
|------------------------------------|-------------------------------------|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessageDescription.ProtectionLevel%2A>|  
|WrapperName|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperName%2A>|  
|WrapperNamespace|<xref:System.ServiceModel.Description.MessageBodyDescription.WrapperNamespace%2A>|  
  
|MessageHeaderAttribute 值|受影響的描述樹狀目錄值|  
|----------------------------------|-------------------------------------|  
|行動|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A> 中對應標頭的 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A> 中對應標頭的 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|名稱|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> 中對應標頭的 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|命名空間|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> 中對應標頭的 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> 中對應標頭的 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A> 中對應標頭的 <xref:System.ServiceModel.Description.MessageDescription.Headers%2A>|  
  
|MessageBodyMemberAttribute 值|受影響的描述樹狀目錄值|  
|--------------------------------------|-------------------------------------|  
|名稱|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> 中的對應部分 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|命名空間|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A> 中的對應部分 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|順序|<xref:System.ServiceModel.Description.MessagePartDescription.Index%2A> 中的對應部分 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A> 中的對應部分 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
|MessageHeaderArrayAttribute 值|受影響的描述樹狀目錄值|  
|---------------------------------------|-------------------------------------|  
|行動|<xref:System.ServiceModel.Description.MessageHeaderDescription.Actor%2A>|  
|MustUnderstand|<xref:System.ServiceModel.Description.MessageHeaderDescription.MustUnderstand%2A>|  
|名稱|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
|命名空間|<xref:System.ServiceModel.Description.MessagePartDescription.Namespace%2A>|  
|ProtectionLevel|<xref:System.ServiceModel.Description.MessagePartDescription.ProtectionLevel%2A>|  
|Relay|<xref:System.ServiceModel.Description.MessageHeaderDescription.Relay%2A>|  
  
|MessagePropertyAttribute 值|受影響的描述樹狀目錄值|  
|------------------------------------|-------------------------------------|  
|名稱|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A>|  
  
|MessageParameterAttribute 值|受影響的描述樹狀目錄值|  
|-------------------------------------|-------------------------------------|  
|名稱|<xref:System.ServiceModel.Description.MessagePartDescription.Name%2A> 中的對應部分 <xref:System.ServiceModel.Description.MessageBodyDescription.Parts%2A>|  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何描述樹狀目錄值會轉換成中繼資料，請參閱[ServiceDescription 與 WSDL 參考](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)。  
  
## <a name="see-also"></a>另請參閱  
 [ServiceDescription 與 WSDL 參考](../../../../docs/framework/wcf/feature-details/servicedescription-and-wsdl-reference.md)
