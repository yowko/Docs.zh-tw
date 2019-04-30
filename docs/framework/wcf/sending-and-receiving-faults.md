---
title: 傳送和接收錯誤
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], sending
ms.assetid: 7be6fb96-ce2a-450b-aebe-f932c6a4bc5d
ms.openlocfilehash: 2757f98066931ca1b5e3ef147cee2c819ee22606
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949600"
---
# <a name="sending-and-receiving-faults"></a>傳送和接收錯誤
SOAP 錯誤會將錯誤狀況資訊從服務傳送到用戶端，而在雙工案例中，則是以互通的方式從用戶端傳送到服務。 一般來說，服務會定義自訂錯誤內容，並指定透過哪項作業來傳回這些內容 (如需詳細資訊，請參閱 <<c0> [ 定義和指定的錯誤](../../../docs/framework/wcf/defining-and-specifying-faults.md)。)本主題將說明在發生錯誤情況時，服務或雙工用戶端如何傳送這些錯誤，以及用戶端或服務應用程式如何處理這些錯誤。 如需 Windows Communication Foundation (WCF) 應用程式中的錯誤處理的概觀，請參閱 <<c0> [ 指定及處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。  
  
## <a name="sending-soap-faults"></a>傳送 SOAP 錯誤  
 已宣告的 SOAP 錯誤是其中作業具有指定自訂 SOAP 錯誤類型之 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>的 SOAP 錯誤。 未宣告的 SOAP 錯誤則是在作業的合約中未指定的 SOAP 錯誤。  
  
### <a name="sending-declared-faults"></a>傳送已宣告的錯誤  
 若要傳送已宣告的 SOAP 錯誤，請偵測包含適當 SOAP 錯誤的錯誤情況並擲回新的 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>，其中的型別參數為該作業之 <xref:System.ServiceModel.FaultContractAttribute> 中所指定的新物件型別。 下列程式碼範例將示範如何使用 <xref:System.ServiceModel.FaultContractAttribute> 來指定 `SampleMethod` 作業可以傳回 SOAP 錯誤，連同 `GreetingFault` 的詳細型別。  
  
 [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
 [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
 若要將 `GreetingFault` 錯誤資訊傳送到用戶端，請捕捉適當的錯誤情況並擲回包含新的 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> 物件之新的 `GreetingFault` (屬於 `GreetingFault` 型別) 做為引數，如下列程式碼範例所示。 如果用戶端是 WCF 用戶端應用程式，它會碰到 managed 例外狀況類型所在<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>型別的`GreetingFault`。  
  
 [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
 [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
### <a name="sending-undeclared-faults"></a>傳送未宣告的錯誤  
 您可以很適合用來快速診斷及偵錯 WCF 應用程式，但其可用性的問題，因為偵錯工具僅限於傳送未宣告的錯誤。 在偵錯時，使用 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> 屬性是較普遍的建議做法。 當您將此值設為 true，用戶端會碰到諸如 <xref:System.ServiceModel.FaultException%601> 類別的 <xref:System.ServiceModel.ExceptionDetail> 例外狀況之類的錯誤。  
  
> [!IMPORTANT]
>  因為 managed 例外狀況可以顯露內部的應用程式的資訊，請設定<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType>或是<xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType>到`true`可允許 WCF 用戶端取得有關內部服務作業例外狀況，包括個人資訊識別或其他機密資訊。  
>   
>  因此，若您只是暫時對服務應用程式進行偵錯，才建議把 <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> 設為 `true`。 此外，若某個方法以這種方式傳回未處理的 Managed 例外狀況，則該方法的 WSDL 不會包含 <xref:System.ServiceModel.FaultException%601> 型別之 <xref:System.ServiceModel.ExceptionDetail> 的合約。 用戶端必須預期未知 SOAP 錯誤的可能性 (傳回給 WCF 用戶端，做為<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>物件) 以正確取得偵錯資訊。  
  
 若要傳送未宣告的 SOAP 錯誤，請擲回 <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 物件 (亦即，不是泛型 <xref:System.ServiceModel.FaultException%601> 型別)，並將字串傳送至建構函式。 這公開的 WCF 用戶端應用程式當做擲回<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>例外狀況的字串可使用的呼叫<xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType>方法。  
  
> [!NOTE]
>  如果您宣告 String 型別的 SOAP 錯誤，則請將此項目做為 <xref:System.ServiceModel.FaultException%601> 擲回服務 (當中的型別參數是一個 <xref:System.String?displayProperty=nameWithType>，而字串值則是指派給 <xref:System.ServiceModel.FaultException%601.Detail%2A?displayProperty=nameWithType> 屬性，而且無法透過 <xref:System.ServiceModel.FaultException%601.ToString%2A?displayProperty=nameWithType> 取得)。  
  
## <a name="handling-faults"></a>處理錯誤  
 WCF 用戶端，在 SOAP 錯誤在通訊期間發生感興趣，用戶端應用程式的引發為 managed 例外狀況。 雖然有許多的任何程式執行期間可能發生的例外狀況，使用 WCF 用戶端程式設計模型的應用程式能夠處理下列兩種因通訊而產生的例外狀況。  
  
- <xref:System.TimeoutException>  
  
- <xref:System.ServiceModel.CommunicationException>  
  
 當作業超出指定的逾時期間，就會擲回 <xref:System.TimeoutException> 物件。  
  
 當服務或用戶端上出現一些可修復的通訊錯誤情況，就會擲回 <xref:System.ServiceModel.CommunicationException> 物件。  
  
 <xref:System.ServiceModel.CommunicationException> 類別包含兩個重要的衍生型別，分別是 <xref:System.ServiceModel.FaultException> 和泛型 <xref:System.ServiceModel.FaultException%601> 型別。  
  
 當接聽項收到未預期的或於作業合約中指定的錯誤，就會擲回 <xref:System.ServiceModel.FaultException> 例外狀況；當針對應用程式進行偵錯，且服務的 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> 屬性設為 `true` 時，就很容易發生這個情況。  
  
 收到作業合約中指定的錯誤時，用戶端會擲回 <xref:System.ServiceModel.FaultException%601> 例外狀況，以回應雙向作業 (也就是具有 <xref:System.ServiceModel.OperationContractAttribute> 屬性，且將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 設為 `false` 的方法)。  
  
> [!NOTE]
>  當 WCF 服務有<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType>或是<xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType>屬性設定為`true`用戶端會把這種未宣告<xref:System.ServiceModel.FaultException%601>型別的<xref:System.ServiceModel.ExceptionDetail>。 用戶端可以捕捉此特定錯誤，或是在 <xref:System.ServiceModel.FaultException> 的 catch 區塊中處理此錯誤。  
  
 一般來說，只有 <xref:System.ServiceModel.FaultException%601>、<xref:System.TimeoutException>，和 <xref:System.ServiceModel.CommunicationException> 例外狀況會與用戶端及服務相關。  
  
> [!NOTE]
>  而其他例外狀況，當然一定會發生。 未預期的例外狀況包含 <xref:System.OutOfMemoryException?displayProperty=nameWithType> 之類的災難性失敗；一般來說，應用程式應該不會捕捉到這類方法。  
  
### <a name="catch-fault-exceptions-in-the-correct-order"></a>以正確順序來捕捉錯誤例外狀況  
 由於 <xref:System.ServiceModel.FaultException%601> 係衍生自 <xref:System.ServiceModel.FaultException>，而 <xref:System.ServiceModel.FaultException> 則是衍生自 <xref:System.ServiceModel.CommunicationException>，請務必以正確順序來捕捉這些例外狀況。 例如，假如在您第一次捕捉 <xref:System.ServiceModel.CommunicationException> 時使用 try/catch 區塊，則所有指定與未指定的 SOAP 錯誤都會就地處理；而且一律不會叫用任何後續的 catch 區塊來處理自訂 <xref:System.ServiceModel.FaultException%601> 例外狀況。  
  
 請記住，一項作業可以傳回的指定錯誤數量不限。 每一項錯誤都具有唯一的型別，而且必須個別處理。  
  
### <a name="handle-exceptions-when-closing-the-channel"></a>關閉通道時處理例外狀況  
 大部分的先前的討論有如何處理錯誤期間處理的應用程式訊息，也就是傳送用戶端應用程式呼叫 WCF 用戶端物件上的作業時，明確傳送的用戶端的訊息。  
  
 就算是本機物件，處理物件也可能引發或遮罩在回收處理序期間所發生的例外狀況。 當您使用 WCF 用戶端物件，會發生類似項目。 當您呼叫作業時，事實上您是透過已建立的連線來傳送訊息。 如果連線無法完全關閉，或是已經關閉，則關閉通道會擲回例外狀況，就算所有作業都正常傳回也是一樣。  
  
 一般來說，用戶端物件通道可透過下列其中一種方式來關閉：  
  
- 當 WCF 用戶端物件就會回收。  
  
- 當用戶端應用程式呼叫 <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType> 時。  
  
- 當用戶端應用程式呼叫 <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> 時。  
  
- 當用戶端應用程式呼叫某個正在終止工作階段作業的作業時。  
  
 不管什麼情況，關閉通道都會讓通道開始關閉任何基礎通道，進而傳送訊息以支援應用程式層級的複雜功能。 例如，當合約需要工作階段嘗試透過繫結來建立工作階段時 (方法是藉由與服務通道交換訊息，直到建立工作階段為止)。 一旦通道關閉，基礎工作階段通道會通知服務，工作階段已經終止。 在此情況下，如果通道已經中止、關閉，或是因為其他原因而無法使用 (例如，當網路纜線已拔除時)，用戶端通道將無法通知服務通道，告知工作階段已終止且可能擲回例外狀況。  
  
### <a name="abort-the-channel-if-necessary"></a>必要時中止通道  
 由於關閉通道也可能會擲回例外狀況，因此我們建議您除了以正確順序來捕捉錯誤例外狀況外，務必記得要中止用來呼叫 catch 區塊的通道。  
  
 如果錯誤傳送了與某項作業相關的特定錯誤資訊，而其他作業也可能透過它來傳送資訊時，就不需要中止通道 (儘管這些情況很罕見)。 在其他任何情況中，建議您中止通道。 如需可示範這些重點的範例，請參閱 <<c0> [ 預期的例外狀況](../../../docs/framework/wcf/samples/expected-exceptions.md)。  
  
 下列程式碼範例將說明如何透過基本用戶端應用程式來處理 SOAP 錯誤例外狀況，包括已宣告與未宣告的錯誤。  
  
> [!NOTE]
>  此範例程式碼不會使用 `using` 建構。 關閉通道，可以擲回例外狀況，因為它被建議應用程式建立 WCF 用戶端第一次，並開啟，請使用，並關閉 WCF 用戶端在同一個 try 區塊。 如需詳細資訊，請參閱 < [WCF Client Overview](../../../docs/framework/wcf/wcf-client-overview.md)並[使用關閉和中止發行 WCF 用戶端資源](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)。  
  
 [!code-csharp[FaultContractAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.FaultException>
- <xref:System.ServiceModel.FaultException%601>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- [預期的例外狀況](../../../docs/framework/wcf/samples/expected-exceptions.md)
- [使用關閉和中止發行 WCF 用戶端資源](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)
