---
title: 訊息偵測器
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: aa5b68f203164a1c50ae9ef921032bd6e5c7bfb8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930704"
---
# <a name="message-inspectors"></a><span data-ttu-id="1f32e-102">訊息偵測器</span><span class="sxs-lookup"><span data-stu-id="1f32e-102">Message Inspectors</span></span>
<span data-ttu-id="1f32e-103">這個範例會示範如何實作與設定用戶端和服務訊息偵測器。</span><span class="sxs-lookup"><span data-stu-id="1f32e-103">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="1f32e-104">訊息偵測器是一種可在服務模型的用戶端執行階段中使用的擴充性物件，並以程式設計方式或透過組態分派執行階段，因此可在接收訊息之後或傳送訊息之前偵測及變更訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-104">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="1f32e-105">這個範例會實作基本用戶端和服務的訊息驗證機制，而這個驗證機制會對一組可設定的 XML 結構描述文件驗證傳入的訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-105">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="1f32e-106">請注意，這個範例不會對每個作業驗證訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-106">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="1f32e-107">這個作用則是針對簡化而設計。</span><span class="sxs-lookup"><span data-stu-id="1f32e-107">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="1f32e-108">訊息偵測器</span><span class="sxs-lookup"><span data-stu-id="1f32e-108">Message Inspector</span></span>  
 <span data-ttu-id="1f32e-109">用戶端訊息偵測器會實作 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> 介面，而服務訊息偵測器會實作 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 介面。</span><span class="sxs-lookup"><span data-stu-id="1f32e-109">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="1f32e-110">該實作可以從用於兩端的訊息偵測器結合至單一類別。</span><span class="sxs-lookup"><span data-stu-id="1f32e-110">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="1f32e-111">這個範例就會實作這類結合的訊息偵測器。</span><span class="sxs-lookup"><span data-stu-id="1f32e-111">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="1f32e-112">對已驗證之傳入和傳出訊息傳遞一組結構描述而建構偵測器，該偵測器並可讓開發人員指定是否要驗證傳入或傳出訊息，以及偵測器是否處於分派或用戶端模式，而這都會影響本主題之後會討論的錯誤處理方式。</span><span class="sxs-lookup"><span data-stu-id="1f32e-112">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
