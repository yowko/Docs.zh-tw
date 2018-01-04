---
title: "定義並指定錯誤"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handling faults [WCF], specifying
- handling faults [WCF], defining
ms.assetid: c00c84f1-962d-46a7-b07f-ebc4f80fbfc1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713b9594ac628c2c256e8592d3894feee8029332
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="defining-and-specifying-faults"></a><span data-ttu-id="9d58f-102">定義並指定錯誤</span><span class="sxs-lookup"><span data-stu-id="9d58f-102">Defining and Specifying Faults</span></span>
<span data-ttu-id="9d58f-103">SOAP 錯誤會將錯誤狀況資訊從服務傳送到用戶端，而在雙工案例中，則是以互通的方式從用戶端傳送到服務。</span><span class="sxs-lookup"><span data-stu-id="9d58f-103">SOAP faults convey error condition information from a service to a client and, in the duplex case, from a client to a service in an interoperable way.</span></span> <span data-ttu-id="9d58f-104">本主題討論何時及如何定義自訂錯誤內容，並指定可以傳回它們的作業。</span><span class="sxs-lookup"><span data-stu-id="9d58f-104">This topic discusses when and how to define custom fault content and specify which operations can return them.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9d58f-105">如何在服務或雙工用戶端，可以傳送這些錯誤和用戶端或服務的應用程式如何處理這些錯誤，請參閱[傳送和接收錯誤](../../../docs/framework/wcf/sending-and-receiving-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="9d58f-105"> how a service, or duplex client, can send those faults and how a client or service application handles these faults, see [Sending and Receiving Faults](../../../docs/framework/wcf/sending-and-receiving-faults.md).</span></span> <span data-ttu-id="9d58f-106">如需中的錯誤處理的概觀[!INCLUDE[indigo1](../../../includes/indigo1-md.md)]應用程式，請參閱[指定與處理合約和服務中的錯誤](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9d58f-106">For an overview of error handling in [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="9d58f-107">總覽</span><span class="sxs-lookup"><span data-stu-id="9d58f-107">Overview</span></span>  
 <span data-ttu-id="9d58f-108">已宣告的 SOAP 錯誤是其中作業具有指定自訂 SOAP 錯誤類型之 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>的 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-108">Declared SOAP faults are those in which an operation has a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> that specifies a custom SOAP fault type.</span></span> <span data-ttu-id="9d58f-109">未宣告的 SOAP 錯誤則是在作業的合約中未指定的 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-109">Undeclared SOAP faults are those that are not specified in the contract for an operation.</span></span> <span data-ttu-id="9d58f-110">本主題將協助您識別這些錯誤狀況，並為您的服務建立錯誤合約，讓用戶端在收到自訂 SOAP 錯誤的通知時，可以用於正確處理這些錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="9d58f-110">This topic helps you identify those error conditions and create a fault contract for your service that clients can use to properly handle those error conditions when notified by custom SOAP faults.</span></span> <span data-ttu-id="9d58f-111">基本的工作依序為：</span><span class="sxs-lookup"><span data-stu-id="9d58f-111">The basic tasks are, in order:</span></span>  
  
1.  <span data-ttu-id="9d58f-112">定義您服務的用戶端應該知道的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="9d58f-112">Define the error conditions that a client of your service should know about.</span></span>  
  
2.  <span data-ttu-id="9d58f-113">定義這些錯誤狀況的 SOAP 錯誤的自訂內容。</span><span class="sxs-lookup"><span data-stu-id="9d58f-113">Define the custom content of the SOAP faults for those error conditions.</span></span>  
  
3.  <span data-ttu-id="9d58f-114">標示您的作業，讓其擲回的特定 SOAP 錯誤以 WSDL 格式對用戶端公開。</span><span class="sxs-lookup"><span data-stu-id="9d58f-114">Mark your operations so that the specific SOAP faults that they throw are exposed to clients in WSDL.</span></span>  
  
### <a name="defining-error-conditions-that-clients-should-know-about"></a><span data-ttu-id="9d58f-115">定義用戶端應知道的錯誤狀況</span><span class="sxs-lookup"><span data-stu-id="9d58f-115">Defining Error Conditions That Clients Should Know About</span></span>  
 <span data-ttu-id="9d58f-116">SOAP 錯誤是公開描述的訊息，具有特定作業的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="9d58f-116">SOAP faults are publicly described messages that carry fault information for a particular operation.</span></span> <span data-ttu-id="9d58f-117">由於它們是和其他作業訊息一起以 WSDL 描述的，因此用戶端知道並預期在叫用作業時處理這類錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-117">Because they are described along with other operation messages in WSDL, clients know and, therefore, expect to handle such faults when invoking an operation.</span></span> <span data-ttu-id="9d58f-118">但是由於 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務是以 Managed 程式碼撰寫的，因此決定要將哪些使用 Managed 程式碼的錯誤狀況轉換成錯誤並傳回用戶端，可讓您有機會將錯誤狀況和您服務中的錯誤與您和用戶端的正式錯誤對話分開。</span><span class="sxs-lookup"><span data-stu-id="9d58f-118">But because [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] services are written in managed code, deciding which error conditions in managed code are to be converted into faults and returned to the client provides you the opportunity to separate error conditions and bugs in your service from the formal error conversation you have with a client.</span></span>  
  
 <span data-ttu-id="9d58f-119">例如，下列程式碼範例顯示採用兩個整數並傳回另一個整數的作業。</span><span class="sxs-lookup"><span data-stu-id="9d58f-119">For example, the following code example shows an operation that takes two integers and returns another integer.</span></span> <span data-ttu-id="9d58f-120">此處可擲回數個例外狀況，因此當設計錯誤合約時，您必須決定哪些錯誤狀況對您的用戶端是重要的。</span><span class="sxs-lookup"><span data-stu-id="9d58f-120">Several exceptions can be thrown here, so when designing the fault contract, you must determine which error conditions are important for your client.</span></span> <span data-ttu-id="9d58f-121">在此案例中，服務應會偵測到 <xref:System.DivideByZeroException?displayProperty=nameWithType> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9d58f-121">In this case, the service should detect the <xref:System.DivideByZeroException?displayProperty=nameWithType> exception.</span></span>  
  
```csharp  
[ServiceContract]  
public class CalculatorService  
{  
    [OperationContract]   
    int Divide(int a, int b)  
    {  
      if (b==0) throw new Exception("Division by zero!");  
      return a/b;  
    }  
}  
```  
  
```vb  
<ServiceContract> _  
Public Class CalculatorService  
    <OperationContract]> _  
    Public Function Divide(ByVal a As Integer, ByVal b As Integer) _  
       As Integer  
      If (b==0) Then   
            Throw New Exception("Division by zero!")  
      Return a/b  
    End Function  
End Class  
```  
  
 <span data-ttu-id="9d58f-122">在前例中，作業可以傳回除以零特定的自訂 SOAP 錯誤、數學作業特定但包含除以零特定的資訊的自訂錯誤、數個不同錯誤情況的多重錯誤或完全沒有 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-122">In the preceding example the operation can either return a custom SOAP fault that is specific to dividing by zero, a custom fault that is specific to math operations but that contains information specific to dividing by zero, multiple faults for several different error situations, or no SOAP fault at all.</span></span>  
  
### <a name="define-the-content-of-error-conditions"></a><span data-ttu-id="9d58f-123">定義錯誤狀況的內容</span><span class="sxs-lookup"><span data-stu-id="9d58f-123">Define the Content of Error Conditions</span></span>  
 <span data-ttu-id="9d58f-124">在錯誤狀況被識別為可用於傳回自訂 SOAP 錯誤之後，下一個步驟就是定義該錯誤的內容，並確保可以序列化內容結構。</span><span class="sxs-lookup"><span data-stu-id="9d58f-124">Once an error condition has been identified as one that can usefully return a custom SOAP fault, the next step is to define the contents of that fault and ensure that the content structure can be serialized.</span></span> <span data-ttu-id="9d58f-125">上節的程式碼範例顯示 `Divide` 作業特定的錯誤，但如果 `Calculator` 服務上有其他的作業，則單一自訂 SOAP 錯誤可以通知用戶端所有的計算機錯誤狀況，包括 `Divide`。</span><span class="sxs-lookup"><span data-stu-id="9d58f-125">The code example in the preceding section shows an error specific to a `Divide` operation, but if there are other operations on the `Calculator` service, then a single custom SOAP fault can inform the client of all calculator error conditions, `Divide` included.</span></span> <span data-ttu-id="9d58f-126">下列程式碼範例顯示自訂 SOAP 錯誤 `MathFault` 的建立，它可以報告使用所有數學作業所造成的錯誤，包括 `Divide`。</span><span class="sxs-lookup"><span data-stu-id="9d58f-126">The following code example shows the creation of a custom SOAP fault, `MathFault`, which can report errors made using all math operations, including `Divide`.</span></span> <span data-ttu-id="9d58f-127">雖然此類別可以指定作業 (`Operation` 屬性) 和描述問題的值 (`ProblemType` 屬性)，但是此類別和這些屬性必須是可序列化的，才能傳輸到自訂 SOAP 錯誤中的用戶端。</span><span class="sxs-lookup"><span data-stu-id="9d58f-127">While the class can specify an operation (the `Operation` property) and a value that describes the problem (the `ProblemType` property), the class and these properties must be serializable to be transferred to the client in a custom SOAP fault.</span></span> <span data-ttu-id="9d58f-128">因此，<xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> 和 <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> 屬性是用於讓類型和其屬性變成可序列化的，並盡量互通。</span><span class="sxs-lookup"><span data-stu-id="9d58f-128">Therefore, the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> and <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> attributes are used to make the type and its properties serializable and as interoperable as possible.</span></span>  
  
 [!code-csharp[Faults#2](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#2)]
 [!code-vb[Faults#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#2)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="9d58f-129">如何確定您的資料都是可序列化，請參閱[在服務合約中指定資料傳輸](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)。</span><span class="sxs-lookup"><span data-stu-id="9d58f-129"> how to ensure your data is serializable, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="9d58f-130">如需序列化的清單支援<xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>提供，請參閱[資料合約序列化程式所支援的型別](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)。</span><span class="sxs-lookup"><span data-stu-id="9d58f-130">For a list of the serialization support that <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> provides, see [Types Supported by the Data Contract Serializer](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).</span></span>  
  
### <a name="mark-operations-to-establish-the-fault-contract"></a><span data-ttu-id="9d58f-131">標示作業以建立錯誤合約</span><span class="sxs-lookup"><span data-stu-id="9d58f-131">Mark Operations to Establish the Fault Contract</span></span>  
 <span data-ttu-id="9d58f-132">在定義傳回做為自訂 SOAP 錯誤一部分的可序列化資料之後，最後一個步驟就是將您的作業合約標示為擲回該類型的 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-132">Once a serializable data structure that is returned as part of a custom SOAP fault is defined, the last step is to mark your operation contract as throwing a SOAP fault of that type.</span></span> <span data-ttu-id="9d58f-133">如果要執行這項操作，請使用 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> 屬性，並傳遞您所建構之自訂資料型別的型別。</span><span class="sxs-lookup"><span data-stu-id="9d58f-133">To do this, use the <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> attribute and pass the type of the custom data type that you have constructed.</span></span> <span data-ttu-id="9d58f-134">下列程式碼範例將示範如何使用 <xref:System.ServiceModel.FaultContractAttribute> 屬性來指定 `Divide` 作業可以傳回型別 `MathFault` 的 SOAP 錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-134">The following code example shows how to use the <xref:System.ServiceModel.FaultContractAttribute> attribute to specify that the `Divide` operation can return a SOAP fault of type `MathFault`.</span></span> <span data-ttu-id="9d58f-135">其他以數學為基礎的作業現在也可以指定它們可以傳回 `MathFault`。</span><span class="sxs-lookup"><span data-stu-id="9d58f-135">Other math-based operations can now also specify that they can return a `MathFault`.</span></span>  
  
 [!code-csharp[Faults#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faults/cs/service.cs#1)]
 [!code-vb[Faults#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faults/vb/service.vb#1)]  
  
 <span data-ttu-id="9d58f-136">作業可以使用一個以上的 <xref:System.ServiceModel.FaultContractAttribute> 屬性來標示該作業，以指定傳回一個以上的自訂錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-136">An operation can specify that it returns more than one custom fault by marking that operation with more than one <xref:System.ServiceModel.FaultContractAttribute> attribute.</span></span>  
  
 <span data-ttu-id="9d58f-137">說明主題中的下一個步驟中，在您的作業實作中實作錯誤合約[傳送和接收錯誤](../../../docs/framework/wcf/sending-and-receiving-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="9d58f-137">The next step, to implement the fault contract in your operation implementation, is described in the topic [Sending and Receiving Faults](../../../docs/framework/wcf/sending-and-receiving-faults.md).</span></span>  
  
#### <a name="soap-wsdl-and-interoperability-considerations"></a><span data-ttu-id="9d58f-138">SOAP、WSDL 和互通性考量</span><span class="sxs-lookup"><span data-stu-id="9d58f-138">SOAP, WSDL, and Interoperability Considerations</span></span>  
 <span data-ttu-id="9d58f-139">在某些情況中，特別是在與其他平台互通時，控制錯誤在 SOAP 訊息中出現的方式或在 WSDL 中繼資料中描述的方式可能會很重要。</span><span class="sxs-lookup"><span data-stu-id="9d58f-139">In some circumstances, especially when interoperating with other platforms, it may be important to control the way a fault appears in a SOAP message or the way it is described in the WSDL metadata.</span></span>  
  
 <span data-ttu-id="9d58f-140"><xref:System.ServiceModel.FaultContractAttribute> 屬性具有 <xref:System.ServiceModel.FaultContractAttribute.Name%2A> 屬性，可控制為該錯誤在中繼資料中產生的 WSDL 錯誤項目名稱。</span><span class="sxs-lookup"><span data-stu-id="9d58f-140">The <xref:System.ServiceModel.FaultContractAttribute> attribute has a <xref:System.ServiceModel.FaultContractAttribute.Name%2A> property that allows control of the WSDL fault element name that is generated in the metadata for that fault.</span></span>  
  
 <span data-ttu-id="9d58f-141">根據 SOAP 標準，錯誤可以有 `Action`、`Code` 和 `Reason`。</span><span class="sxs-lookup"><span data-stu-id="9d58f-141">According to the SOAP standard, a fault can have an `Action`, a `Code`, and a `Reason`.</span></span> <span data-ttu-id="9d58f-142">`Action` 是由 <xref:System.ServiceModel.FaultContractAttribute.Action%2A> 屬性控制的。</span><span class="sxs-lookup"><span data-stu-id="9d58f-142">The `Action` is controlled by the <xref:System.ServiceModel.FaultContractAttribute.Action%2A> property.</span></span> <span data-ttu-id="9d58f-143"><xref:System.ServiceModel.FaultException.Code%2A> 屬性和 <xref:System.ServiceModel.FaultException.Reason%2A> 屬性都是 <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> 類別的屬性，而該類別是一般 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> 的父類別。</span><span class="sxs-lookup"><span data-stu-id="9d58f-143">The <xref:System.ServiceModel.FaultException.Code%2A> property and <xref:System.ServiceModel.FaultException.Reason%2A> property are both properties of the <xref:System.ServiceModel.FaultException?displayProperty=nameWithType> class, which is the parent class of the generic <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9d58f-144">`Code` 屬性包括 <xref:System.ServiceModel.FaultCode.SubCode%2A> 成員。</span><span class="sxs-lookup"><span data-stu-id="9d58f-144">The `Code` property includes a <xref:System.ServiceModel.FaultCode.SubCode%2A> member.</span></span>  
  
 <span data-ttu-id="9d58f-145">當存取產生錯誤的非服務時，會有特定限制。</span><span class="sxs-lookup"><span data-stu-id="9d58f-145">When accessing non-services that generate faults, certain limitations exist.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="9d58f-146"> 只支援有結構描述所描述以及與資料合約相容之詳細類型的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-146"> supports only faults with detail types that the schema describes and that are compatible with data contracts.</span></span> <span data-ttu-id="9d58f-147">例如，如上所述，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 不支援在其詳細類型中使用 XML 屬性的錯誤，或在詳細資訊區段中有一個以上之最上層項目的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9d58f-147">For example, as mentioned above, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] does not support faults that use XML attributes in their detail types, or faults with more than one top-level element in the detail section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d58f-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="9d58f-148">See Also</span></span>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 [<span data-ttu-id="9d58f-149">指定及處理合約與服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="9d58f-149">Specifying and Handling Faults in Contracts and Services</span></span>](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [<span data-ttu-id="9d58f-150">傳送及接收錯誤</span><span class="sxs-lookup"><span data-stu-id="9d58f-150">Sending and Receiving Faults</span></span>](../../../docs/framework/wcf/sending-and-receiving-faults.md)  
 [<span data-ttu-id="9d58f-151">如何：在服務合約中宣告錯誤</span><span class="sxs-lookup"><span data-stu-id="9d58f-151">How to: Declare Faults in Service Contracts</span></span>](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md)  
 [<span data-ttu-id="9d58f-152">了解保護層級</span><span class="sxs-lookup"><span data-stu-id="9d58f-152">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)  
 [<span data-ttu-id="9d58f-153">如何：設定 ProtectionLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="9d58f-153">How to: Set the ProtectionLevel Property</span></span>](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [<span data-ttu-id="9d58f-154">指定服務合約中的資料傳輸</span><span class="sxs-lookup"><span data-stu-id="9d58f-154">Specifying Data Transfer in Service Contracts</span></span>](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
