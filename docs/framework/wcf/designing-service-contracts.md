---
title: 設計服務合約
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 68ea866b736350b8a393d1f4788e4b08754e5ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785030"
---
# <a name="designing-service-contracts"></a><span data-ttu-id="fb763-102">設計服務合約</span><span class="sxs-lookup"><span data-stu-id="fb763-102">Designing Service Contracts</span></span>
<span data-ttu-id="fb763-103">本主題說明何謂服務合約、如何定義服務合約、能夠進行哪些作業 (以及對基礎訊息交換的影響)、使用哪些資料型別以及其他問題，協助您設計能夠適當滿足情況需求的作業。</span><span class="sxs-lookup"><span data-stu-id="fb763-103">This topic describes what service contracts are, how they are defined, what operations are available (and the implications for the underlying message exchanges), what data types are used, and other issues that help you design operations that satisfy the requirements of your scenario.</span></span>  
  
## <a name="creating-a-service-contract"></a><span data-ttu-id="fb763-104">建立服務合約</span><span class="sxs-lookup"><span data-stu-id="fb763-104">Creating a Service Contract</span></span>  
 <span data-ttu-id="fb763-105">服務會公開作業的數量。</span><span class="sxs-lookup"><span data-stu-id="fb763-105">Services expose a number of operations.</span></span> <span data-ttu-id="fb763-106">在 Windows Communication Foundation (WCF) 應用程式定義的作業所建立的方法，並將其與標示<xref:System.ServiceModel.OperationContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="fb763-106">In Windows Communication Foundation (WCF) applications, define the operations by creating a method and marking it with the <xref:System.ServiceModel.OperationContractAttribute> attribute.</span></span> <span data-ttu-id="fb763-107">接著，若要建立服務合約，請在以 <xref:System.ServiceModel.ServiceContractAttribute> 屬性標記的介面內宣告作業，或是在以相同屬性標記的類別中定義作業，藉此將作業分組。</span><span class="sxs-lookup"><span data-stu-id="fb763-107">Then, to create a service contract, group together your operations, either by declaring them within an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute, or by defining them in a class marked with the same attribute.</span></span> <span data-ttu-id="fb763-108">(如需基本範例，請參閱[How to:定義服務合約](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。)</span><span class="sxs-lookup"><span data-stu-id="fb763-108">(For a basic example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)</span></span>  
  
 <span data-ttu-id="fb763-109">沒有任何方法<xref:System.ServiceModel.OperationContractAttribute>屬性不是服務作業並不會公開 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fb763-109">Any methods that do not have a <xref:System.ServiceModel.OperationContractAttribute> attribute are not service operations and are not exposed by WCF services.</span></span>  
  
 <span data-ttu-id="fb763-110">本主題將說明設計服務合約時的決策點：</span><span class="sxs-lookup"><span data-stu-id="fb763-110">This topic describes the following decision points when designing a service contract:</span></span>  
  
- <span data-ttu-id="fb763-111">使用類別或介面。</span><span class="sxs-lookup"><span data-stu-id="fb763-111">Whether to use classes or interfaces.</span></span>  
  
- <span data-ttu-id="fb763-112">如何指定要交換的資料型別。</span><span class="sxs-lookup"><span data-stu-id="fb763-112">How to specify the data types you want to exchange.</span></span>  
  
- <span data-ttu-id="fb763-113">您可以使用的交換模式類型。</span><span class="sxs-lookup"><span data-stu-id="fb763-113">The types of exchange patterns you can use.</span></span>  
  
- <span data-ttu-id="fb763-114">是否可以在合約中加入明確的安全性需求。</span><span class="sxs-lookup"><span data-stu-id="fb763-114">Whether you can make explicit security requirements part of the contract.</span></span>  
  
- <span data-ttu-id="fb763-115">作業輸入和輸出的限制。</span><span class="sxs-lookup"><span data-stu-id="fb763-115">The restrictions for operation inputs and outputs.</span></span>  
  
## <a name="classes-or-interfaces"></a><span data-ttu-id="fb763-116">類別或介面</span><span class="sxs-lookup"><span data-stu-id="fb763-116">Classes or Interfaces</span></span>  
 <span data-ttu-id="fb763-117">類別和介面，代表功能的群組，因此，兩者都可以用來定義 WCF 服務合約。</span><span class="sxs-lookup"><span data-stu-id="fb763-117">Both classes and interfaces represent a grouping of functionality and, therefore, both can be used to define a WCF service contract.</span></span> <span data-ttu-id="fb763-118">不過，建議您使用介面，因為介面會直接建立服務合約的模型。</span><span class="sxs-lookup"><span data-stu-id="fb763-118">However, it is recommended that you use interfaces because they directly model service contracts.</span></span> <span data-ttu-id="fb763-119">在沒有實作的情況下，介面的功能不過就是定義包含特定簽章的方法群組。</span><span class="sxs-lookup"><span data-stu-id="fb763-119">Without an implementation, interfaces do no more than define a grouping of methods with certain signatures.</span></span> <span data-ttu-id="fb763-120">實作服務合約介面，並已實作的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fb763-120">Implement a service contract interface and you have implemented a WCF service.</span></span>  
  
 <span data-ttu-id="fb763-121">Managed 介面的所有優勢都會套用至服務合約介面：</span><span class="sxs-lookup"><span data-stu-id="fb763-121">All the benefits of managed interfaces apply to service contract interfaces:</span></span>  
  
- <span data-ttu-id="fb763-122">服務合約介面可擴充任意數目的其他服務合約介面。</span><span class="sxs-lookup"><span data-stu-id="fb763-122">Service contract interfaces can extend any number of other service contract interfaces.</span></span>  
  
- <span data-ttu-id="fb763-123">單一類別可藉由實作服務合約介面的方式，實作任意數目的服務合約。</span><span class="sxs-lookup"><span data-stu-id="fb763-123">A single class can implement any number of service contracts by implementing those service contract interfaces.</span></span>  
  
- <span data-ttu-id="fb763-124">您可以藉由變更介面實作的方式修改服務合約的實作，同時讓服務合約維持不變。</span><span class="sxs-lookup"><span data-stu-id="fb763-124">You can modify the implementation of a service contract by changing the interface implementation, while the service contract remains the same.</span></span>  
  
- <span data-ttu-id="fb763-125">您只要實作舊介面和新介面，就能設定服務的版本。</span><span class="sxs-lookup"><span data-stu-id="fb763-125">You can version your service by implementing the old interface and the new one.</span></span> <span data-ttu-id="fb763-126">舊的用戶端可連接到原始版本，而新的用戶端則可連接到新版本。</span><span class="sxs-lookup"><span data-stu-id="fb763-126">Old clients connect to the original version, while newer clients can connect to the newer version.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb763-127">繼承自其他服務合約介面時，無法覆寫如名稱或命名空間這類作業屬性。</span><span class="sxs-lookup"><span data-stu-id="fb763-127">When inheriting from other service contract interfaces, you cannot override operation properties, such as the name or namespace.</span></span> <span data-ttu-id="fb763-128">如果您嘗試這樣做，則會在目前的服務合約中建立新作業。</span><span class="sxs-lookup"><span data-stu-id="fb763-128">If you attempt to do so, you create a new operation in the current service contract.</span></span>  
  
 <span data-ttu-id="fb763-129">如需使用介面來建立服務合約的範例，請參閱[How to:建立服務合約介面](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-129">For an example of using an interface to create a service contract, see [How to: Create a Service with a Contract Interface](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).</span></span>  
  
 <span data-ttu-id="fb763-130">不過，您可以使用類別定義服務合約，同時實作該合約。</span><span class="sxs-lookup"><span data-stu-id="fb763-130">You can, however, use a class to define a service contract and implement that contract at the same time.</span></span> <span data-ttu-id="fb763-131">直接將 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 分別套用至類別及該類別上的方法，藉此建立服務的好處在於速度和單純性。</span><span class="sxs-lookup"><span data-stu-id="fb763-131">The advantage of creating your services by applying <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> directly to the class and the methods on the class, respectively, is speed and simplicity.</span></span> <span data-ttu-id="fb763-132">而缺點則在於，Managed 類別不支援多重繼承，因此一次只能實作一個服務合約。</span><span class="sxs-lookup"><span data-stu-id="fb763-132">The disadvantages are that managed classes do not support multiple inheritance, and as a result they can only implement one service contract at a time.</span></span> <span data-ttu-id="fb763-133">此外，對類別或方法簽章所做的任何修改，都會修改該服務的公開合約，如此可能會讓未修改的用戶端無法使用您的服務。</span><span class="sxs-lookup"><span data-stu-id="fb763-133">In addition, any modification to the class or method signatures modifies the public contract for that service, which can prevent unmodified clients from using your service.</span></span> <span data-ttu-id="fb763-134">如需詳細資訊，請參閱 < [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-134">For more information, see [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md).</span></span>  
  
 <span data-ttu-id="fb763-135">如需使用類別來建立服務合約和實作一次的範例，請參閱[How to:使用合約類別，建立服務](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-135">For an example that uses a class to create a service contract and implements it at the same time, see [How to: Create a Service with a Contract Class](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).</span></span>  
  
 <span data-ttu-id="fb763-136">至此您應了解使用介面和類別定義服務合約的差異。</span><span class="sxs-lookup"><span data-stu-id="fb763-136">At this point, you should understand the difference between defining your service contract by using an interface and by using a class.</span></span> <span data-ttu-id="fb763-137">下一步將要決定可在服務及其用戶端之間來回傳遞的資料。</span><span class="sxs-lookup"><span data-stu-id="fb763-137">The next step is deciding what data can be passed back and forth between a service and its clients.</span></span>  
  
## <a name="parameters-and-return-values"></a><span data-ttu-id="fb763-138">參數和傳回值</span><span class="sxs-lookup"><span data-stu-id="fb763-138">Parameters and Return Values</span></span>  
 <span data-ttu-id="fb763-139">每一項作業都有傳回值和參數，即使它們是 `void`。</span><span class="sxs-lookup"><span data-stu-id="fb763-139">Each operation has a return value and a parameter, even if these are `void`.</span></span> <span data-ttu-id="fb763-140">不過與區域方法不同的是，區域方法可以用來在物件之間傳遞物件的參考，服務作業則不會傳遞物件的參考，</span><span class="sxs-lookup"><span data-stu-id="fb763-140">However, unlike a local method, in which you can pass references to objects from one object to another, service operations do not pass references to objects.</span></span> <span data-ttu-id="fb763-141">而是傳遞物件的複本。</span><span class="sxs-lookup"><span data-stu-id="fb763-141">Instead, they pass copies of the objects.</span></span>  
  
 <span data-ttu-id="fb763-142">這點相當重要，因為參數或傳回值使用的每一個型別都必須可序列化，也就是說，必須能夠將該型別的物件轉換成位元組資料流，以及從位元組資料流轉換成物件。</span><span class="sxs-lookup"><span data-stu-id="fb763-142">This is significant because each type used in a parameter or return value must be serializable; that is, it must be possible to convert an object of that type into a stream of bytes and from a stream of bytes into an object.</span></span>  
  
 <span data-ttu-id="fb763-143">基本型別預設為可序列化，.NET Framework 中的許多型別也是如此。</span><span class="sxs-lookup"><span data-stu-id="fb763-143">Primitive types are serializable by default, as are many types in the .NET Framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb763-144">作業簽章中參數名稱的值是合約的一部分，而且必須區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fb763-144">The value of the parameter names in the operation signature are part of the contract and are case sensitive.</span></span> <span data-ttu-id="fb763-145">如果您要在本機上使用相同的參數名稱，但是要修改已發行中繼資料的名稱，請參閱 <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fb763-145">If you want to use the same parameter name locally but modify the name in the published metadata, see the <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.</span></span>  
  
#### <a name="data-contracts"></a><span data-ttu-id="fb763-146">資料合約</span><span class="sxs-lookup"><span data-stu-id="fb763-146">Data Contracts</span></span>  
 <span data-ttu-id="fb763-147">服務導向應用程式，例如 Windows Communication Foundation (WCF) 應用程式被設計來與最多的 Microsoft 和非 Microsoft 平台上的用戶端應用程式交互操作。</span><span class="sxs-lookup"><span data-stu-id="fb763-147">Service-oriented applications like Windows Communication Foundation (WCF) applications are designed to interoperate with the widest possible number of client applications on both Microsoft and non-Microsoft platforms.</span></span> <span data-ttu-id="fb763-148">為了盡可能提供最廣泛的互通性，建議您以 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性標記型別來建立資料合約，這是服務合約中描述服務作業所交換資料的部分。</span><span class="sxs-lookup"><span data-stu-id="fb763-148">For the widest possible interoperability, it is recommended that you mark your types with the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create a data contract, which is the portion of the service contract that describes the data that your service operations exchange.</span></span>  
  
 <span data-ttu-id="fb763-149">資料合約為 opt-in 式合約：除非您明確套用資料合約屬性，則會序列化任何型別或資料成員。</span><span class="sxs-lookup"><span data-stu-id="fb763-149">Data contracts are opt-in style contracts: No type or data member is serialized unless you explicitly apply the data contract attribute.</span></span> <span data-ttu-id="fb763-150">資料合約不相關的 managed 程式碼的存取範圍：私用資料成員可以序列化，並傳送至可公開存取的其他位置。</span><span class="sxs-lookup"><span data-stu-id="fb763-150">Data contracts are unrelated to the access scope of the managed code: Private data members can be serialized and sent elsewhere to be accessed publicly.</span></span> <span data-ttu-id="fb763-151">(如資料合約的基本範例，請參閱[How to:建立類別或結構的基本資料合約](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md)。)WCF 會處理啟用作業的功能的基礎 SOAP 訊息的定義，以及您的資料類型的序列化，傳入和傳出訊息本文。</span><span class="sxs-lookup"><span data-stu-id="fb763-151">(For a basic example of a data contract, see [How to: Create a Basic Data Contract for a Class or Structure](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF handles the definition of the underlying SOAP messages that enable the operation's functionality as well as the serialization of your data types into and out of the body of the messages.</span></span> <span data-ttu-id="fb763-152">只要資料型別可以序列化，在設計您的作業時，就不需要考慮基礎訊息交換的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="fb763-152">As long as your data types are serializable, you do not need to think about the underlying message exchange infrastructure when designing your operations.</span></span>  
  
 <span data-ttu-id="fb763-153">雖然典型 WCF 應用程式會使用<xref:System.Runtime.Serialization.DataContractAttribute>和<xref:System.Runtime.Serialization.DataMemberAttribute>屬性來建立資料合約的作業，您可以使用其他序列化機制。</span><span class="sxs-lookup"><span data-stu-id="fb763-153">Although the typical WCF application uses the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to create data contracts for operations, you can use other serialization mechanisms.</span></span> <span data-ttu-id="fb763-154">標準 <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> 和 <xref:System.Xml.Serialization.IXmlSerializable> 機制的功能都在於處理資料型別序列化為基礎 SOAP 訊息，以便在應用程式之間傳輸的過程。</span><span class="sxs-lookup"><span data-stu-id="fb763-154">The standard <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> and <xref:System.Xml.Serialization.IXmlSerializable> mechanisms all work to handle the serialization of your data types into the underlying SOAP messages that carry them from one application to another.</span></span> <span data-ttu-id="fb763-155">如果您的資料型別需要特殊支援，可採用更多序列化策略。</span><span class="sxs-lookup"><span data-stu-id="fb763-155">You can employ more serialization strategies if your data types require special support.</span></span> <span data-ttu-id="fb763-156">如需有關 WCF 應用程式中的資料類型的序列化選擇的詳細資訊，請參閱[Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-156">For more information about the choices for serialization of data types in WCF applications, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span>  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a><span data-ttu-id="fb763-157">將參數和傳回值對應到訊息交換</span><span class="sxs-lookup"><span data-stu-id="fb763-157">Mapping Parameters and Return Values to Message Exchanges</span></span>  
 <span data-ttu-id="fb763-158">服務作業是由來回傳輸應用程式資料的基礎 SOAP 訊息交換所支援，此外還包括應用程式支援特定標準的安全性、交易和工作階段相關功能時所需的資料。</span><span class="sxs-lookup"><span data-stu-id="fb763-158">Service operations are supported by an underlying exchange of SOAP messages that transfer application data back and forth, in addition to the data required by the application to support certain standard security, transaction, and session-related features.</span></span> <span data-ttu-id="fb763-159">因為這種情況，服務作業的簽章會指定基礎*訊息交換模式*(MEP)，可支援資料傳輸，以及作業所需的功能。</span><span class="sxs-lookup"><span data-stu-id="fb763-159">Because this is the case, the signature of a service operation dictates a certain underlying *message exchange pattern* (MEP) that can support the data transfer and the features an operation requires.</span></span> <span data-ttu-id="fb763-160">您可以指定三種模式中的 WCF 程式設計模型： 要求/回覆、 單向和雙工訊息模式。</span><span class="sxs-lookup"><span data-stu-id="fb763-160">You can specify three patterns in the WCF programming model: request/reply, one-way, and duplex message patterns.</span></span>  
  
##### <a name="requestreply"></a><span data-ttu-id="fb763-161">要求/回覆</span><span class="sxs-lookup"><span data-stu-id="fb763-161">Request/Reply</span></span>  
 <span data-ttu-id="fb763-162">要求/回覆模式是要求傳送者 (用戶端應用程式) 接收與要求相關聯之回覆的模式。</span><span class="sxs-lookup"><span data-stu-id="fb763-162">A request/reply pattern is one in which a request sender (a client application) receives a reply with which the request is correlated.</span></span> <span data-ttu-id="fb763-163">這是預設的 MEP，因為它支援將一個或多個參數傳遞至作業並將傳回值回傳給呼叫端的作業。</span><span class="sxs-lookup"><span data-stu-id="fb763-163">This is the default MEP because it supports an operation in which one or more parameters are passed to the operation and a return value is passed back to the caller.</span></span> <span data-ttu-id="fb763-164">例如，下列 C# 程式碼範例示範基本的服務作業，此作業會取得一個字串並傳回一個字串。</span><span class="sxs-lookup"><span data-stu-id="fb763-164">For example, the following C# code example shows a basic service operation that takes one string and returns a string.</span></span>  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 <span data-ttu-id="fb763-165">以下為 Visual Basic 程式碼的對等用法。</span><span class="sxs-lookup"><span data-stu-id="fb763-165">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 <span data-ttu-id="fb763-166">這個作業簽章表示基礎訊息交換的形式。</span><span class="sxs-lookup"><span data-stu-id="fb763-166">This operation signature dictates the form of underlying message exchange.</span></span> <span data-ttu-id="fb763-167">如果沒有關聯性存在，WCF 無法判斷哪一項作業的傳回值適用。</span><span class="sxs-lookup"><span data-stu-id="fb763-167">If no correlation existed, WCF cannot determine for which operation the return value is intended.</span></span>  
  
 <span data-ttu-id="fb763-168">請注意，除非您指定不同的基礎訊息模式，甚至是傳回服務作業`void`(`Nothing` Visual Basic 中) 會要求/回覆訊息交換。</span><span class="sxs-lookup"><span data-stu-id="fb763-168">Note that unless you specify a different underlying message pattern, even service operations that return `void` (`Nothing` in Visual Basic) are request/reply message exchanges.</span></span> <span data-ttu-id="fb763-169">作業的結果會是：除非用戶端未同步叫用作業，否則用戶端會停止處理，直到收到傳回訊息為止 (即使一般情況下該訊息會是空的)。</span><span class="sxs-lookup"><span data-stu-id="fb763-169">The result for your operation is that unless a client invokes the operation asynchronously, the client stops processing until the return message is received, even though that message is empty in the normal case.</span></span> <span data-ttu-id="fb763-170">下列 C# 程式碼範例示範一個作業，此作業會在用戶端收到空的訊息回應之後才傳回。</span><span class="sxs-lookup"><span data-stu-id="fb763-170">The following C# code example shows an operation that does not return until the client has received an empty message in response.</span></span>  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="fb763-171">以下為 Visual Basic 程式碼的對等用法。</span><span class="sxs-lookup"><span data-stu-id="fb763-171">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="fb763-172">如果作業的執行時間較長，前一個範例可能會降低用戶端效能與回應，但是即使要求/回覆作業傳回 `void`，這項作業仍有許多優點。</span><span class="sxs-lookup"><span data-stu-id="fb763-172">The preceding example can slow client performance and responsiveness if the operation takes a long time to perform, but there are advantages to request/reply operations even when they return `void`.</span></span> <span data-ttu-id="fb763-173">最明顯的優點就是可在回應訊息中傳回 SOAP 錯誤，表示通訊或處理過程中發生了某種服務相關的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="fb763-173">The most obvious one is that SOAP faults can be returned in the response message, which indicates that some service-related error condition has occurred, whether in communication or processing.</span></span> <span data-ttu-id="fb763-174">服務合約中指出的 SOAP 錯誤會做為 <xref:System.ServiceModel.FaultException%601> 物件傳遞至用戶端應用程式，其中型別參數為服務合約中指定的型別。</span><span class="sxs-lookup"><span data-stu-id="fb763-174">SOAP faults that are specified in a service contract are passed to the client application as a <xref:System.ServiceModel.FaultException%601> object, where the type parameter is the type specified in the service contract.</span></span> <span data-ttu-id="fb763-175">這簡化通知用戶端錯誤狀況中 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="fb763-175">This makes notifying clients about error conditions in WCF services easy.</span></span> <span data-ttu-id="fb763-176">如需例外狀況、 SOAP 錯誤和錯誤處理的詳細資訊，請參閱[指定及處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-176">For more information about exceptions, SOAP faults, and error handling, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span> <span data-ttu-id="fb763-177">若要查看要求/回覆服務和用戶端的範例，請參閱[How to:建立要求-回覆合約](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-177">To see an example of a request/reply service and client, see [How to: Create a Request-Reply Contract](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="fb763-178">如需要求-回覆模式問題的詳細資訊，請參閱 <<c0> [ 要求-回覆服務](../../../docs/framework/wcf/feature-details/request-reply-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-178">For more information about issues with the request-reply pattern, see [Request-Reply Services](../../../docs/framework/wcf/feature-details/request-reply-services.md).</span></span>  
  
##### <a name="one-way"></a><span data-ttu-id="fb763-179">單向</span><span class="sxs-lookup"><span data-stu-id="fb763-179">One-way</span></span>  
 <span data-ttu-id="fb763-180">如果 WCF 服務應用程式的用戶端不需要等待作業完成，而且不會處理 SOAP 錯誤，此作業可以指定單向訊息模式。</span><span class="sxs-lookup"><span data-stu-id="fb763-180">If the client of a WCF service application should not wait for the operation to complete and does not process SOAP faults, the operation can specify a one-way message pattern.</span></span> <span data-ttu-id="fb763-181">單向作業則是用戶端叫用作業並繼續處理之後，WCF 將訊息寫入到網路。</span><span class="sxs-lookup"><span data-stu-id="fb763-181">A one-way operation is one in which a client invokes an operation and continues processing after WCF writes the message to the network.</span></span> <span data-ttu-id="fb763-182">通常這表示，除非傳出訊息中傳送的資料相當大，否則用戶端幾乎會立即繼續執行 (除非傳送資料時發生錯誤)。</span><span class="sxs-lookup"><span data-stu-id="fb763-182">Typically this means that unless the data being sent in the outbound message is extremely large the client continues running almost immediately (unless there is an error sending the data).</span></span> <span data-ttu-id="fb763-183">這種類型的訊息交換模式支援用戶端與伺服器應用程式之間，類似事件的行為。</span><span class="sxs-lookup"><span data-stu-id="fb763-183">This type of message exchange pattern supports event-like behavior from a client to a service application.</span></span>  
  
 <span data-ttu-id="fb763-184">若訊息交換僅包含送出訊息但未收到任何訊息，則不支援指定 `void` 以外傳回值的服務作業；在此情況下，會擲回 <xref:System.InvalidOperationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fb763-184">A message exchange in which one message is sent and none are received cannot support a service operation that specifies a return value other than `void`; in this case an <xref:System.InvalidOperationException> exception is thrown.</span></span>  
  
 <span data-ttu-id="fb763-185">沒有傳回訊息也就表示，可能未傳回任何 SOAP 錯誤，指出處理或通訊中發生任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="fb763-185">No return message also means that there can be no SOAP fault returned to indicate any errors in processing or communication.</span></span> <span data-ttu-id="fb763-186">(單向作業的通訊錯誤資訊需要雙工訊息交換模式)。</span><span class="sxs-lookup"><span data-stu-id="fb763-186">(Communicating error information when operations are one-way operations requires a duplex message exchange pattern.)</span></span>  
  
 <span data-ttu-id="fb763-187">若要為傳回 `void` 的作業指定單向訊息交換，請將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設定為 `true`，如下列 C# 程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="fb763-187">To specify a one-way message exchange for an operation that returns `void`, set the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true`, as in the following C# code example.</span></span>  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 <span data-ttu-id="fb763-188">以下為 Visual Basic 程式碼的對等用法。</span><span class="sxs-lookup"><span data-stu-id="fb763-188">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 <span data-ttu-id="fb763-189">這個方法與之前的要求/回覆範例相同，但是將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設為 `true` 表示即使方法相同，服務作業仍不會送出傳回訊息，而且用戶端會在傳出訊息送至通道層之後立即傳回。</span><span class="sxs-lookup"><span data-stu-id="fb763-189">This method is identical to the preceding request/reply example, but setting the <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> property to `true` means that although the method is identical, the service operation does not send a return message and clients return immediately once the outbound message has been handed to the channel layer.</span></span> <span data-ttu-id="fb763-190">如需範例，請參閱[如何：建立單向合約](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-190">For an example, see [How to: Create a One-Way Contract](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md).</span></span> <span data-ttu-id="fb763-191">如需有關單向模式的詳細資訊，請參閱 <<c0> [ 單向服務](../../../docs/framework/wcf/feature-details/one-way-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-191">For more information about the one-way pattern, see [One-Way Services](../../../docs/framework/wcf/feature-details/one-way-services.md).</span></span>  
  
##### <a name="duplex"></a><span data-ttu-id="fb763-192">雙工</span><span class="sxs-lookup"><span data-stu-id="fb763-192">Duplex</span></span>  
 <span data-ttu-id="fb763-193">雙工模式的特性在於同時擁有服務和用戶端的能力，可使用單向或要求/回覆傳訊方式分別傳送訊息給彼此。</span><span class="sxs-lookup"><span data-stu-id="fb763-193">A duplex pattern is characterized by the ability of both the service and the client to send messages to each other independently whether using one-way or request/reply messaging.</span></span> <span data-ttu-id="fb763-194">這種雙向通訊的方式對於需要直接與用戶端通訊，或是提供非同步經驗給訊息交換之任一端 (包括類似事件的行為) 的服務而言相當實用。</span><span class="sxs-lookup"><span data-stu-id="fb763-194">This form of two-way communication is useful for services that must communicate directly to the client or for providing an asynchronous experience to either side of a message exchange, including event-like behavior.</span></span>  
  
 <span data-ttu-id="fb763-195">由於與用戶單通訊時的額外機制，雙工模式會比要求/回覆或單向模式稍微複雜一些。</span><span class="sxs-lookup"><span data-stu-id="fb763-195">The duplex pattern is slightly more complex than the request/reply or one-way patterns because of the additional mechanism for communicating with the client.</span></span>  
  
 <span data-ttu-id="fb763-196">若要設計雙工合約，您必須同時設計回呼合約，並指派回呼合約的類型給標記服務合約之 <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> 屬性 (Attribute) 的 <xref:System.ServiceModel.ServiceContractAttribute> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="fb763-196">To design a duplex contract, you must also design a callback contract and assign the type of that callback contract to the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> property of the <xref:System.ServiceModel.ServiceContractAttribute> attribute that marks your service contract.</span></span>  
  
 <span data-ttu-id="fb763-197">若要實作雙工模式，您必須建立另一個介面，其中包含在用戶端上呼叫的方法宣告。</span><span class="sxs-lookup"><span data-stu-id="fb763-197">To implement a duplex pattern, you must create a second interface that contains the method declarations that are called on the client.</span></span>  
  
 <span data-ttu-id="fb763-198">如需建立服務，以及存取該服務的用戶端的範例，請參閱[How to:建立雙工合約](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)和[How to:使用雙工合約存取服務](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-198">For an example of creating a service, and a client that accesses that service, see [How to: Create a Duplex Contract](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) and [How to: Access Services with a Duplex Contract](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md).</span></span> <span data-ttu-id="fb763-199">如需實用範例，請參閱 <<c0> [ 雙工](../../../docs/framework/wcf/samples/duplex.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-199">For a working sample, see [Duplex](../../../docs/framework/wcf/samples/duplex.md).</span></span> <span data-ttu-id="fb763-200">如需有關使用雙工合約的問題的詳細資訊，請參閱[雙工服務](../../../docs/framework/wcf/feature-details/duplex-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-200">For more information about issues using duplex contracts, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="fb763-201">當服務收到雙工訊息時，會查看該傳入訊息中的 `ReplyTo` 項目，以判斷傳送回覆的位置。</span><span class="sxs-lookup"><span data-stu-id="fb763-201">When a service receives a duplex message, it looks at the `ReplyTo` element in that incoming message to determine where to send the reply.</span></span> <span data-ttu-id="fb763-202">如果用來接收訊息的通道不安全，那麼未受信任的用戶端可能會傳送惡意訊息，其中包含目標電腦的 `ReplyTo`，而導致該目標電腦拒絕服務 (DOS)。</span><span class="sxs-lookup"><span data-stu-id="fb763-202">If the channel that is used to receive the message is not secured, then an untrusted client could send a malicious message with a target machine's `ReplyTo`, leading to a denial of service (DOS) of that target machine.</span></span>  
  
##### <a name="out-and-ref-parameters"></a><span data-ttu-id="fb763-203">Out 和 Ref 參數</span><span class="sxs-lookup"><span data-stu-id="fb763-203">Out and Ref Parameters</span></span>  
 <span data-ttu-id="fb763-204">在大部分情況下，您可以使用`in`參數 (`ByVal` Visual Basic 中) 及`out`並`ref`參數 (`ByRef` Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="fb763-204">In most cases, you can use `in` parameters (`ByVal` in Visual Basic) and `out` and `ref` parameters (`ByRef` in Visual Basic).</span></span> <span data-ttu-id="fb763-205">由於 `out` 和 `ref` 這兩個參數都表示資料是從作業傳回，因此即使作業簽章 (如下所示) 傳回 `void`，仍會指定必須要求/回覆作業。</span><span class="sxs-lookup"><span data-stu-id="fb763-205">Because both `out` and `ref` parameters indicate that data is returned from an operation, an operation signature such as the following specifies that a request/reply operation is required even though the operation signature returns `void`.</span></span>  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 <span data-ttu-id="fb763-206">以下為 Visual Basic 程式碼的對等用法。</span><span class="sxs-lookup"><span data-stu-id="fb763-206">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 <span data-ttu-id="fb763-207">唯一的例外狀況是簽章擁有特殊結構的情況。</span><span class="sxs-lookup"><span data-stu-id="fb763-207">The only exceptions are those cases in which your signature has a particular structure.</span></span> <span data-ttu-id="fb763-208">例如，只有在用來宣告作業的方法傳回 <xref:System.ServiceModel.NetMsmqBinding> 時，才能使用 `void` 繫結與用戶端通訊；可能不會有輸出值，無論是傳回值或是 `ref` 或 `out` 參數。</span><span class="sxs-lookup"><span data-stu-id="fb763-208">For example, you can use the <xref:System.ServiceModel.NetMsmqBinding> binding to communicate with clients only if the method used to declare an operation returns `void`; there can be no output value, whether it is a return value, `ref`, or `out` parameter.</span></span>  
  
 <span data-ttu-id="fb763-209">此外，使用 `out` 或 `ref` 參數會要求作業擁有基礎回應訊息，以便攜回修改的物件。</span><span class="sxs-lookup"><span data-stu-id="fb763-209">In addition, using `out` or `ref` parameters requires that the operation have an underlying response message to carry back the modified object.</span></span> <span data-ttu-id="fb763-210">如果您的作業是單向作業，則會在執行階段擲回 <xref:System.InvalidOperationException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fb763-210">If your operation is a one-way operation, an <xref:System.InvalidOperationException> exception is thrown at runtime.</span></span>  
  
### <a name="specify-message-protection-level-on-the-contract"></a><span data-ttu-id="fb763-211">指定合約上的訊息保護層級</span><span class="sxs-lookup"><span data-stu-id="fb763-211">Specify Message Protection Level on the Contract</span></span>  
 <span data-ttu-id="fb763-212">設計合約時，您還必須決定實作合約之服務的訊息保護層級。</span><span class="sxs-lookup"><span data-stu-id="fb763-212">When designing your contract, you must also decide the message protection level of services that implement your contract.</span></span> <span data-ttu-id="fb763-213">只有在訊息安全性套用至合約端點的繫結中時，才需要這樣做。</span><span class="sxs-lookup"><span data-stu-id="fb763-213">This is necessary only if message security is applied to the binding in the contract's endpoint.</span></span> <span data-ttu-id="fb763-214">如果繫結的安全性已關閉 (也就是說，如果提供繫結的系統將 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> 設為 <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType> 這個值)，那麼您就不必決定合約的訊息保護層級。</span><span class="sxs-lookup"><span data-stu-id="fb763-214">If the binding has security turned off (that is, if the system-provided binding sets the <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> to the value <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) then you do not have to decide on the message protection level for the contract.</span></span> <span data-ttu-id="fb763-215">在大部分情況下，系統所提供已套用訊息層級安全性的繫結會提供足夠的保護層級，因此您不需要考慮每項作業或每個訊息的保護層級。</span><span class="sxs-lookup"><span data-stu-id="fb763-215">In most cases, system-provided bindings with message-level security applied provide a sufficient protection level and you do not have to consider the protection level for each operation or for each message.</span></span>  
  
 <span data-ttu-id="fb763-216">保護層級是一個值，會指定支援服務的訊息 (或訊息部分) 為經過簽署、經過簽署且加密，或是已傳送但未包含簽章或加密。</span><span class="sxs-lookup"><span data-stu-id="fb763-216">The protection level is a value that specifies whether the messages (or message parts) that support a service are signed, signed and encrypted, or sent without signatures or encryption.</span></span> <span data-ttu-id="fb763-217">可在各種範圍設定的保護層級：在服務層級，針對特定的作業，該作業或訊息部分內的訊息。</span><span class="sxs-lookup"><span data-stu-id="fb763-217">The protection level can be set at various scopes: At the service level, for a particular operation, for a message within that operation, or a message part.</span></span> <span data-ttu-id="fb763-218">設定於某一範圍的值會變成更小範圍的預設值，除非有明確覆寫的值。</span><span class="sxs-lookup"><span data-stu-id="fb763-218">Values set at one scope become the default value for smaller scopes unless explicitly overridden.</span></span> <span data-ttu-id="fb763-219">如果繫結組態無法提供合約所需的最小保護層級，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fb763-219">If a binding configuration cannot provide the required minimum protection level for the contract, an exception is thrown.</span></span> <span data-ttu-id="fb763-220">而如果合約上未明確設定保護層級值，繫結組態就會控制所有訊息的保護層級 (如果繫結具備訊息安全性的話)。</span><span class="sxs-lookup"><span data-stu-id="fb763-220">And when no protection level values are explicitly set on the contract, the binding configuration controls the protection level for all messages if the binding has message security.</span></span> <span data-ttu-id="fb763-221">這是預設行為。</span><span class="sxs-lookup"><span data-stu-id="fb763-221">This is the default behavior.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb763-222">決定是否將合約的各種範圍明確設定為低於 <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> 的完整保護層級，通常是犧牲某種程度的安全性換取較高效能的決策。</span><span class="sxs-lookup"><span data-stu-id="fb763-222">Deciding whether to explicitly set various scopes of a contract to less than the full protection level of <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> is generally a decision that trades some degree of security for increased performance.</span></span> <span data-ttu-id="fb763-223">在這種情況下，您的決定必須包含作業及其交換的資料值。</span><span class="sxs-lookup"><span data-stu-id="fb763-223">In these cases, your decisions must revolve around your operations and the value of the data they exchange.</span></span> <span data-ttu-id="fb763-224">如需詳細資訊，請參閱 < [Securing Services](../../../docs/framework/wcf/securing-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-224">For more information, see [Securing Services](../../../docs/framework/wcf/securing-services.md).</span></span>  
  
 <span data-ttu-id="fb763-225">例如，下列程式碼範例不會設定合約上的 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 或 <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fb763-225">For example, the following code example does not set either the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> or the <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> property on the contract.</span></span>  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();    
}  
```  
  
 <span data-ttu-id="fb763-226">以下為 Visual Basic 程式碼的對等用法。</span><span class="sxs-lookup"><span data-stu-id="fb763-226">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 <span data-ttu-id="fb763-227">與包含預設 `ISampleService` (預設的 <xref:System.ServiceModel.WSHttpBinding>，也就是 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>) 的端點中的 <xref:System.ServiceModel.SecurityMode.Message> 實作互動時，所有訊息都會經過加密及簽署，因為這是預設的保護層級。</span><span class="sxs-lookup"><span data-stu-id="fb763-227">When interacting with an `ISampleService` implementation in an endpoint with a default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>), all messages are encrypted and signed because this is the default protection level.</span></span> <span data-ttu-id="fb763-228">不過，使用包含預設 `ISampleService` (預設的 <xref:System.ServiceModel.BasicHttpBinding>，也就是 <xref:System.ServiceModel.SecurityMode>) 的 <xref:System.ServiceModel.SecurityMode.None> 服務時，所有訊息都會以文字傳送，因為此繫結沒有安全性，因此會忽略保護層級 (也就是說，訊息不會經過加密也不會簽署)。</span><span class="sxs-lookup"><span data-stu-id="fb763-228">However, when an `ISampleService` service is used with a default <xref:System.ServiceModel.BasicHttpBinding> (the default <xref:System.ServiceModel.SecurityMode>, which is <xref:System.ServiceModel.SecurityMode.None>), all messages are sent as text because there is no security for this binding and so the protection level is ignored (that is, the messages are neither encrypted nor signed).</span></span> <span data-ttu-id="fb763-229">如果將 <xref:System.ServiceModel.SecurityMode> 變更為 <xref:System.ServiceModel.SecurityMode.Message>，則這些訊息會經過加密並簽署 (因為該設定會成為繫結的預設保護層級)。</span><span class="sxs-lookup"><span data-stu-id="fb763-229">If the <xref:System.ServiceModel.SecurityMode> was changed to <xref:System.ServiceModel.SecurityMode.Message>, then these messages would be encrypted and signed (because that would now be the binding's default protection level).</span></span>  
  
 <span data-ttu-id="fb763-230">如果您要明確指定或調整合約的保護需求，請將 <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> 屬性 (或範圍較小的任何 `ProtectionLevel` 屬性) 設為服務合約需要的層級。</span><span class="sxs-lookup"><span data-stu-id="fb763-230">If you want to explicitly specify or adjust the protection requirements for your contract, set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property (or any of the `ProtectionLevel` properties at a smaller scope) to the level your service contract requires.</span></span> <span data-ttu-id="fb763-231">在這種情況下，若要使用明確的設定，繫結必須至少在使用的範圍內支援該設定。</span><span class="sxs-lookup"><span data-stu-id="fb763-231">In this case, using an explicit setting requires the binding to support that setting at a minimum for the scope used.</span></span> <span data-ttu-id="fb763-232">例如，下列程式碼範例會明確指定一個 <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> 值，用於 `GetGuid` 作業。</span><span class="sxs-lookup"><span data-stu-id="fb763-232">For example, the following code example specifies one <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> value explicitly, for the `GetGuid` operation.</span></span>  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();    
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();    
}  
```  
  
 <span data-ttu-id="fb763-233">以下為 Visual Basic 程式碼的對等用法。</span><span class="sxs-lookup"><span data-stu-id="fb763-233">The following is the equivalent Visual Basic code.</span></span>  
  
```vb  
<ServiceContract()> _   
Public Interface IExplicitProtectionLevelSampleService   
    <OperationContract()> _   
    Public Function GetString() As String   
    End Function   
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _   
    Public Function GetInt() As Integer   
    End Function   
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _   
    Public Function GetGuid() As Integer   
    End Function   
  
End Interface  
```  
  
 <span data-ttu-id="fb763-234">實作此 `IExplicitProtectionLevelSampleService` 合約且擁有使用預設 <xref:System.ServiceModel.WSHttpBinding> (預設的 <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>，也就是 <xref:System.ServiceModel.SecurityMode.Message>) 之端點的服務會有下列行為：</span><span class="sxs-lookup"><span data-stu-id="fb763-234">A service that implements this `IExplicitProtectionLevelSampleService` contract and has an endpoint that uses the default <xref:System.ServiceModel.WSHttpBinding> (the default <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, which is <xref:System.ServiceModel.SecurityMode.Message>) has the following behavior:</span></span>  
  
- <span data-ttu-id="fb763-235">`GetString` 作業訊息會經過加密及簽署。</span><span class="sxs-lookup"><span data-stu-id="fb763-235">The `GetString` operation messages are encrypted and signed.</span></span>  
  
- <span data-ttu-id="fb763-236">`GetInt` 作業訊息會以未加密且未簽署的文字 (也就是純文字) 傳送。</span><span class="sxs-lookup"><span data-stu-id="fb763-236">The `GetInt` operation messages are sent as unencrypted and unsigned (that is, plain) text.</span></span>  
  
- <span data-ttu-id="fb763-237">`GetGuid` 作業 <xref:System.Guid?displayProperty=nameWithType> 會在加密且簽署的訊息中傳回。</span><span class="sxs-lookup"><span data-stu-id="fb763-237">The `GetGuid` operation <xref:System.Guid?displayProperty=nameWithType> is returned in a message that is encrypted and signed.</span></span>  
  
 <span data-ttu-id="fb763-238">如需保護層級和使用方式的詳細資訊，請參閱[了解保護層級](../../../docs/framework/wcf/understanding-protection-level.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-238">For more information about protection levels and how to use them, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span> <span data-ttu-id="fb763-239">如需有關安全性的詳細資訊，請參閱 < [Securing Services](../../../docs/framework/wcf/securing-services.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-239">For more information about security, see [Securing Services](../../../docs/framework/wcf/securing-services.md).</span></span>  
  
##### <a name="other-operation-signature-requirements"></a><span data-ttu-id="fb763-240">其他作業簽署需求</span><span class="sxs-lookup"><span data-stu-id="fb763-240">Other Operation Signature Requirements</span></span>  
 <span data-ttu-id="fb763-241">某些應用程式功能需要特殊類型的作業簽章。</span><span class="sxs-lookup"><span data-stu-id="fb763-241">Some application features require a particular kind of operation signature.</span></span> <span data-ttu-id="fb763-242">例如，<xref:System.ServiceModel.NetMsmqBinding> 繫結支援長期服務和用戶端，其中應用程式可以在通訊期間重新啟動，並且從中斷的位置繼續進行，而不會遺漏任何訊息 </span><span class="sxs-lookup"><span data-stu-id="fb763-242">For example, the <xref:System.ServiceModel.NetMsmqBinding> binding supports durable services and clients, in which an application can restart in the middle of communication and pick up where it left off without missing any messages.</span></span> <span data-ttu-id="fb763-243">(如需詳細資訊，請參閱 < [WCF 中的佇列](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。)不過，永久性作業只能採用一個 `in` 參數，而且沒有傳回值。</span><span class="sxs-lookup"><span data-stu-id="fb763-243">(For more information, see [Queues in WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) However, durable operations must take only one `in` parameter and have no return value.</span></span>  
  
 <span data-ttu-id="fb763-244">另一個範例是在作業中使用 <xref:System.IO.Stream> 類型。</span><span class="sxs-lookup"><span data-stu-id="fb763-244">Another example is the use of <xref:System.IO.Stream> types in operations.</span></span> <span data-ttu-id="fb763-245">遊於 <xref:System.IO.Stream> 參數包含整個訊息本文，因此如果輸入或輸出 (也就是 `ref` 參數、`out` 參數或傳回值) 為 <xref:System.IO.Stream> 類型，則必須是作業中指定的唯一輸入或輸出。</span><span class="sxs-lookup"><span data-stu-id="fb763-245">Because the <xref:System.IO.Stream> parameter includes the entire message body, if an input or an output (that is, `ref` parameter, `out` parameter, or return value) is of type <xref:System.IO.Stream>, then it must be the only input or output specified in your operation.</span></span> <span data-ttu-id="fb763-246">此外，參數或傳回型別都必須是 <xref:System.IO.Stream>、<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> 或 <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="fb763-246">In addition, the parameter or return type must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, or <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fb763-247">如需有關資料流的詳細資訊，請參閱 < [Large Data and Streaming](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)。</span><span class="sxs-lookup"><span data-stu-id="fb763-247">For more information about streams, see [Large Data and Streaming](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
##### <a name="names-namespaces-and-obfuscation"></a><span data-ttu-id="fb763-248">名稱、命名空間和混淆</span><span class="sxs-lookup"><span data-stu-id="fb763-248">Names, Namespaces, and Obfuscation</span></span>  
 <span data-ttu-id="fb763-249">當合約轉換為 WSDL 時，以及當建立及傳送合約訊息時，合約定義和作業中的 .NET 型別名稱和命名空間是有意義的。</span><span class="sxs-lookup"><span data-stu-id="fb763-249">The names and namespaces of the .NET types in the definition of contracts and operations are significant when contracts are converted into WSDL and when contract messages are created and sent.</span></span> <span data-ttu-id="fb763-250">因此，強烈建議使用所有支援合約之屬性 (Attribute) (例如 `Name`、`Namespace`、<xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.OperationContractAttribute> 和其他合約屬性 (Attribute) 的 <xref:System.Runtime.Serialization.DataContractAttribute> 和 <xref:System.Runtime.Serialization.DataMemberAttribute> 屬性 (Property)) 來明確設定服務合約名稱和命名空間。</span><span class="sxs-lookup"><span data-stu-id="fb763-250">Therefore, it is strongly recommended that service contract names and namespaces are explicitly set using the `Name` and `Namespace` properties of all supporting contract attributes such as the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>, and other contract attributes.</span></span>  
  
 <span data-ttu-id="fb763-251">這麼做的結果就是，如果未明確設定名稱和命名空間，對組件使用 IL 混淆會變更合約型別名稱和命名空間，並且導致 WSDL 遭到修改和連線交換 (通常會失敗)。</span><span class="sxs-lookup"><span data-stu-id="fb763-251">One result of this is that if the names and namespaces are not explicitly set, the use of IL obfuscation on the assembly alters the contract type names and namespaces and results in modified WSDL and wire exchanges that typically fail.</span></span> <span data-ttu-id="fb763-252">如果您未明確設定合約名稱和命名空間，但是想要使用混淆，請使用 <xref:System.Reflection.ObfuscationAttribute> 和 <xref:System.Reflection.ObfuscateAssemblyAttribute> 屬性，以防止合約型別名稱和命名空間遭到修改。</span><span class="sxs-lookup"><span data-stu-id="fb763-252">If you do not set the contract names and namespaces explicitly but do intend to use obfuscation, use the <xref:System.Reflection.ObfuscationAttribute> and <xref:System.Reflection.ObfuscateAssemblyAttribute> attributes to prevent the modification of the contract type names and namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb763-253">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb763-253">See also</span></span>

- [<span data-ttu-id="fb763-254">如何：建立要求-回覆合約</span><span class="sxs-lookup"><span data-stu-id="fb763-254">How to: Create a Request-Reply Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)
- [<span data-ttu-id="fb763-255">如何：建立單向合約</span><span class="sxs-lookup"><span data-stu-id="fb763-255">How to: Create a One-Way Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)
- [<span data-ttu-id="fb763-256">如何：建立雙工合約</span><span class="sxs-lookup"><span data-stu-id="fb763-256">How to: Create a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="fb763-257">指定服務合約中的資料傳輸</span><span class="sxs-lookup"><span data-stu-id="fb763-257">Specifying Data Transfer in Service Contracts</span></span>](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [<span data-ttu-id="fb763-258">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="fb763-258">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [<span data-ttu-id="fb763-259">使用工作階段</span><span class="sxs-lookup"><span data-stu-id="fb763-259">Using Sessions</span></span>](../../../docs/framework/wcf/using-sessions.md)
- [<span data-ttu-id="fb763-260">同步和非同步作業</span><span class="sxs-lookup"><span data-stu-id="fb763-260">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="fb763-261">可靠的服務</span><span class="sxs-lookup"><span data-stu-id="fb763-261">Reliable Services</span></span>](../../../docs/framework/wcf/reliable-services.md)
- [<span data-ttu-id="fb763-262">服務與異動</span><span class="sxs-lookup"><span data-stu-id="fb763-262">Services and Transactions</span></span>](../../../docs/framework/wcf/services-and-transactions.md)