```  
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 <span data-ttu-id="1f32e-113">任何服務 (發送器) 偵測器都必須實作兩個 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> 方法 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 和 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>。</span><span class="sxs-lookup"><span data-stu-id="1f32e-113">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="1f32e-114">接收訊息時，發送器會叫用 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>，但將此項解除序列化並分派至作業之前，是由通道堆疊所處理並指派至服務。</span><span class="sxs-lookup"><span data-stu-id="1f32e-114"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="1f32e-115">如果已加密傳入訊息，在訊息抵達訊息偵測器時就會進行解密。</span><span class="sxs-lookup"><span data-stu-id="1f32e-115">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="1f32e-116">方法會取得當做參考屬性傳遞的 `request` 訊息，而此參考屬性可讓您根據需要檢查訊息、管理或取代訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-116">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="1f32e-117">傳回值可以是服務將回覆傳回現行訊息時，當做傳遞至 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> 之相互關聯狀態物件使用的任何物件。</span><span class="sxs-lookup"><span data-stu-id="1f32e-117">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="1f32e-118">在此範例中，<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 會將訊息檢查 (驗證) 委派給私用的本機方法 `ValidateMessageBody`，而且不會傳回任何相互關聯狀態物件。</span><span class="sxs-lookup"><span data-stu-id="1f32e-118">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="1f32e-119">這個方法會確定不會有無效的訊息傳遞至服務。</span><span class="sxs-lookup"><span data-stu-id="1f32e-119">This method ensures that no invalid messages pass into the service.</span></span>  
  
```  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="1f32e-120">已處理傳入訊息時，每次準備將回覆傳送回用戶端，或者傳入訊息為單向訊息時，就會叫用 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>。</span><span class="sxs-lookup"><span data-stu-id="1f32e-120"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="1f32e-121">這樣可不管 MEP，都將延伸項目當做已對稱地呼叫。</span><span class="sxs-lookup"><span data-stu-id="1f32e-121">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="1f32e-122">搭配 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 使用時，會當做參考參數傳遞訊息，並且可檢查、修改或取代訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-122">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="1f32e-123">在此範例中執行的訊息驗證會再次委派給 `ValidMessageBody` 方法，在這裡的驗證錯誤處理方式稍有不同。</span><span class="sxs-lookup"><span data-stu-id="1f32e-123">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="1f32e-124">如果是在服務上發生驗證錯誤，`ValidateMessageBody` 方法會擲回 <xref:System.ServiceModel.FaultException> 衍生的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f32e-124">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="1f32e-125">在 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> 中，這些例外狀況可以放入服務模型基礎結構，在這裡會自動將例外狀況轉換為 SOAP 錯誤，並轉送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="1f32e-125">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="1f32e-126">在 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> 中，例外狀況不可放置在基礎結構中，因為服務擲回的錯誤例外狀況轉換會在呼叫訊息偵測器之前即發生。</span><span class="sxs-lookup"><span data-stu-id="1f32e-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="1f32e-127">因此，下列實作可以攔截已知的 `ReplyValidationFault` 例外狀況，並以明確的錯誤訊息取代回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-127">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="1f32e-128">這個方法可確定服務實作不會傳回無效的訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-128">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
```  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error   
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,   
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 <span data-ttu-id="1f32e-129">用戶端訊息偵測器的運作方法也很類似。</span><span class="sxs-lookup"><span data-stu-id="1f32e-129">The client message inspector is very similar.</span></span> <span data-ttu-id="1f32e-130">必須從 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> 實作的這兩個方法為 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> 和 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f32e-130">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="1f32e-131">當用戶端應用程式或作業格式器編寫訊息時，就會叫用 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>。</span><span class="sxs-lookup"><span data-stu-id="1f32e-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="1f32e-132">搭配使用發送器訊息偵測器時，就可以只檢查或完全取代訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-132">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="1f32e-133">在此範例中，偵測器會分派至相同的本機 `ValidateMessageBody` Helper 方法，而這個方法也會用於委派訊息偵測器。</span><span class="sxs-lookup"><span data-stu-id="1f32e-133">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="1f32e-134">用戶端和服務驗證 (如建構函式中指定) 之間的行為差異，主要是在用戶端驗證擲回的本機例外狀況會放置在使用者程式碼中，其原因為這些例外狀況是在本機產生，而不是因為服務錯誤所產生。</span><span class="sxs-lookup"><span data-stu-id="1f32e-134">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="1f32e-135">一般來說，規則為服務發送器偵測器會擲回錯誤，而用戶端偵測器則是擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f32e-135">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="1f32e-136">這個 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> 實作可確定不會將無效的訊息傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="1f32e-136">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
```  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="1f32e-137">`AfterReceiveReply` 實作可確定從服務接收的無效訊息不會轉送至用戶端使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="1f32e-137">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="1f32e-138">此特殊訊息偵測器的中心則為 `ValidateMessageBody` 方法。</span><span class="sxs-lookup"><span data-stu-id="1f32e-138">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="1f32e-139">若要執行其工作，會包裝驗證的 <xref:System.Xml.XmlReader> 與所傳遞訊息的本文內容子樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="1f32e-139">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="1f32e-140">將以一組訊息偵測器持有的結構描述來填入讀取器，而且驗證回呼會設定為代理人，也就是與此方法一起定義的 `InspectionValidationHandler`。</span><span class="sxs-lookup"><span data-stu-id="1f32e-140">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="1f32e-141">若要執行驗證，接著便需要讀取訊息，並多工緩衝處理至以記憶體資料流為基礎的 <xref:System.Xml.XmlDictionaryWriter>。</span><span class="sxs-lookup"><span data-stu-id="1f32e-141">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="1f32e-142">如果在處理序期間發生驗證錯誤或警告，就會叫用回呼方法。</span><span class="sxs-lookup"><span data-stu-id="1f32e-142">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="1f32e-143">如果沒有任何錯誤，就會建構從原始訊息複製屬性和標頭的新訊息，並在記憶體資料流中使用現在驗證的 Infoset (由 <xref:System.Xml.XmlDictionaryReader> 包裝並新增至取代訊息)。</span><span class="sxs-lookup"><span data-stu-id="1f32e-143">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
```  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =   
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =   
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =   
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =   
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new   
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,   
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =   
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =   
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 <span data-ttu-id="1f32e-144">每次發生結構描述驗證錯誤或警告時，驗證的 `InspectionValidationHandler` 就會呼叫 <xref:System.Xml.XmlReader> 方法。</span><span class="sxs-lookup"><span data-stu-id="1f32e-144">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="1f32e-145">下列實作只能處理錯誤，而忽略所有警告。</span><span class="sxs-lookup"><span data-stu-id="1f32e-145">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="1f32e-146">在第一個考量上，可能可以將驗證 <xref:System.Xml.XmlReader> 插入具有訊息偵測器的訊息，並在處理訊息時進行驗證，而不緩衝處理訊息。</span><span class="sxs-lookup"><span data-stu-id="1f32e-146">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="1f32e-147">因此，這表示偵測到無效的 XML 節點時，此回呼會在服務模型基礎結構的某個位置或使用者程式碼中擲回驗證例外狀況，因而導致無法預期的行為。</span><span class="sxs-lookup"><span data-stu-id="1f32e-147">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="1f32e-148">緩衝處理方法會完全保護使用者程式碼不受無效訊息的影響。</span><span class="sxs-lookup"><span data-stu-id="1f32e-148">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="1f32e-149">如前所討論，處理常式擲回的例外狀況和用戶端與服務擲回的例外狀況不同。</span><span class="sxs-lookup"><span data-stu-id="1f32e-149">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="1f32e-150">在服務上，例外狀況是衍生自 <xref:System.ServiceModel.FaultException>，而在用戶端上，例外狀況則是一般自訂例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1f32e-150">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
```  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel   
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a><span data-ttu-id="1f32e-151">行為</span><span class="sxs-lookup"><span data-stu-id="1f32e-151">Behavior</span></span>  
 <span data-ttu-id="1f32e-152">訊息偵測器為用戶端執行階段或分派執行階段的延伸項目。</span><span class="sxs-lookup"><span data-stu-id="1f32e-152">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="1f32e-153">這類延伸模組是使用*行為*來設定。</span><span class="sxs-lookup"><span data-stu-id="1f32e-153">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="1f32e-154">行為就是類別，而這個類別會透過變更預設組態或新增延伸項目 (例如訊息偵測器)，來變更服務模型執行階段的行為。</span><span class="sxs-lookup"><span data-stu-id="1f32e-154">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="1f32e-155">下列 `SchemaValidationBehavior` 類別是用來將此範例的訊息偵測器新增至用戶端或分派執行階段的行為。</span><span class="sxs-lookup"><span data-stu-id="1f32e-155">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="1f32e-156">在這兩個例子中，實作都相當基本。</span><span class="sxs-lookup"><span data-stu-id="1f32e-156">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="1f32e-157">在 <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> 和 <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A> 中，會建立訊息偵測器並新增至相對之執行階段的 <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> 集合中。</span><span class="sxs-lookup"><span data-stu-id="1f32e-157">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
