---
title: 擴充用戶端
ms.date: 03/30/2017
helpviewer_keywords:
- proxy extensions [WCF]
ms.assetid: 1328c61c-06e5-455f-9ebd-ceefb59d3867
ms.openlocfilehash: 48e6177e7098f8131d2a0fd62bda9c505fa8bcc9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662807"
---
# <a name="extending-clients"></a>擴充用戶端
在呼叫應用程式中，服務模型層會負責使用應用程式程式碼將方法引動過程轉譯到傳出訊息中、將這些訊息推送到基礎通道、將結果轉譯回應用程式程式碼中的傳回值與 out 參數，並將結果傳回到呼叫端。 服務模型延伸會修改或實作涉及用戶端或發送器功能、自訂行為、訊息與參數攔截以及其他擴充性功能的執行或通訊行為與功能。  
  
 本主題描述如何使用<xref:System.ServiceModel.Dispatcher.ClientRuntime>和<xref:System.ServiceModel.Dispatcher.ClientOperation>類別在 Windows Communication Foundation (WCF) 用戶端應用程式中修改預設的執行行為的 WCF 用戶端，或如何攔截或修改訊息、 參數或傳回值之前或之後傳送或擷取通道層。 如需有關如何擴充服務執行階段的詳細資訊，請參閱[擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。 如需修改，並將自訂物件插入至用戶端執行階段行為的詳細資訊，請參閱[設定和擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
## <a name="clients"></a>用戶端  
 在用戶端，WCF 用戶端物件或用戶端通道會將方法引動過程轉換成傳出訊息與作業結果傳回至呼叫的應用程式的內送訊息。 (如需用戶端類型的詳細資訊，請參閱[WCF 用戶端架構](../../../../docs/framework/wcf/feature-details/client-architecture.md)。)  
  
 WCF 用戶端類型具有執行階段類型，可處理這項端點和作業層級功能。 當應用程式呼叫作業時，<xref:System.ServiceModel.Dispatcher.ClientOperation> 便會將傳出物件轉譯到訊息中、處理攔截器、確認該傳出呼叫符合目標合約，並將傳出訊息交給 <xref:System.ServiceModel.Dispatcher.ClientRuntime>，該執行階段會負責建立及管理傳出通道 (在雙工服務的情況下也包括傳入通道)、處理額外的傳出訊息處理程序 (例如標頭修改)、處理雙向的訊息攔截器，以及將傳入的雙工呼叫傳遞到適當的用戶端 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 物件。 <xref:System.ServiceModel.Dispatcher.ClientOperation> 和 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 都會在訊息 (包括錯誤) 傳回到用戶端時提供相似的服務。  
  
 這兩個執行階段類別是主要的延伸模組，以自訂的 WCF 用戶端物件和通道處理。 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 類別讓使用者能夠對合約中的所有訊息進行攔截和擴充用戶端執行。 <xref:System.ServiceModel.Dispatcher.ClientOperation> 類別則讓使用者能夠對特定作業中的所有訊息進行攔截和擴充用戶端執行。  
  
 使用合約、端點及作業行為，即可修改屬性或插入自訂。 如需如何使用這種行為來執行用戶端執行階段自訂的詳細資訊，請參閱[設定和擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
## <a name="scenarios"></a>案例  
 用戶端系統會因為一些原因而需要擴充，其中包括：  
  
- 自訂訊息驗證。 使用者可能想要強制訊息對特定結構描述有效。 藉由實作 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> 介面，並將實作 (Implementation) 指派到 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.MessageInspectors%2A> 屬性，即可做到這點。 如需範例，請參閱[如何：檢查或修改用戶端上的訊息](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)和[How to:檢查或修改用戶端上的訊息](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)。  
  
- 自訂訊息記錄。 使用者可能想要檢查和記錄某些流經端點的應用程式訊息集。 使用訊息攔截器介面也可以完成這個動作。  
  
- 自訂訊息轉換。 除了修改應用程式程式碼以外，使用者可能想要將特定轉換套用到執行階段中的訊息 (例如，為了進行版本管理)。 使用訊息攔截器介面同樣可以完成這個動作。  
  
- 自訂資料模型。 使用者可能會想要有一個資料或序列化的模型不支援在 WCF 中的預設 (亦即<xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>， <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>，和<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>物件)。 實作訊息格式器介面即可做到這點。 如需詳細資訊，請參閱 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType> 和 <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A?displayProperty=nameWithType> 屬性。  
  
- 自訂參數驗證。 使用者可能想要強制型別參數都是有效的 (即非 XML)。 使用參數偵測器介面即可達到這個目的。 如需範例，請參閱[如何：檢查或修改參數](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)或是[用戶端驗證](../../../../docs/framework/wcf/samples/client-validation.md)。  
  
### <a name="using-the-clientruntime-class"></a>使用 ClientRuntime 類別  
 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 類別是一個擴充點，您可以在這個擴充點上新增會攔截訊息及擴充用戶端行為的延伸物件。 攔截物件可以處理特定合約中的所有訊息，只處理特定作業的訊息，執行自訂通道初始設定，以及實作其他的自訂用戶端應用程式行為。  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A> 屬性會傳回服務初始化回呼用戶端的分派執行階段物件。  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.OperationSelector%2A> 屬性則會接受自訂作業選取器物件。  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ChannelInitializers%2A> 屬性可以用來加入通道初始設定式，以便檢查或修改用戶端通道。  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> 屬性會取得 <xref:System.ServiceModel.Dispatcher.ClientOperation> 物件的集合，而您可以在這些物件中加入自訂訊息攔截器，以提供該作業之訊息的專屬功能。  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ManualAddressing%2A> 屬性允許應用程式關閉一些自動定址標頭，以便直接控制定址。  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.Via%2A> 屬性會設定在傳輸層之訊息的目的端值，以便支援媒介及其他案例。  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A>屬性取得的集合<xref:System.ServiceModel.Dispatcher.IClientMessageInspector>物件，您可以新增自訂訊息攔截器，透過 WCF 用戶端傳輸的所有訊息。  
  
 此外，還有一些會擷取合約資訊的其他屬性：  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractName%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractNamespace%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.ContractClientType%2A>  
  
 如果 WCF 用戶端是雙工的 WCF 用戶端，下列屬性還會擷取回呼 WCF 用戶端資訊：  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackClientType%2A>  
  
- <xref:System.ServiceModel.Dispatcher.ClientRuntime.CallbackDispatchRuntime%2A>  
  
 若要擴充 WCF 用戶端執行跨整個的 WCF 用戶端，請檢閱上可用的屬性<xref:System.ServiceModel.Dispatcher.ClientRuntime>類別，以查看修改屬性或實作介面並將它新增至屬性是否會建立您所需要的功能。 選擇了要建置的特定延伸之後，請透過實作會在叫用時提供存取 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 類別的用戶端行為，將您的延伸插入到適當的 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 屬性。  
  
 您可以使用作業行為 (實作 <xref:System.ServiceModel.Description.IOperationBehavior> 的物件)、合約行為 (實作 <xref:System.ServiceModel.Description.IContractBehavior> 的物件) 或是端點行為 (實作 <xref:System.ServiceModel.Description.IEndpointBehavior> 的物件)，將自訂延伸物件插入到集合中。 安裝行為物件新增到適當的行為集合的方式，可以是程式設計方式、宣告方式 (即透過實作自訂屬性)，或是實作自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 物件以便讓該行為可透過應用程式組態檔來進行插入等方式。 如需詳細資訊，請參閱 <<c0> [ 設定和擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
 如需示範攔截跨 WCF 用戶端的範例，請參閱[How to:檢查或修改用戶端上的訊息](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)。  
  
### <a name="using-the-clientoperation-class"></a>使用 ClientOperation 類別  
 用戶端執行階段修改的位置以及範圍僅限一項服務作業之自訂擴充的插入點，就是 <xref:System.ServiceModel.Dispatcher.ClientOperation> 類別。 (若要修改合約中所有訊息的用戶端執行階段行為，請使用 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 類別)。  
  
 您可以使用 <xref:System.ServiceModel.Dispatcher.ClientRuntime.Operations%2A> 屬性找出表示特定服務作業的 <xref:System.ServiceModel.Dispatcher.ClientOperation> 物件。 下列屬性可讓您將自訂物件插入至 WCF 用戶端系統：  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> 屬性，即可插入作業的自訂 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> 實作或修改目前的格式器。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A> 屬性，即可插入自訂 <xref:System.ServiceModel.Dispatcher.IParameterInspector> 實作或修改目前的實作。  
  
 下列屬性讓您能夠透過與格式器及自訂參數偵測器互動來修改系統。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.SerializeRequest%2A> 屬性，即可控制傳出訊息的序列化。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.DeserializeReply%2A> 屬性，即可控制傳入訊息的還原序列化 (Deserialization)。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.Action%2A> 屬性，即可控制要求訊息的 WS-Addressing 動作。  
  
- 使用<xref:System.ServiceModel.Dispatcher.ClientOperation.BeginMethod%2A>和<xref:System.ServiceModel.Dispatcher.ClientOperation.EndMethod%2A>以指定哪一個 WCF 用戶端的方法與非同步作業建立關聯。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.FaultContractInfos%2A> 屬性來取得集合，其中包含可依詳細類型方式出現在 SOAP 錯誤中的型別。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.IsInitiating%2A> 和 <xref:System.ServiceModel.Dispatcher.ClientOperation.IsTerminating%2A> 屬性，即可分別控制在呼叫作業時是否要產生或卸除工作階段。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.IsOneWay%2A> 屬性，即可控制作業是否為單向作業。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.Parent%2A> 屬性，即可取得 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 包含物件。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.Name%2A> 屬性，即可取得作業的名稱。  
  
- 使用 <xref:System.ServiceModel.Dispatcher.ClientOperation.SyncMethod%2A> 屬性，即可控制要對應到作業的方法。  
  
 若要擴充 WCF 用戶端執行跨只有一個服務作業，請檢閱上可用的屬性<xref:System.ServiceModel.Dispatcher.ClientOperation>類別，以查看修改屬性或實作介面並將它新增至屬性是否會建立您所需要的功能。 選擇了要建置的特定延伸之後，請透過實作會在叫用時提供存取 <xref:System.ServiceModel.Dispatcher.ClientOperation> 類別的用戶端行為，將您的延伸插入到適當的 <xref:System.ServiceModel.Dispatcher.ClientOperation> 屬性。 然後，您就可以在該行為的內部，將 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 屬性修改成符合您的需求。  
  
 一般而言，實作作業行為 (即實作 <xref:System.ServiceModel.Description.IOperationBehavior> 介面的物件) 就夠了，不過您也可以使用端點行為與合約行為，找到特定作業的 <xref:System.ServiceModel.Description.OperationDescription>，並在此處附加該行為來達成相同結果。 如需詳細資訊，請參閱 <<c0> [ 設定和擴充執行階段行為](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)。  
  
 若要從組態使用自訂行為，請使用自訂行為組態區段處理常式來安裝您的行為。 您也可以建立自訂屬性以安裝行為。  
  
 如需示範攔截跨 WCF 用戶端的範例，請參閱[How to:檢查或修改參數](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Dispatcher.ClientRuntime>
- <xref:System.ServiceModel.Dispatcher.ClientOperation>
- [如何：檢查或修改用戶端上的訊息](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-messages-on-the-client.md)
- [如何：檢查或修改參數](../../../../docs/framework/wcf/extending/how-to-inspect-or-modify-parameters.md)
