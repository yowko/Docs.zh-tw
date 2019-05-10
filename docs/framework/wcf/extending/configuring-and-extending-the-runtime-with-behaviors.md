---
title: 使用行為來設定與擴充執行階段
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 297a951e4678e05da73193133bd6050360b041ff
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587339"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a><span data-ttu-id="120f8-102">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="120f8-102">Configuring and Extending the Runtime with Behaviors</span></span>
<span data-ttu-id="120f8-103">行為可讓您修改預設行為，並新增自訂延伸模組，檢查及驗證服務組態或修改在 Windows Communication Foundation (WCF) 用戶端和服務應用程式的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="120f8-103">Behaviors enable you to modify default behavior and add custom extensions that inspect and validate service configuration or modify runtime behavior in Windows Communication Foundation (WCF) client and service applications.</span></span> <span data-ttu-id="120f8-104">本主題會說明行為介面、如何實作這些介面，以及如何透過程式設計方式或組態檔來將它們新增到服務描述 (在服務應用程式中) 或端點 (在用戶端應用程式中)。</span><span class="sxs-lookup"><span data-stu-id="120f8-104">This topic describes the behavior interfaces, how to implement them, and how to add them to the service description (in a service application) or endpoint (in a client application) programmatically or in a configuration file.</span></span> <span data-ttu-id="120f8-105">如需使用系統提供行為的詳細資訊，請參閱 <<c0> [ 指定服務執行階段行為](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)並[指定用戶端執行階段行為](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="120f8-105">For more information about using system-provided behaviors, see [Specifying Service Run-Time Behavior](../../../../docs/framework/wcf/specifying-service-run-time-behavior.md) and [Specifying Client Run-Time Behavior](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md).</span></span>  
  
## <a name="behaviors"></a><span data-ttu-id="120f8-106">「行為」</span><span class="sxs-lookup"><span data-stu-id="120f8-106">Behaviors</span></span>  
 <span data-ttu-id="120f8-107">行為類型會新增至服務或服務端點描述物件 (服務或用戶端，分別) 使用這些物件由 Windows Communication Foundation (WCF) 來建立執行 WCF 服務或 WCF 用戶端執行階段之前。</span><span class="sxs-lookup"><span data-stu-id="120f8-107">Behavior types are added to the service or service endpoint description objects (on the service or client, respectively) before those objects are used by Windows Communication Foundation (WCF) to create a runtime that executes a WCF service or a WCF client.</span></span> <span data-ttu-id="120f8-108">當在執行階段建構程序期間呼叫這些行為之後，這些行為即可存取可修改由合約、繫結及位址所構成之執行階段的執行階段屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="120f8-108">When these behaviors are called during the runtime construction process they are then able to access runtime properties and methods that modify the runtime constructed by the contract, bindings, and addresses.</span></span>  
  
### <a name="behavior-methods"></a><span data-ttu-id="120f8-109">行為方法</span><span class="sxs-lookup"><span data-stu-id="120f8-109">Behavior Methods</span></span>  
 <span data-ttu-id="120f8-110">所有的行為有`AddBindingParameters`方法中，`ApplyDispatchBehavior`方法，`Validate`方法，和`ApplyClientBehavior`有一個例外狀況的方法：因為<xref:System.ServiceModel.Description.IServiceBehavior>無法執行在用戶端，它不會實作`ApplyClientBehavior`。</span><span class="sxs-lookup"><span data-stu-id="120f8-110">All behaviors have an `AddBindingParameters` method, an `ApplyDispatchBehavior` method, a `Validate` method, and an `ApplyClientBehavior` method with one exception: Because <xref:System.ServiceModel.Description.IServiceBehavior> cannot execute in a client, it does not implement `ApplyClientBehavior`.</span></span>  
  
- <span data-ttu-id="120f8-111">使用 `AddBindingParameters` 方法來修改自訂物件，或將其加入至自訂繫結可在執行階段建構時存取以供自己使用的集合中。</span><span class="sxs-lookup"><span data-stu-id="120f8-111">Use the `AddBindingParameters` method to modify or add custom objects to a collection that custom bindings can access for their use when the runtime is constructed.</span></span> <span data-ttu-id="120f8-112">例如，在這種情況下，通道開發人員不知道實際影響通道建置方式的保護需求指定方式。</span><span class="sxs-lookup"><span data-stu-id="120f8-112">For example, this how protection requirements are specified that affect the way the channel is built, but are not known by the channel developer.</span></span>  
  
- <span data-ttu-id="120f8-113">使用 `Validate` 方法來檢查描述樹狀目錄和對應的執行階段物件，以確定該物件符合一些準則。</span><span class="sxs-lookup"><span data-stu-id="120f8-113">Use the `Validate` method to examine the description tree and corresponding runtime object to ensure it conforms to some set of criteria.</span></span>  
  
- <span data-ttu-id="120f8-114">使用 `ApplyDispatchBehavior` 和 `ApplyClientBehavior` 方法來檢查描述樹狀目錄，以及修改服務或用戶端上之特定範圍的執行階段。</span><span class="sxs-lookup"><span data-stu-id="120f8-114">Use the `ApplyDispatchBehavior` and `ApplyClientBehavior` methods to examine the description tree and modify the runtime for a particular scope on either the service or the client.</span></span> <span data-ttu-id="120f8-115">您也可以插入擴充物件。</span><span class="sxs-lookup"><span data-stu-id="120f8-115">You can also insert extension objects as well.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="120f8-116">雖然在這些方法中有提供描述樹狀目錄，但它僅供檢查用途。</span><span class="sxs-lookup"><span data-stu-id="120f8-116">Although a description tree is provided in these methods, it is for examination only.</span></span> <span data-ttu-id="120f8-117">如果描述樹狀目錄遭到修改，該行為便屬於未定義的。</span><span class="sxs-lookup"><span data-stu-id="120f8-117">If a description tree is modified, the behavior is undefined.</span></span>  
  
 <span data-ttu-id="120f8-118">您可以修改的屬性及可以實作的自訂介面，將透過服務和用戶端執行階段類別來存取。</span><span class="sxs-lookup"><span data-stu-id="120f8-118">The properties you can modify and the customization interfaces you can implement are accessed through the service and client runtime classes.</span></span> <span data-ttu-id="120f8-119">這些服務類型是 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別。</span><span class="sxs-lookup"><span data-stu-id="120f8-119">The service types are the <xref:System.ServiceModel.Dispatcher.DispatchRuntime> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes.</span></span> <span data-ttu-id="120f8-120">用戶端類型則是 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.ClientOperation> 類別。</span><span class="sxs-lookup"><span data-stu-id="120f8-120">The client types are the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.ClientOperation> classes.</span></span> <span data-ttu-id="120f8-121"><xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別分別是存取全用戶端及全服務執行階段屬性和擴充集合的擴充性進入點 (Entry Point)。</span><span class="sxs-lookup"><span data-stu-id="120f8-121">The <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes are the extensibility entry points to access client-wide and service-wide runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="120f8-122">同樣地，<xref:System.ServiceModel.Dispatcher.ClientOperation> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別會分別公開 (Expose) 用戶端作業及服務作業執行階段屬性和擴充集合。</span><span class="sxs-lookup"><span data-stu-id="120f8-122">Similarly, the <xref:System.ServiceModel.Dispatcher.ClientOperation> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes expose client operation and service operation runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="120f8-123">不過，您可以從作業執行階段物件存取範圍更廣的執行階段物件，或是在需要時反向執行。</span><span class="sxs-lookup"><span data-stu-id="120f8-123">You can, however, access the wider scoped runtime object from the operation runtime object and vice versa if need be.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="120f8-124">如需執行階段屬性和延伸模組類型可供您修改用戶端的執行行為的討論，請參閱 <<c0> [ 擴充用戶端](../../../../docs/framework/wcf/extending/extending-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="120f8-124">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a client, see [Extending Clients](../../../../docs/framework/wcf/extending/extending-clients.md).</span></span> <span data-ttu-id="120f8-125">如需執行階段屬性和延伸模組類型可供您修改服務發送器的執行行為的討論，請參閱 <<c0> [ 擴充發送器](../../../../docs/framework/wcf/extending/extending-dispatchers.md)。</span><span class="sxs-lookup"><span data-stu-id="120f8-125">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a service dispatcher, see [Extending Dispatchers](../../../../docs/framework/wcf/extending/extending-dispatchers.md).</span></span>  
  
 <span data-ttu-id="120f8-126">大部分的 WCF 使用者直接; 不會互動的執行階段改為使用核心程式設計模型建構，例如端點、 合約、 繫結、 位址和行為上的類別或行為在組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-126">Most WCF users do not interact with the runtime directly; instead they use core programming model constructs like endpoints, contracts, bindings, addresses, and behavior attributes on classes or behaviors in configuration files.</span></span> <span data-ttu-id="120f8-127">這些建構組成*描述樹狀目錄*，這是完整的規格來建構執行階段以支援服務，或描述樹狀結構所描述的用戶端。</span><span class="sxs-lookup"><span data-stu-id="120f8-127">These constructs make up the *description tree*, which is the complete specification for constructing a runtime to support a service or client described by the description tree.</span></span>  
  
 <span data-ttu-id="120f8-128">有四種 WCF 中的行為：</span><span class="sxs-lookup"><span data-stu-id="120f8-128">There are four kinds of behaviors in WCF:</span></span>  
  
- <span data-ttu-id="120f8-129">服務行為 (<xref:System.ServiceModel.Description.IServiceBehavior> 類型) 讓整個服務執行階段 (包括 <xref:System.ServiceModel.ServiceHostBase>) 能夠進行自訂。</span><span class="sxs-lookup"><span data-stu-id="120f8-129">Service behaviors (<xref:System.ServiceModel.Description.IServiceBehavior> types) enable the customization of the entire service runtime including <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
- <span data-ttu-id="120f8-130">端點行為 (<xref:System.ServiceModel.Description.IEndpointBehavior> 類型) 讓服務端點及其關聯的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 物件能夠進行自訂。</span><span class="sxs-lookup"><span data-stu-id="120f8-130">Endpoint behaviors (<xref:System.ServiceModel.Description.IEndpointBehavior> types) enable the customization of service endpoints and their associated <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objects.</span></span>  
  
- <span data-ttu-id="120f8-131">合約行為 (<xref:System.ServiceModel.Description.IContractBehavior> 類型) 讓 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別能夠分別在用戶端及服務應用程式中進行自訂。</span><span class="sxs-lookup"><span data-stu-id="120f8-131">Contract behaviors (<xref:System.ServiceModel.Description.IContractBehavior> types) enable the customization of both the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes in client and service applications, respectively.</span></span>  
  
- <span data-ttu-id="120f8-132">作業行為 (<xref:System.ServiceModel.Description.IOperationBehavior> 類型) 同樣地讓 <xref:System.ServiceModel.Dispatcher.ClientOperation> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別能在用戶端及服務上進行自訂。</span><span class="sxs-lookup"><span data-stu-id="120f8-132">Operation behaviors (<xref:System.ServiceModel.Description.IOperationBehavior> types) enable the customization of the <xref:System.ServiceModel.Dispatcher.ClientOperation> and <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes, again, on the client and service.</span></span>  
  
 <span data-ttu-id="120f8-133">將這些行為新增到各種描述物件的作業，可以透過實作自訂屬性、使用應用程式組態檔來完成，或是將這些行為直接新增到適當描述物件的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="120f8-133">You can add these behaviors to the various description objects by implementing custom attributes, using application configuration files, or directly by adding them to the behaviors collection on the appropriate description object.</span></span> <span data-ttu-id="120f8-134">不過，在呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 或 <xref:System.ServiceModel.ServiceHost><xref:System.ServiceModel.ChannelFactory%601>上的  之前，這些行為一定要先新增到服務描述或服務端點描述物件。</span><span class="sxs-lookup"><span data-stu-id="120f8-134">The must, however, be added to a service description or service endpoint description object prior to calling <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on the <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>.</span></span>  
  
### <a name="behavior-scopes"></a><span data-ttu-id="120f8-135">行為範圍</span><span class="sxs-lookup"><span data-stu-id="120f8-135">Behavior Scopes</span></span>  
 <span data-ttu-id="120f8-136">這四個行為類型都會分別對應到執行階段存取的特定範圍。</span><span class="sxs-lookup"><span data-stu-id="120f8-136">There are four behavior types, each of which corresponds to a particular scope of runtime access.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="120f8-137">服務行為</span><span class="sxs-lookup"><span data-stu-id="120f8-137">Service Behaviors</span></span>  
 <span data-ttu-id="120f8-138">實作 <xref:System.ServiceModel.Description.IServiceBehavior> 的服務行為，是您用來修改整個服務執行階段的主要機制。</span><span class="sxs-lookup"><span data-stu-id="120f8-138">Service behaviors, which implement <xref:System.ServiceModel.Description.IServiceBehavior>, are the primary mechanism by which you modify the entire service runtime.</span></span> <span data-ttu-id="120f8-139">將服務行為新增到服務時可使用三種機制。</span><span class="sxs-lookup"><span data-stu-id="120f8-139">There are three mechanisms for adding service behaviors to a service.</span></span>  
  
1. <span data-ttu-id="120f8-140">在服務類別上使用屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-140">Using an attribute on the service class.</span></span>  <span data-ttu-id="120f8-141">當已建構 <xref:System.ServiceModel.ServiceHost> 時，<xref:System.ServiceModel.ServiceHost> 實作 (Implementation) 會使用反映 (Reflection) 來找出該服務類型上的一組屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-141">When a <xref:System.ServiceModel.ServiceHost> is constructed, the <xref:System.ServiceModel.ServiceHost> implementation uses reflection to discover the set of attributes on the type of the service.</span></span> <span data-ttu-id="120f8-142">如果其中任何一個屬性是 <xref:System.ServiceModel.Description.IServiceBehavior> 的實作，這組屬性便會新增到 <xref:System.ServiceModel.Description.ServiceDescription> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="120f8-142">If any of those attributes are implementations of <xref:System.ServiceModel.Description.IServiceBehavior>, they are added to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="120f8-143">這樣便可讓這些行為參與建構服務執行階段的程序。</span><span class="sxs-lookup"><span data-stu-id="120f8-143">This allows those behaviors to participate in the construction of the service run time.</span></span>  
  
2. <span data-ttu-id="120f8-144">以程式設計方式將行為新增到 <xref:System.ServiceModel.Description.ServiceDescription> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="120f8-144">Programmatically adding the behavior to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="120f8-145">運用下列幾行程式碼即可達成這點：</span><span class="sxs-lookup"><span data-stu-id="120f8-145">This can be accomplished with the following lines of code:</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. <span data-ttu-id="120f8-146">實作會擴充組態的自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>。</span><span class="sxs-lookup"><span data-stu-id="120f8-146">Implementing a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span> <span data-ttu-id="120f8-147">這樣便可從應用程式組態檔使用服務行為。</span><span class="sxs-lookup"><span data-stu-id="120f8-147">This enables the use of the service behavior from application configuration files.</span></span>  
  
 <span data-ttu-id="120f8-148">在 WCF 中的服務行為的範例包括<xref:System.ServiceModel.ServiceBehaviorAttribute>屬性， <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>，和<xref:System.ServiceModel.Description.ServiceMetadataBehavior>行為。</span><span class="sxs-lookup"><span data-stu-id="120f8-148">Examples of service behaviors in WCF include the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute, the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>, and the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="120f8-149">合約行為</span><span class="sxs-lookup"><span data-stu-id="120f8-149">Contract Behaviors</span></span>  
 <span data-ttu-id="120f8-150">實作 <xref:System.ServiceModel.Description.IContractBehavior> 介面的合約行為，可用於擴充整個合約的用戶端與服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="120f8-150">Contract behaviors, which implement the <xref:System.ServiceModel.Description.IContractBehavior> interface, are used to extend both the client and service runtime across a contract.</span></span>  
  
 <span data-ttu-id="120f8-151">將合約行為新增到合約時可以使用兩種機制。</span><span class="sxs-lookup"><span data-stu-id="120f8-151">There are two mechanisms for adding contract behaviors to a contract.</span></span>  <span data-ttu-id="120f8-152">第一種機制是建立要在合約介面上使用的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-152">The first mechanism is to create a custom attribute to be used on the contract interface.</span></span> <span data-ttu-id="120f8-153">當合約介面傳遞至<xref:System.ServiceModel.ServiceHost>或<xref:System.ServiceModel.ChannelFactory%601>，WCF 會檢查在介面上的屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-153">When a contract interface is passed to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>, WCF examines the attributes on the interface.</span></span> <span data-ttu-id="120f8-154">如果其中任何一個屬性是 <xref:System.ServiceModel.Description.IContractBehavior> 的實作，這些屬性便會新增到為該介面建立之 <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="120f8-154">If any attributes are implementations of <xref:System.ServiceModel.Description.IContractBehavior>, those are added to the behaviors collection on the <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> created for that interface.</span></span>  
  
 <span data-ttu-id="120f8-155">您也可以在自訂合約行為屬性上實作 <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="120f8-155">You can also implement the <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> on the custom contract behavior attribute.</span></span> <span data-ttu-id="120f8-156">在此情況下，將依套用對象產生類似下列的行為：</span><span class="sxs-lookup"><span data-stu-id="120f8-156">In this case, the behavior is as follows when applied to:</span></span>  
  
 <span data-ttu-id="120f8-157">•合約介面。</span><span class="sxs-lookup"><span data-stu-id="120f8-157">•A contract interface.</span></span> <span data-ttu-id="120f8-158">在此情況下，行為會套用至任何端點中該類型的所有合約，WCF 會忽略值<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-158">In this case, the behavior is applied to all contracts of that type in any endpoint and WCF ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="120f8-159">•服務類別。</span><span class="sxs-lookup"><span data-stu-id="120f8-159">•A service class.</span></span> <span data-ttu-id="120f8-160">在此情況下，行為只會套用至其中合約為 <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> 屬性值的端點。</span><span class="sxs-lookup"><span data-stu-id="120f8-160">In this case, the behavior is applied only to endpoints the contract of which is the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="120f8-161">•回呼類別。</span><span class="sxs-lookup"><span data-stu-id="120f8-161">•A callback class.</span></span> <span data-ttu-id="120f8-162">在此情況下，行為會套用至雙工用戶端的端點，WCF 會忽略值<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-162">In this case, the behavior is applied to the duplex client's endpoint and WCF ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="120f8-163">第二種機制是將行為新增至 <xref:System.ServiceModel.Description.ContractDescription> 上的行為集合。</span><span class="sxs-lookup"><span data-stu-id="120f8-163">The second mechanism is to add the behavior to the behaviors collection on a <xref:System.ServiceModel.Description.ContractDescription>.</span></span>  
  
 <span data-ttu-id="120f8-164">在 WCF 中的合約行為的範例包括<xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType>屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-164">Examples of contract behaviors in WCF include the <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="120f8-165">如需詳細資訊和範例，請參閱參考主題。</span><span class="sxs-lookup"><span data-stu-id="120f8-165">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="endpoint-behaviors"></a><span data-ttu-id="120f8-166">端點行為</span><span class="sxs-lookup"><span data-stu-id="120f8-166">Endpoint Behaviors</span></span>  
 <span data-ttu-id="120f8-167">實作 <xref:System.ServiceModel.Description.IEndpointBehavior> 的端點行為，是您用來針對特定端點修改整個服務或用戶端執行階段的主要機制。</span><span class="sxs-lookup"><span data-stu-id="120f8-167">Endpoint behaviors, which implement <xref:System.ServiceModel.Description.IEndpointBehavior>, are the primary mechanism by which you modify the entire service or client run time for a specific endpoint.</span></span>  
  
 <span data-ttu-id="120f8-168">將端點行為新增到服務時可以使用兩種機制。</span><span class="sxs-lookup"><span data-stu-id="120f8-168">There are two mechanisms for adding endpoint behaviors to a service.</span></span>  
  
1. <span data-ttu-id="120f8-169">將行為新增到 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-169">Add the behavior to the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property.</span></span>  
  
2. <span data-ttu-id="120f8-170">實作會擴充組態的自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>。</span><span class="sxs-lookup"><span data-stu-id="120f8-170">Implement a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span>  
  
 <span data-ttu-id="120f8-171">如需詳細資訊和範例，請參閱參考主題。</span><span class="sxs-lookup"><span data-stu-id="120f8-171">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="120f8-172">作業行為</span><span class="sxs-lookup"><span data-stu-id="120f8-172">Operation Behaviors</span></span>  
 <span data-ttu-id="120f8-173">實作 <xref:System.ServiceModel.Description.IOperationBehavior> 介面的作業行為，可用來擴充每個作業的用戶端與服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="120f8-173">Operation behaviors, which implement the <xref:System.ServiceModel.Description.IOperationBehavior> interface, are used to extend both the client and service runtime for each operation.</span></span>  
  
 <span data-ttu-id="120f8-174">將作業行為新增到作業時可以使用兩種機制。</span><span class="sxs-lookup"><span data-stu-id="120f8-174">There are two mechanisms for adding operation behaviors to an operation.</span></span> <span data-ttu-id="120f8-175">第一種機制是建立要用於建立作業模型之方法的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-175">The first mechanism is to create a custom attribute to be used on the method that models the operation.</span></span> <span data-ttu-id="120f8-176">當將作業新增至<xref:System.ServiceModel.ServiceHost>或<xref:System.ServiceModel.ChannelFactory>，WCF 新增<xref:System.ServiceModel.Description.IOperationBehavior>屬性的行為集合<xref:System.ServiceModel.Description.OperationDescription>建立該作業。</span><span class="sxs-lookup"><span data-stu-id="120f8-176">When an operation is added to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory>, WCF adds any  <xref:System.ServiceModel.Description.IOperationBehavior> attributes to the behaviors collection on the <xref:System.ServiceModel.Description.OperationDescription> created for that operation.</span></span>  
  
 <span data-ttu-id="120f8-177">第二種機制是將行為直接新增至已建構 <xref:System.ServiceModel.Description.OperationDescription> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="120f8-177">The second mechanism is by directly adding the behavior to the behaviors collection on a constructed <xref:System.ServiceModel.Description.OperationDescription>.</span></span>  
  
 <span data-ttu-id="120f8-178">在 WCF 中的作業行為的範例包括<xref:System.ServiceModel.OperationBehaviorAttribute>而<xref:System.ServiceModel.TransactionFlowAttribute>。</span><span class="sxs-lookup"><span data-stu-id="120f8-178">Examples of operation behaviors in WCF include the <xref:System.ServiceModel.OperationBehaviorAttribute> and the <xref:System.ServiceModel.TransactionFlowAttribute>.</span></span>  
  
 <span data-ttu-id="120f8-179">如需詳細資訊和範例，請參閱參考主題。</span><span class="sxs-lookup"><span data-stu-id="120f8-179">For more information and an example, see the reference topic.</span></span>  
  
### <a name="using-configuration-to-create-behaviors"></a><span data-ttu-id="120f8-180">使用組態來建立行為</span><span class="sxs-lookup"><span data-stu-id="120f8-180">Using Configuration to Create Behaviors</span></span>  
 <span data-ttu-id="120f8-181">服務行為、端點行為以及合約行為都可以設計成透過程式碼或使用屬性來加以指定；只有服務行為和端點行為可以使用應用程式或 Web 組態檔來加以設定。</span><span class="sxs-lookup"><span data-stu-id="120f8-181">Service and endpoint, and contract behaviors can by designed to be specified in code or using attributes; only service and endpoint behaviors can be configured using application or Web configuration files.</span></span> <span data-ttu-id="120f8-182">使用屬性公開行為，可讓開發人員在編譯時期指定在執行階段時所無法新增、移除或修改的行為。</span><span class="sxs-lookup"><span data-stu-id="120f8-182">Exposing behaviors using attributes allows developers to specify a behavior at compilation-time that cannot be added, removed, or modified at runtime.</span></span> <span data-ttu-id="120f8-183">這種做法往往適用於正確服務作業一定需要的行為 (例如，<xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> 屬性的異動相關參數)。</span><span class="sxs-lookup"><span data-stu-id="120f8-183">This is often suitable for behaviors that are always required for the correct operation of a service (for example, the transaction-related parameters to the <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> attribute).</span></span> <span data-ttu-id="120f8-184">使用組態公開行為，可讓開發人員將這些行為的規格和組態留給部署該服務的人員來決定。</span><span class="sxs-lookup"><span data-stu-id="120f8-184">Exposing behaviors using configuration allows developers to leave the specification and configuration of those behaviors to those who deploy the service.</span></span> <span data-ttu-id="120f8-185">這種做法適用於屬於選擇性元件或其他部署特定組態的行為，例如是否要向服務公開中繼資料，或是服務的特定授權組態。</span><span class="sxs-lookup"><span data-stu-id="120f8-185">This is suitable for behaviors that are optional components or other deployment-specific configuration, such as whether metadata is exposed for the service or the particular authorization configuration for a service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="120f8-186">您也可以使用支援組態強制公司應用程式原則的行為，使用方法是將這些行為插入 machine.config 組態檔，並鎖定這些項目。</span><span class="sxs-lookup"><span data-stu-id="120f8-186">You can also use behaviors that support configuration to enforce company application policies by inserting them into the machine.config configuration file and locking those items down.</span></span> <span data-ttu-id="120f8-187">如需說明和範例，請參閱[How to:鎖定在企業中的端點](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="120f8-187">For a description and an example, see [How to: Lock Down Endpoints in the Enterprise](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).</span></span>  
  
 <span data-ttu-id="120f8-188">若要使用組態公開行為，開發人員必須建立 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 的衍生類別 (Derived Class)，然後再向組態註冊該延伸。</span><span class="sxs-lookup"><span data-stu-id="120f8-188">To expose a behavior using configuration, a developer must create a derived class of <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> and then register that extension with configuration.</span></span>  
  
 <span data-ttu-id="120f8-189">下列程式碼範例會示範 <xref:System.ServiceModel.Description.IEndpointBehavior> 如何實作 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>：</span><span class="sxs-lookup"><span data-stu-id="120f8-189">The following code example shows how an  <xref:System.ServiceModel.Description.IEndpointBehavior> implements <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:</span></span>  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 <span data-ttu-id="120f8-190">為了讓組態系統載入自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>，此項目必須註冊為延伸。</span><span class="sxs-lookup"><span data-stu-id="120f8-190">In order for the configuration system to load a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, it must be registered as an extension.</span></span> <span data-ttu-id="120f8-191">下列程式碼範例顯示了前述端點行為的組態檔：</span><span class="sxs-lookup"><span data-stu-id="120f8-191">The following code example shows the configuration file for the preceding endpoint behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service   
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"   
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add   
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="120f8-192">何處`Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector`是行為延伸型別和`HostApplication`是該類別已編譯所在的組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="120f8-192">Where `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` is the behavior extension type and `HostApplication` is the name of the assembly into which that class has been compiled.</span></span>  
  
### <a name="evaluation-order"></a><span data-ttu-id="120f8-193">評估順序</span><span class="sxs-lookup"><span data-stu-id="120f8-193">Evaluation Order</span></span>  
 <span data-ttu-id="120f8-194"><xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 和 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 會負責從程式設計模型及描述來建置執行階段。</span><span class="sxs-lookup"><span data-stu-id="120f8-194">The <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> and the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> are responsible for building the runtime from the programming model and description.</span></span> <span data-ttu-id="120f8-195">正如先前所述，行為會作用於位在服務、端點、合約及作業時的建置程序。</span><span class="sxs-lookup"><span data-stu-id="120f8-195">Behaviors, as previously described, contribute to that build process at the service, endpoint, contract, and operation.</span></span>  
  
 <span data-ttu-id="120f8-196"><xref:System.ServiceModel.ServiceHost> 會依照下列順序來套用行為：</span><span class="sxs-lookup"><span data-stu-id="120f8-196">The <xref:System.ServiceModel.ServiceHost> applies behaviors in the following order:</span></span>  
  
1. <span data-ttu-id="120f8-197">服務</span><span class="sxs-lookup"><span data-stu-id="120f8-197">Service</span></span>  
  
2. <span data-ttu-id="120f8-198">合約</span><span class="sxs-lookup"><span data-stu-id="120f8-198">Contract</span></span>  
  
3. <span data-ttu-id="120f8-199">端點</span><span class="sxs-lookup"><span data-stu-id="120f8-199">Endpoint</span></span>  
  
4. <span data-ttu-id="120f8-200">運算</span><span class="sxs-lookup"><span data-stu-id="120f8-200">Operation</span></span>  
  
 <span data-ttu-id="120f8-201">在任何行為集合內，並不會保證任何順序。</span><span class="sxs-lookup"><span data-stu-id="120f8-201">Within any collection of behaviors, no order is guaranteed.</span></span>  
  
 <span data-ttu-id="120f8-202"><xref:System.ServiceModel.ChannelFactory%601> 會依照下列順序來套用行為：</span><span class="sxs-lookup"><span data-stu-id="120f8-202">The <xref:System.ServiceModel.ChannelFactory%601> applies behaviors in the following order:</span></span>  
  
1. <span data-ttu-id="120f8-203">合約</span><span class="sxs-lookup"><span data-stu-id="120f8-203">Contract</span></span>  
  
2. <span data-ttu-id="120f8-204">端點</span><span class="sxs-lookup"><span data-stu-id="120f8-204">Endpoint</span></span>  
  
3. <span data-ttu-id="120f8-205">運算</span><span class="sxs-lookup"><span data-stu-id="120f8-205">Operation</span></span>  
  
 <span data-ttu-id="120f8-206">同樣地，在任何行為集合內，並不會保證任何順序。</span><span class="sxs-lookup"><span data-stu-id="120f8-206">Within any collection of behaviors, again, no order is guaranteed.</span></span>  
  
### <a name="adding-behaviors-programmatically"></a><span data-ttu-id="120f8-207">以程式設計方式來新增行為</span><span class="sxs-lookup"><span data-stu-id="120f8-207">Adding Behaviors Programmatically</span></span>  
 <span data-ttu-id="120f8-208">在服務應用程式中 <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> 的屬性，絕對不能在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> 方法之後遭到修改。</span><span class="sxs-lookup"><span data-stu-id="120f8-208">Properties of the <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> method on <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="120f8-209">有些方法在通過該點後若遭到修改，就會擲回例外狀況，這些方法包括 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> 屬性，以及在 `AddServiceEndpoint` 與 <xref:System.ServiceModel.ServiceHostBase> 上的 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="120f8-209">Some members, like the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, throw an exception if modified past that point.</span></span> <span data-ttu-id="120f8-210">其他成員可讓您加以修改，但結果仍未定義。</span><span class="sxs-lookup"><span data-stu-id="120f8-210">Others permit you to modify them, but the result is undefined.</span></span>  
  
 <span data-ttu-id="120f8-211">同樣地，您不可以在呼叫 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之後修改用戶端上的 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="120f8-211">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>.</span></span> <span data-ttu-id="120f8-212">如果 <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> 屬性在通過該點之後遭到修改，它便會擲回例外狀況，不過其他用戶端描述值在遭到修改時並不會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="120f8-212">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> property throws an exception if modified past that point, but the other client description values can be modified without error.</span></span> <span data-ttu-id="120f8-213">不過產生結果將會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="120f8-213">The result, however, is undefined.</span></span>  
  
 <span data-ttu-id="120f8-214">無論是在服務或是用戶端，建議的做法都是在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> 之前修改說明。</span><span class="sxs-lookup"><span data-stu-id="120f8-214">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="inheritance-rules-for-behavior-attributes"></a><span data-ttu-id="120f8-215">行為屬性的繼承規則</span><span class="sxs-lookup"><span data-stu-id="120f8-215">Inheritance Rules for Behavior Attributes</span></span>  
 <span data-ttu-id="120f8-216">這四種行為都可以使用屬性 (服務行為與合約行為) 來填入。</span><span class="sxs-lookup"><span data-stu-id="120f8-216">All four types of behaviors can be populated using attributes – service behaviors and contract behaviors.</span></span> <span data-ttu-id="120f8-217">由於屬性是定義在 Managed 物件與成員上，而 Managed 物件與成員會支援繼承 (Inheritance)，所以這時必須定義行為屬性在繼承內容中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="120f8-217">Because attributes are defined on managed objects and members, and managed objects and members support inheritance, it is necessary to define how behavior attributes work in the context of inheritance.</span></span>  
  
 <span data-ttu-id="120f8-218">在高層級的規則是指針對特定範圍 (例如，服務、合約或作業) 的規則，而繼承階層架構 (Inheritance Hierarchy) 中的所有行為屬性是指針對該範圍所套用的行為屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-218">At a high level, the rule is that for a particular scope (for example, service, contract, or operation), all behavior attributes in the inheritance hierarchy for that scope are applied.</span></span> <span data-ttu-id="120f8-219">如果這時出現兩個相同型別的行為屬性，將只套用最末層衍生型別。</span><span class="sxs-lookup"><span data-stu-id="120f8-219">If there are two behavior attributes of the same type, only the most-derived type is used.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="120f8-220">服務行為</span><span class="sxs-lookup"><span data-stu-id="120f8-220">Service Behaviors</span></span>  
 <span data-ttu-id="120f8-221">對於特定的服務類別，將套用該類別及其父代 (Parent) 上的所有服務行為屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-221">For a given service class, all service behavior attributes on that class, and on parents of that class, are applied.</span></span> <span data-ttu-id="120f8-222">如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。</span><span class="sxs-lookup"><span data-stu-id="120f8-222">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 <span data-ttu-id="120f8-223">例如，在上述範例中，服務 B 最後產生 <xref:System.ServiceModel.InstanceContextMode><xref:System.ServiceModel.InstanceContextMode.Single>的 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode>、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> 的 <xref:System.ServiceModel.ConcurrencyMode> 模式，以及 <xref:System.ServiceModel.ConcurrencyMode.Single> 的 。</span><span class="sxs-lookup"><span data-stu-id="120f8-223">For example, in the preceding case, the service B ends up with an <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.Single>, an <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> mode of <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, and a <xref:System.ServiceModel.ConcurrencyMode> of <xref:System.ServiceModel.ConcurrencyMode.Single>.</span></span> <span data-ttu-id="120f8-224">由於服務 B 上的 <xref:System.ServiceModel.ConcurrencyMode> 屬性比服務 A 上的相同屬性「更具衍生性」，所以 <xref:System.ServiceModel.ConcurrencyMode.Single> 會是 <xref:System.ServiceModel.ServiceBehaviorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="120f8-224">The <xref:System.ServiceModel.ConcurrencyMode> is <xref:System.ServiceModel.ConcurrencyMode.Single>, because <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute on service B is on "more derived" than that on service A.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="120f8-225">合約行為</span><span class="sxs-lookup"><span data-stu-id="120f8-225">Contract Behaviors</span></span>  
 <span data-ttu-id="120f8-226">對於指定的合約，將套用該介面及其父代上的所有合約行為屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-226">For a given contract, all contract behavior attributes on that interface and on parents of that interface, are applied.</span></span> <span data-ttu-id="120f8-227">如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。</span><span class="sxs-lookup"><span data-stu-id="120f8-227">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="120f8-228">作業行為</span><span class="sxs-lookup"><span data-stu-id="120f8-228">Operation Behaviors</span></span>  
 <span data-ttu-id="120f8-229">如果指定的作業沒有覆寫現有的抽象或虛擬作業，就不會套用任何繼承規則。</span><span class="sxs-lookup"><span data-stu-id="120f8-229">If a given operation does not override an existing abstract or virtual operation, no inheritance rules apply.</span></span>  
  
 <span data-ttu-id="120f8-230">如果作業確實覆寫了現有的作業，這時將套用該作業及其父代上的所有作業行為屬性。</span><span class="sxs-lookup"><span data-stu-id="120f8-230">If an operation does override an existing operation, then all operation behavior attributes on that operation and on parents of that operation, are applied.</span></span>  <span data-ttu-id="120f8-231">如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。</span><span class="sxs-lookup"><span data-stu-id="120f8-231">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>