```  
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;   
    bool validateRequest;   
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool   
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,   
       System.ServiceModel.Channels.BindingParameterCollection   
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,   
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,   
         System.ServiceModel.Dispatcher.EndpointDispatcher   
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =   
           new SchemaValidationMessageInspector(schemaSet,   
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="1f32e-158">此特定行為不會兼做屬性，因此無法以宣告方式新增至服務類型的合約類型。</span><span class="sxs-lookup"><span data-stu-id="1f32e-158">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="1f32e-159">這是根據設計所做的決策，因為結構描述集合無法載入屬性宣告，而參考至此屬性中額外的組態位置 (例如，應用程式設定) 則表示所建立的組態項目，會與其他服務模型組態不一致。</span><span class="sxs-lookup"><span data-stu-id="1f32e-159">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="1f32e-160">因此，您只能以命令方式，透過程式碼和服務模型組態延伸項目新增此行為。</span><span class="sxs-lookup"><span data-stu-id="1f32e-160">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="1f32e-161">透過組態新增訊息偵測器</span><span class="sxs-lookup"><span data-stu-id="1f32e-161">Adding the Message Inspector through Configuration</span></span>  
 <span data-ttu-id="1f32e-162">若要在應用程式佈建檔中的端點上設定自訂行為, 服務模型會要求實施者建立由衍生自之<xref:System.ServiceModel.Configuration.BehaviorExtensionElement>類別所代表的設定*延伸元素*。</span><span class="sxs-lookup"><span data-stu-id="1f32e-162">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="1f32e-163">針對如本節所討論之下列延伸項目所示的延伸項目，此延伸項目必須新增至服務模型的組態區段。</span><span class="sxs-lookup"><span data-stu-id="1f32e-163">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 <span data-ttu-id="1f32e-164">延伸項目可以新增至應用程式或 ASP.NET 組態檔 (最常見的方式)，或新增至電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="1f32e-164">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="1f32e-165">當延伸項目新增至組態範圍時，可以將行為新增至行為組態，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="1f32e-165">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="1f32e-166">行為組態為可重複使用的項目，也可依需求套用至多個端點。</span><span class="sxs-lookup"><span data-stu-id="1f32e-166">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="1f32e-167">由於在此處要設定的特定行為會實作 <xref:System.ServiceModel.Description.IEndpointBehavior>，因此只能在組態檔中相對的組態區段中使用。</span><span class="sxs-lookup"><span data-stu-id="1f32e-167">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />    
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="1f32e-168">設定訊息偵測器的 `<schemaValidator>` 項目是由 `SchemaValidationBehaviorExtensionElement` 類別所支援。</span><span class="sxs-lookup"><span data-stu-id="1f32e-168">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="1f32e-169">類別會公開兩個名稱為 `ValidateRequest` 和 `ValidateReply` 的布林公用屬性。</span><span class="sxs-lookup"><span data-stu-id="1f32e-169">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="1f32e-170">這兩個屬性都會使用 <xref:System.Configuration.ConfigurationPropertyAttribute> 來標示。</span><span class="sxs-lookup"><span data-stu-id="1f32e-170">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="1f32e-171">這個屬性 (Attribute) 會組成程式碼屬性 (Properties) 和 XML 屬性 (Attribute) 之間的連結，而您可以在之前的 XML 組態項目中看到此連結。</span><span class="sxs-lookup"><span data-stu-id="1f32e-171">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="1f32e-172">類別也擁有額外以 `Schemas` 標示，而且型別為 <xref:System.Configuration.ConfigurationCollectionAttribute> 的 `SchemaCollection` 屬性，此型別也是範例的一部分，但是為了簡潔起見在這份文件中省略不提。</span><span class="sxs-lookup"><span data-stu-id="1f32e-172">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="1f32e-173">這個屬性會與集合一起使用，而集合項目類別 `SchemaConfigElement` 支援先前組態程式碼片段中的 `<schemas>` 項目，並允許將結構描述集合新增至驗證組。</span><span class="sxs-lookup"><span data-stu-id="1f32e-173">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="1f32e-174">當執行階段在建置用戶端或端點的同時評估組態資料時，覆寫的 `CreateBehavior` 方法便會將組態資料轉換為行為物件。</span><span class="sxs-lookup"><span data-stu-id="1f32e-174">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
```  
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType   
    {   
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }   
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new   
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new   
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =   
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new   
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs   
     //.NET Framework to build a nested section of   
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="1f32e-175">以命令方式新增訊息偵測器</span><span class="sxs-lookup"><span data-stu-id="1f32e-175">Adding Message Inspectors Imperatively</span></span>  
 <span data-ttu-id="1f32e-176">除了使用屬性 (由於先前所提的原因，在此範例中不支援) 和組態，也可以使用命令式程式碼輕鬆地將行為新增至用戶端和服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="1f32e-176">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="1f32e-177">在此範例中，會在用戶端應用程式中完成此動作，以測試用戶端訊息偵測器。</span><span class="sxs-lookup"><span data-stu-id="1f32e-177">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="1f32e-178">`GenericClient` 類別衍生自 <xref:System.ServiceModel.ClientBase%601>，而這會對使用者程式碼公開端點組態。</span><span class="sxs-lookup"><span data-stu-id="1f32e-178">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="1f32e-179">在隱含地開啟用戶端之前，您可以變更端點組態，例如像下列程式碼所示地新增行為。</span><span class="sxs-lookup"><span data-stu-id="1f32e-179">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="1f32e-180">在服務上新增行為幾乎等同於此處顯示的用戶端技術，並必須在開啟服務主機之前即已執行新增動作。</span><span class="sxs-lookup"><span data-stu-id="1f32e-180">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
```  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),   
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new   
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1f32e-181">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="1f32e-181">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1f32e-182">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="1f32e-182">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="1f32e-183">若要建立方案, 請依照[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="1f32e-183">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="1f32e-184">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="1f32e-184">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1f32e-185">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1f32e-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1f32e-186">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="1f32e-186">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1f32e-187">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="1f32e-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1f32e-188">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="1f32e-188">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
