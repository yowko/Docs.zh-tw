---
title: 使用訊息合約
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
caps.latest.revision: 46
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 600d938b8981ddfabcb79028ae66b5b9d02107b7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="using-message-contracts"></a><span data-ttu-id="ea9a6-102">使用訊息合約</span><span class="sxs-lookup"><span data-stu-id="ea9a6-102">Using Message Contracts</span></span>
<span data-ttu-id="ea9a6-103">通常當建置 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式時，程式開發人員會特別注意資料結構與序列化的問題，並且本身不需要考慮傳送資料的訊息結構。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-103">Typically when building [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="ea9a6-104">針對這類應用程式，建立參數的資料合約或傳回值是很明確的。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="ea9a6-105">(如需詳細資訊，請參閱[在服務合約中指定資料傳輸](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。)</span><span class="sxs-lookup"><span data-stu-id="ea9a6-105">(For more information, see [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="ea9a6-106">但是，有時候完整控制 SOAP 訊息的結構與控制其內容一樣重要。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="ea9a6-107">當互通性很重要，或是要具體控制在訊息層級或訊息部分的安全性問題時，這就顯得特別重要。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="ea9a6-108">在這些情況下，您可以建立*訊息合約*，可讓您指定所需的精確 SOAP 訊息的結構。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="ea9a6-109">此主題會討論如何使用各種訊息合約屬性，以建立作業的特定訊息合約。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="ea9a6-110">在作業中使用訊息合約</span><span class="sxs-lookup"><span data-stu-id="ea9a6-110">Using Message Contracts in Operations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ea9a6-111"> 支援在建立模型的作業*遠端程序呼叫 (RPC) 樣式*或*傳訊樣式*。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-111"> supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="ea9a6-112">在 RPC 樣式作業中，您可以使用任何可序列化類型，並且有存取本機呼叫的功能，例如多個參數以及 `ref` 與 `out` 參數。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="ea9a6-113">在這個樣式中，選擇的序列化形式會控制基礎訊息中的資料結構，並且 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段會建立訊息以支援作業。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime creates the messages to support the operation.</span></span> <span data-ttu-id="ea9a6-114">這可以讓不熟悉 SOAP 和 SOAP 訊息的程式開發人員，快速而輕鬆地建立與使用服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="ea9a6-115">下列程式碼範例顯示根據 RPC 樣式建立模型的服務作業。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="ea9a6-116">通常資料合約已足夠定義訊息的結構描述。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="ea9a6-117">例如，在之前的範例中，如果 `BankingTransaction` 和 `BankingTransactionResponse` 都有定義基礎 SOAP 訊息內容的資料合約，對大部分的應用程式來說就已足夠。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="ea9a6-118">如需資料合約的詳細資訊，請參閱[使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-118">For more information about data contracts, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="ea9a6-119">但是，偶爾也會需要精確控制透過網路傳輸 SOAP 訊息結構的方式。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="ea9a6-120">最常見的案例是插入自訂 SOAP 標頭。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="ea9a6-121">另一個常見的案例是定義訊息標頭與本文的安全性屬性，也就是決定是否要數位簽署或加密這些項目。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="ea9a6-122">最後，某些協力廠商 SOAP 堆疊會要求訊息使用特定的格式。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="ea9a6-123">訊息樣式作業提供這項控制。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="ea9a6-124">訊息樣式作業最多只有一個參數和一個傳回值，並且兩者都是訊息類型；也就是它們會直接序列化至指定的 SOAP 訊息結構中。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="ea9a6-125">這可能是使用 <xref:System.ServiceModel.MessageContractAttribute> 或 <xref:System.ServiceModel.Channels.Message> 類型標記的任何類型。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="ea9a6-126">下列程式碼範例顯示類似之前 RCP 樣式的作業，但是使用訊息樣式。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="ea9a6-127">例如，如果 `BankingTransaction` 和 `BankingTransactionResponse` 都是訊息合約的類型，則下列作業中的程式碼就有效。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="ea9a6-128">但是，下列程式碼無效。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="ea9a6-129">包含不遵循其中一種有效模式之訊息合約類型的任何作業都會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="ea9a6-130">當然，不包含訊息合約類型的作業則不受這些限制。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="ea9a6-131">如果類型同時是訊息合約與資料合約，當在作業中使用類型時只會考量其訊息合約。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="ea9a6-132">定義訊息合約</span><span class="sxs-lookup"><span data-stu-id="ea9a6-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="ea9a6-133">若要定義類型的訊息合約 (也就是定義類型與 SOAP 封套之間的對應)，請將 <xref:System.ServiceModel.MessageContractAttribute> 套用至類型。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="ea9a6-134">然後將 <xref:System.ServiceModel.MessageHeaderAttribute> 套用至想要當做 SOAP 標頭之類型的成員，再將 <xref:System.ServiceModel.MessageBodyMemberAttribute> 套用至想要當做訊息之 SOAP 本文部分的成員。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="ea9a6-135">下列程式碼提供使用訊息合約的範例。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-135">The following code provides an example of using a message contract.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="ea9a6-136">使用這個類型做為作業參數時，會產生下列 SOAP envelope：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ea9a6-137">請注意，`operation` 和 `transactionDate` 會顯示為 SOAP 標頭，而 SOAP 本文是由包含 `BankingTransaction`、`sourceAccount` 和 `targetAccount` 的 `amount` 包裝函式元素所組成。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="ea9a6-138">您可以將 <xref:System.ServiceModel.MessageHeaderAttribute> 和 <xref:System.ServiceModel.MessageBodyMemberAttribute> 套用至所有欄位、屬性和事件 (不論其是否屬於公開、私用、保護或內部)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="ea9a6-139"><xref:System.ServiceModel.MessageContractAttribute> 可讓您指定 WrapperName 和 WrapperNamespace 屬性，用來控制 SOAP 訊息本文中包裝函式元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="ea9a6-140">預設訊息合約的名稱類型會使用包裝函式和命名空間定義的訊息合約`HYPERLINK "http://tempuri.org/" http://tempuri.org/`做為預設命名空間。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined  `HYPERLINK "http://tempuri.org/" http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea9a6-141">在訊息合約中會忽略 <xref:System.Runtime.Serialization.KnownTypeAttribute> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="ea9a6-142">如果需要 <xref:System.Runtime.Serialization.KnownTypeAttribute>，請將其置於使用有問題之訊息合約的作業。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="ea9a6-143">控制標頭和本文部分的名稱與命名空間</span><span class="sxs-lookup"><span data-stu-id="ea9a6-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="ea9a6-144">在訊息合約的 SOAP 表示法中，每個標頭和本文部分會對應至擁有名稱與命名空間的 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="ea9a6-145">根據預設，命名空間與訊息參與之服務合約的命名空間相同，並且名稱是由套用 <xref:System.ServiceModel.MessageHeaderAttribute> 或 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性的成員名稱來判定。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="ea9a6-146">您可以藉由管理 <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> 和  <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (在  <xref:System.ServiceModel.MessageHeaderAttribute> 和  <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性的父類別上) 以變更這些預設值。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="ea9a6-147">請考量下列程式碼範例中的類別。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="ea9a6-148">在這個範例中，`IsAudited` 標頭在程式碼指定的命名空間內，而表示 `theData` 成員的本文部分則是由名為 `transactionData` 的 XML 項目所表示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="ea9a6-149">以下顯示本訊息合約產生的 XML。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-149">The following shows the XML generated for this message contract.</span></span>  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="ea9a6-150">控制是否要包裝 SOAP 本文部分</span><span class="sxs-lookup"><span data-stu-id="ea9a6-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="ea9a6-151">根據預設，SOAP 本文部分會在已包裝的項目內序列化。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="ea9a6-152">例如，下列程式碼顯示產生自 `HelloGreetingMessage` 訊息之訊息合約中，<xref:System.ServiceModel.MessageContractAttribute> 型別名稱的 `HelloGreetingMessage` 包裝函式項目。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="ea9a6-153">若要隱藏包裝函式項目，請將 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="ea9a6-154">若要控制包裝函式項目的名稱與命名空間，請使用 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 和 <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ea9a6-155">在訊息中如果有一個以上未包裝的訊息本文部分，就不符合 WS-I Basic Profile 1.1 並且不建議在設計新訊息合約時使用。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="ea9a6-156">但是，在某些特定互通性案例中，可能會需要有一個以上未包裝的訊息本文部分。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="ea9a6-157">如果您要在訊息本文中傳輸一段以上的資料，建議您使用預設 (包裝) 模式。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="ea9a6-158">在未包裝訊息中有一個以上的訊息標頭是完全可接受的。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="ea9a6-159">在訊息合約中使用自訂類型</span><span class="sxs-lookup"><span data-stu-id="ea9a6-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="ea9a6-160">每個個別訊息標頭與訊息本文部分，會針對使用訊息的服務合約，使用選擇的序列化引擎進行序列化 (轉變成 XML)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="ea9a6-161">預設的序列化引擎 `XmlFormatter` 能夠處理擁有資料合約的任何類型，不論是使用明確的方式 (藉由擁有 <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) 或隱含的方式 (藉由成為基本型別、擁有 <xref:System.SerializableAttribute?displayProperty=nameWithType> 等等)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="ea9a6-162">如需詳細資訊，請參閱[使用資料合約](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-162">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="ea9a6-163">在之前的範例中，`Operation` 和 `BankingTransactionData` 型別必須擁有資料合約，並且 `transactionDate` 是可序列化的，因為 <xref:System.DateTime> 是基本型別 (並且擁有隱含資料合約)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="ea9a6-164">但是，也有可能切換為不同的序列化引擎 `XmlSerializer`。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="ea9a6-165">如果您進行這類切換，就應該確定訊息標頭和本文部分所使用的所有型別都能夠使用 `XmlSerializer` 進行序列化。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="ea9a6-166">在訊息合約中使用陣列</span><span class="sxs-lookup"><span data-stu-id="ea9a6-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="ea9a6-167">您可以利用下列兩種方式在訊息合約中使用重複項目的陣列。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="ea9a6-168">第一個是在陣列上直接使用 <xref:System.ServiceModel.MessageHeaderAttribute> 或 <xref:System.ServiceModel.MessageBodyMemberAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="ea9a6-169">在此例中，整個陣列會序列化當做使用多個子項目的單一項目 (也就是單一標頭或單一本文部分)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="ea9a6-170">請考量下列範例中的類別。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="ea9a6-171">SOAP 標頭中的這個結果類似下列所示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-171">This results in SOAP headers is similar to the following.</span></span>  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 <span data-ttu-id="ea9a6-172">其替代方案是使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="ea9a6-173">在此例中，每個陣列項目會獨立序列化，所以每個陣列項目都有一個標頭，類似下列所示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="ea9a6-174">陣列項目的預設名稱為套用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="ea9a6-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute> 屬性繼承自 <xref:System.ServiceModel.MessageHeaderAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="ea9a6-176">它與非陣列屬性擁有相同的功能集合，例如，您可以使用與設定單一標頭相同的方式，設定標頭陣列的順序、名稱與命名空間。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="ea9a6-177">當您在陣列使用 `Order` 屬性時，就會套用至整個陣列。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="ea9a6-178">您可以將 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 只套用至陣列而不是集合上。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="ea9a6-179">在訊息合約中使用位元組陣列</span><span class="sxs-lookup"><span data-stu-id="ea9a6-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="ea9a6-180">當搭配非陣列屬性 (<xref:System.ServiceModel.MessageBodyMemberAttribute> 和 <xref:System.ServiceModel.MessageHeaderAttribute>) 使用位元組陣列時，就不會將位元組陣列視為陣列，而是視為在產生之 XML 中以 Base64 編碼之資料表示的特殊基本型別。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="ea9a6-181">當您搭配陣列屬性 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 使用位元組陣列時，結果會根據所使用的序列化程式而不同。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="ea9a6-182">當使用預設序列化程式時，陣列會以每個位元組的個別項目表示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="ea9a6-183">但是，當選取 `XmlSerializer` 時 (在服務合約使用 <xref:System.ServiceModel.XmlSerializerFormatAttribute>)，不論是否使用陣列或非陣列屬性，都會將位元組陣列視為 Base64 資料。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="ea9a6-184">簽署和加密部分訊息</span><span class="sxs-lookup"><span data-stu-id="ea9a6-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="ea9a6-185">訊息合約可以表示是否應該數位簽署與加密訊息的標頭和/或本文。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="ea9a6-186">藉由設定 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.MessageHeaderAttribute> 屬性 (Attribute) 的 <xref:System.ServiceModel.MessageBodyMemberAttribute> 屬性 (Property) 可以達到此目的。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="ea9a6-187">這個型別是 <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> 型別的列舉，並且可以設定為 <xref:System.Net.Security.ProtectionLevel.None> (無加密或簽章)、<xref:System.Net.Security.ProtectionLevel.Sign> (只有數位簽章) 或 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (同時使用加密和數位簽章)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="ea9a6-188">預設值為 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="ea9a6-189">若要讓這些安全性功能運作，您必須正確設定繫結與行為。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="ea9a6-190">如果沒有透過正確的組態 (例如，嘗試在不提供認證的情況下簽署訊息) 使用這些安全性功能，就會在驗證階段發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="ea9a6-191">針對訊息標頭，保護層級是針對每一個標頭個別決定的。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="ea9a6-192">對於訊息本文部分而言，可以將保護層級視為「最低保護層級」。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="ea9a6-193">無論有多少個本文部分，本文都只有一個保護層級。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="ea9a6-194">本文保護層級是由所有本文部分的最高層 <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> 屬性設定所決定。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="ea9a6-195">但是，您應該將每個本文部分的保護層級，設定為實際的最低必要保護層級。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="ea9a6-196">請考量下列程式碼範例中的類別。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-196">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 <span data-ttu-id="ea9a6-197">在這個範例中，`recordID` 標頭不受保護，`patientName` 已經過 `signed`，而 `SSN` 已經過加密並簽署。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="ea9a6-198">至少有一個本文部分 `medicalHistory` 已套用 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>，因此即使註解和診斷本文部分指定較低的保護層級，仍然會加密並簽署整個訊息本文。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="ea9a6-199">SOAP 動作</span><span class="sxs-lookup"><span data-stu-id="ea9a6-199">SOAP Action</span></span>  
 <span data-ttu-id="ea9a6-200">SOAP 與相關的 Web 服務標準會定義稱為 `Action` 的屬性，可能存在於每個已傳送的 SOAP 訊息中。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="ea9a6-201">作業的 <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> 屬性會控制此屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="ea9a6-202">SOAP 標頭屬性</span><span class="sxs-lookup"><span data-stu-id="ea9a6-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="ea9a6-203">SOAP 標準會定義下列可能存在於標頭的屬性：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
-   <span data-ttu-id="ea9a6-204">`Actor/Role` (在 SOAP 1.1 中為 `Actor`，在 SOAP 1.2 中為 `Role`)</span><span class="sxs-lookup"><span data-stu-id="ea9a6-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 <span data-ttu-id="ea9a6-205">`Actor` 或 `Role` 屬性會定義指定標頭想要之節點的統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="ea9a6-206">`MustUnderstand` 屬性會指定處理標頭的節點是否必須識別它。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="ea9a6-207">`Relay` 屬性會指定標頭是否要轉送至下游節點。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="ea9a6-208">除了 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 屬性外，`MustUnderstand` 不會對傳入訊息上的這些屬性執行任何處理，如本主題稍後＜訊息合約版本控制＞一節中所述。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-208">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="ea9a6-209">但是，它允許您依需要讀取和寫入這些屬性，如同下列所描述。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="ea9a6-210">當傳送訊息時，根據預設不會發出這些屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="ea9a6-211">變更這項作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-211">You can change this in two ways.</span></span> <span data-ttu-id="ea9a6-212">首先，您可以藉由變更 <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>、<xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> 和 <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> 屬性 (Property)，使用靜態方式將屬性 (Attribute) 設定為任何需要的值，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="ea9a6-213">(請注意並沒有 `Role` 屬性 (Property)；如果您使用 SOAP 1.2，設定 <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> 屬性 (Property) 會發出 `Role` 屬性 (Attribute))。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="ea9a6-214">第二種方法是透過程式碼以動態方式控制這些屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="ea9a6-215">您可以藉由將需要的標頭類型包裝在 <xref:System.ServiceModel.MessageHeader%601> 型別中 (請不要將此型別與非泛型版本混淆)，以及同時使用型別與 <xref:System.ServiceModel.MessageHeaderAttribute> 來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="ea9a6-216">然後可以在 <xref:System.ServiceModel.MessageHeader%601> 使用屬性 (Property) 以設定 SOAP 屬性 (Attribute)，如同下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 <span data-ttu-id="ea9a6-217">如果您同時使用動態與靜態控制機制，則靜態設定會用來當做預設，但稍後可以使用動態機制加以覆寫，如同下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="ea9a6-218">允許您使用動態屬性控制建立重複的標頭，如同下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="ea9a6-219">在接收端，只能在針對型別中標頭使用 <xref:System.ServiceModel.MessageHeader%601> 類別的情況下，才能讀取這些 SOAP 屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="ea9a6-220">您可以檢查 `Actor` 型別標頭的 `Relay`、`MustUnderstand` 或 <xref:System.ServiceModel.MessageHeader%601> 屬性 (Property)，探索所接收訊息的屬性 (Attribute) 設定。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="ea9a6-221">當接收到訊息然後傳回訊息時，SOAP 屬性設定只會為 <xref:System.ServiceModel.MessageHeader%601> 型別的標頭而往返。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="ea9a6-222">SOAP 本文部分的順序</span><span class="sxs-lookup"><span data-stu-id="ea9a6-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="ea9a6-223">在某些情況下，您會需要控制本文部分的順序。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="ea9a6-224">根據預設，本文項目的順序是依字母順序排列，但是可以透過 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 屬性控制。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="ea9a6-225">這個屬性與 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> 屬性有相同的語意，除了在繼承案例中的行為有所不同 (在訊息合約中，基底型別本文成員不會排序在衍生型別本文成員之前)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="ea9a6-226">如需詳細資訊，請參閱[資料成員順序](../../../../docs/framework/wcf/feature-details/data-member-order.md)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-226">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="ea9a6-227">在下列程式碼範例中，`amount` 通常會第一個出現 (因為依字母順序它是第一個)。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="ea9a6-228">但是，<xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> 屬性會將它放在第三位。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a><span data-ttu-id="ea9a6-229">訊息合約版本控制</span><span class="sxs-lookup"><span data-stu-id="ea9a6-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="ea9a6-230">您偶爾也會需要變更訊息合約。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="ea9a6-231">例如，新版應用程式可能會將額外的標頭新增至訊息中。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="ea9a6-232">然後當從新版應用程式傳送至舊版時，系統就必須處理額外的標頭；而從舊版傳送至新版時則要處理缺少標頭的狀況。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="ea9a6-233">下列規則會套用至版本控制標頭：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-233">The following rules apply for versioning headers:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ea9a6-234"> 不會拒絕處理缺少標頭的狀況—對應的成員則會保留其預設值。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-234"> does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ea9a6-235"> 也會忽略未預期的額外標頭。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-235"> also ignores unexpected extra headers.</span></span> <span data-ttu-id="ea9a6-236">這個規則的其中一個例外狀況是，如果在傳入 SOAP 訊息中的額外標頭將 `MustUnderstand` 屬性設定為 `true`，在這樣的情況下，因為無法處理必須解讀的標頭而會發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="ea9a6-237">訊息本文有類似的版本控制規則：缺少與額外的訊息本文部分都會受到忽略。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="ea9a6-238">繼承考量</span><span class="sxs-lookup"><span data-stu-id="ea9a6-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="ea9a6-239">只要基底型別也有訊息合約，訊息合約類型就可以繼承自其他類型。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="ea9a6-240">當使用繼承自其他訊息合約類型的訊息合約類型建立或存取訊息時，則適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
-   <span data-ttu-id="ea9a6-241">繼承階層架構中的所有訊息標頭都會收集在一起，以形成訊息標頭的完整集合。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
-   <span data-ttu-id="ea9a6-242">繼承階層架構中的所有訊息本文部分都會收集在一起，以形成完整的訊息本文。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="ea9a6-243">本文部分會根據常用排序規則 (根據 <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> 屬性，然後再根據字母順序) 進行排序，並且與它們在繼承階層架構中的位置無關。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="ea9a6-244">強烈建議不要在繼承樹狀結構之多個層級中發生訊息本文部分的情況下，使用訊息合約繼承。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="ea9a6-245">如果基底類別和衍生類別使用相同名稱定義標頭或本文部分，則會使用來自最底層類別的成員儲存該標頭或本文部分的值。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="ea9a6-246">請考量下列程式碼範例中的類別。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-246">Consider the classes in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 <span data-ttu-id="ea9a6-247">`PatientRecord` 類別描述使用稱為 `ID` 標頭的訊息。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="ea9a6-248">這個標頭對應至 `personID` 而不是 `patientID` 成員，因為已選擇最底層成員。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="ea9a6-249">因此，在此例中已經用不到 `patientID` 欄位。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="ea9a6-250">訊息本文包含之後跟隨 `diagnosis` 項目的 `patientName` 項目，因為這是依字母順序排列。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="ea9a6-251">請注意，該範例顯示強烈建議不要遵循的模式：基底與衍生訊息合約都有訊息本文部分。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="ea9a6-252">WSDL 考慮事項</span><span class="sxs-lookup"><span data-stu-id="ea9a6-252">WSDL Considerations</span></span>  
 <span data-ttu-id="ea9a6-253">當從使用訊息合約的服務產生 Web 服務描述語言 (WSDL) 合約時，重要的是並非所有訊息合約功能都會反應在產生的 WSDL 中。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="ea9a6-254">請考慮下列各點：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-254">Consider the following points:</span></span>  
  
-   <span data-ttu-id="ea9a6-255">WSDL 無法表達標頭陣列的概念。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="ea9a6-256">當使用 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 建立搭配標頭陣列的訊息時，產生的 WSDL 只會反應一個標頭而不是陣列。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
-   <span data-ttu-id="ea9a6-257">產生的 WSDL 文件可能不會反應某些保護層級資訊。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
-   <span data-ttu-id="ea9a6-258">WSDL 中產生的訊息類型名稱，與訊息合約類型的類別名稱相同。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
-   <span data-ttu-id="ea9a6-259">當您在多個作業中使用相同的訊息合約時，在 WSDL 文件中會產生多個訊息類型。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="ea9a6-260">藉由在後續使用時新增數字 "2"、"3" 等等，可以讓名稱具有唯一性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="ea9a6-261">當匯回 WSDL 時，會建立多個訊息合約類型，並且除了名稱以外都完全相同。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="ea9a6-262">SOAP 編碼考量</span><span class="sxs-lookup"><span data-stu-id="ea9a6-262">SOAP Encoding Considerations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ea9a6-263"> 可以讓您使用舊版的 XML SOAP 編碼樣式，但是不建議使用它。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-263"> allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="ea9a6-264">當使用這個樣式時 (藉由將套用至服務合約之 `Use` 的 `Encoded` 屬性設定為 <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>)，則適用下列其他考量：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
-   <span data-ttu-id="ea9a6-265">不支援訊息標頭，這表示屬性 <xref:System.ServiceModel.MessageHeaderAttribute> 和陣列屬性 <xref:System.ServiceModel.MessageHeaderArrayAttribute> 與 SOAP 編碼不相容。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
-   <span data-ttu-id="ea9a6-266">如果訊息合約並未包裝，也就是說如果屬性 <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> 設定為 `false`，訊息合約就只能有一個本文部分。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
-   <span data-ttu-id="ea9a6-267">要求訊息合約的包裝函式項目名稱必須符合作業名稱。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="ea9a6-268">對此請使用訊息合約的 `WrapperName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="ea9a6-269">回應訊息合約的包裝函式項目名稱必須與後置字元為 'Response' 的作業名稱相同。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="ea9a6-270">對此請使用訊息合約的 <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="ea9a6-271">SOAP 編碼會保留物件參考。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="ea9a6-272">例如，試想下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-272">For example, consider the following code.</span></span>  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 <span data-ttu-id="ea9a6-273">在使用 SOAP 編碼序列化訊息後，`changedFrom` 和 `changedTo` 並未包含專屬的 `p` 複本，而是指向 `changedBy` 項目內的複本。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="ea9a6-274">效能考量</span><span class="sxs-lookup"><span data-stu-id="ea9a6-274">Performance Considerations</span></span>  
 <span data-ttu-id="ea9a6-275">每個訊息標頭和訊息本文部分會各自獨立的序列化。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="ea9a6-276">因此，可以針對每個標頭和本文部分再次宣告相同的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="ea9a6-277">若要改善效能，特別是針對在網路上傳輸的訊息大小，可以將多個標頭和本文部分合併至單一標頭或本文部分。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="ea9a6-278">例如，不要使用下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ea9a6-278">For example, instead of the following code:</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 <span data-ttu-id="ea9a6-279">使用這段程式碼。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-279">Use this code.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="ea9a6-280">事件架構非同步和訊息合約</span><span class="sxs-lookup"><span data-stu-id="ea9a6-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="ea9a6-281">事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ea9a6-282">這麼做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="ea9a6-283">如果您要接收訊息物件做為 `Result` 屬性，並讓傳回的值做為該物件的屬性，則使用 `/messageContract` 命令選項。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="ea9a6-284">這會產生一個簽章，此簽章會將回應訊息傳回做為 `Result` 物件的 <xref:System.EventArgs> 屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="ea9a6-285">然後，所有的內部傳回值都成為回應訊息物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="ea9a6-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea9a6-286">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea9a6-286">See Also</span></span>  
 [<span data-ttu-id="ea9a6-287">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="ea9a6-287">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="ea9a6-288">設計與實作服務</span><span class="sxs-lookup"><span data-stu-id="ea9a6-288">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
