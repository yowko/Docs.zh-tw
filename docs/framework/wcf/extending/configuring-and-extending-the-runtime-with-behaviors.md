---
title: 使用行為來設定與擴充執行階段
description: 瞭解如何在 WCF 應用程式中執行行為介面，並以程式設計方式或在設定檔中將其加入至服務描述或端點。
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: fc297f593b744d69cb09a33be6816fb646f88b67
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247581"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a><span data-ttu-id="a1771-103">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="a1771-103">Configuring and Extending the Runtime with Behaviors</span></span>
<span data-ttu-id="a1771-104">行為可讓您修改預設行為，並加入自訂延伸模組，以檢查和驗證服務設定，或修改 Windows Communication Foundation （WCF）用戶端和服務應用程式中的執行時間行為。</span><span class="sxs-lookup"><span data-stu-id="a1771-104">Behaviors enable you to modify default behavior and add custom extensions that inspect and validate service configuration or modify runtime behavior in Windows Communication Foundation (WCF) client and service applications.</span></span> <span data-ttu-id="a1771-105">本主題會說明行為介面、如何實作這些介面，以及如何透過程式設計方式或組態檔來將它們新增到服務描述 (在服務應用程式中) 或端點 (在用戶端應用程式中)。</span><span class="sxs-lookup"><span data-stu-id="a1771-105">This topic describes the behavior interfaces, how to implement them, and how to add them to the service description (in a service application) or endpoint (in a client application) programmatically or in a configuration file.</span></span> <span data-ttu-id="a1771-106">如需使用系統提供之行為的詳細資訊，請參閱[指定服務執行時間行為](../specifying-service-run-time-behavior.md)和[指定用戶端執行時間行為](../specifying-client-run-time-behavior.md)。</span><span class="sxs-lookup"><span data-stu-id="a1771-106">For more information about using system-provided behaviors, see [Specifying Service Run-Time Behavior](../specifying-service-run-time-behavior.md) and [Specifying Client Run-Time Behavior](../specifying-client-run-time-behavior.md).</span></span>  
  
## <a name="behaviors"></a><span data-ttu-id="a1771-107">「行為」</span><span class="sxs-lookup"><span data-stu-id="a1771-107">Behaviors</span></span>  
 <span data-ttu-id="a1771-108">行為類型會先新增至服務或服務端點描述物件（分別在服務或用戶端上），Windows Communication Foundation （WCF）使用這些物件來建立執行 WCF 服務或 WCF 用戶端的執行時間。</span><span class="sxs-lookup"><span data-stu-id="a1771-108">Behavior types are added to the service or service endpoint description objects (on the service or client, respectively) before those objects are used by Windows Communication Foundation (WCF) to create a runtime that executes a WCF service or a WCF client.</span></span> <span data-ttu-id="a1771-109">當在執行階段建構程序期間呼叫這些行為之後，這些行為即可存取可修改由合約、繫結及位址所構成之執行階段的執行階段屬性和方法。</span><span class="sxs-lookup"><span data-stu-id="a1771-109">When these behaviors are called during the runtime construction process they are then able to access runtime properties and methods that modify the runtime constructed by the contract, bindings, and addresses.</span></span>  
  
### <a name="behavior-methods"></a><span data-ttu-id="a1771-110">行為方法</span><span class="sxs-lookup"><span data-stu-id="a1771-110">Behavior Methods</span></span>  
 <span data-ttu-id="a1771-111">所有的行為方法都有 `AddBindingParameters` 方法、`ApplyDispatchBehavior` 方法、`Validate` 方法，以及例外的 `ApplyClientBehavior` 方法：因為 <xref:System.ServiceModel.Description.IServiceBehavior> 無法在用戶端中執行，因此它不會實作 `ApplyClientBehavior`。</span><span class="sxs-lookup"><span data-stu-id="a1771-111">All behaviors have an `AddBindingParameters` method, an `ApplyDispatchBehavior` method, a `Validate` method, and an `ApplyClientBehavior` method with one exception: Because <xref:System.ServiceModel.Description.IServiceBehavior> cannot execute in a client, it does not implement `ApplyClientBehavior`.</span></span>  
  
- <span data-ttu-id="a1771-112">使用 `AddBindingParameters` 方法來修改自訂物件，或將其加入至自訂繫結可在執行階段建構時存取以供自己使用的集合中。</span><span class="sxs-lookup"><span data-stu-id="a1771-112">Use the `AddBindingParameters` method to modify or add custom objects to a collection that custom bindings can access for their use when the runtime is constructed.</span></span> <span data-ttu-id="a1771-113">例如，在這種情況下，通道開發人員不知道實際影響通道建置方式的保護需求指定方式。</span><span class="sxs-lookup"><span data-stu-id="a1771-113">For example, this how protection requirements are specified that affect the way the channel is built, but are not known by the channel developer.</span></span>  
  
- <span data-ttu-id="a1771-114">使用 `Validate` 方法來檢查描述樹狀目錄和對應的執行階段物件，以確定該物件符合一些準則。</span><span class="sxs-lookup"><span data-stu-id="a1771-114">Use the `Validate` method to examine the description tree and corresponding runtime object to ensure it conforms to some set of criteria.</span></span>  
  
- <span data-ttu-id="a1771-115">使用 `ApplyDispatchBehavior` 和 `ApplyClientBehavior` 方法來檢查描述樹狀目錄，以及修改服務或用戶端上之特定範圍的執行階段。</span><span class="sxs-lookup"><span data-stu-id="a1771-115">Use the `ApplyDispatchBehavior` and `ApplyClientBehavior` methods to examine the description tree and modify the runtime for a particular scope on either the service or the client.</span></span> <span data-ttu-id="a1771-116">您也可以插入擴充物件。</span><span class="sxs-lookup"><span data-stu-id="a1771-116">You can also insert extension objects as well.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="a1771-117">雖然在這些方法中有提供描述樹狀目錄，但它僅供檢查用途。</span><span class="sxs-lookup"><span data-stu-id="a1771-117">Although a description tree is provided in these methods, it is for examination only.</span></span> <span data-ttu-id="a1771-118">如果描述樹狀目錄遭到修改，該行為便屬於未定義的。</span><span class="sxs-lookup"><span data-stu-id="a1771-118">If a description tree is modified, the behavior is undefined.</span></span>  
  
 <span data-ttu-id="a1771-119">您可以修改的屬性及可以實作的自訂介面，將透過服務和用戶端執行階段類別來存取。</span><span class="sxs-lookup"><span data-stu-id="a1771-119">The properties you can modify and the customization interfaces you can implement are accessed through the service and client runtime classes.</span></span> <span data-ttu-id="a1771-120">這些服務類型是 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別。</span><span class="sxs-lookup"><span data-stu-id="a1771-120">The service types are the <xref:System.ServiceModel.Dispatcher.DispatchRuntime> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes.</span></span> <span data-ttu-id="a1771-121">用戶端類型則是 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.ClientOperation> 類別。</span><span class="sxs-lookup"><span data-stu-id="a1771-121">The client types are the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.ClientOperation> classes.</span></span> <span data-ttu-id="a1771-122"><xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別分別是存取全用戶端及全服務執行階段屬性和擴充集合的擴充性進入點 (Entry Point)。</span><span class="sxs-lookup"><span data-stu-id="a1771-122">The <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes are the extensibility entry points to access client-wide and service-wide runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="a1771-123">同樣地，<xref:System.ServiceModel.Dispatcher.ClientOperation> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別會分別公開 (Expose) 用戶端作業及服務作業執行階段屬性和擴充集合。</span><span class="sxs-lookup"><span data-stu-id="a1771-123">Similarly, the <xref:System.ServiceModel.Dispatcher.ClientOperation> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes expose client operation and service operation runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="a1771-124">不過，您可以從作業執行階段物件存取範圍更廣的執行階段物件，或是在需要時反向執行。</span><span class="sxs-lookup"><span data-stu-id="a1771-124">You can, however, access the wider scoped runtime object from the operation runtime object and vice versa if need be.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1771-125">如需您可以用來修改用戶端執行行為的執行時間屬性和擴充類型的討論，請參閱[擴充用戶端](extending-clients.md)。</span><span class="sxs-lookup"><span data-stu-id="a1771-125">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a client, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="a1771-126">如需您可以用來修改服務發送器之執行行為的執行時間屬性和擴充類型的討論，請參閱[擴充發送器](extending-dispatchers.md)。</span><span class="sxs-lookup"><span data-stu-id="a1771-126">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a service dispatcher, see [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
 <span data-ttu-id="a1771-127">大部分的 WCF 使用者都不會直接與執行時間互動;相反地，它們會在設定檔中的類別或行為上使用核心程式設計模型結構，例如端點、合約、系結、位址及行為屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-127">Most WCF users do not interact with the runtime directly; instead they use core programming model constructs like endpoints, contracts, bindings, addresses, and behavior attributes on classes or behaviors in configuration files.</span></span> <span data-ttu-id="a1771-128">這些結構組成*描述樹狀結構*，這是用來建立執行時間以支援描述樹狀目錄所描述之服務或用戶端的完整規格。</span><span class="sxs-lookup"><span data-stu-id="a1771-128">These constructs make up the *description tree*, which is the complete specification for constructing a runtime to support a service or client described by the description tree.</span></span>  
  
 <span data-ttu-id="a1771-129">在 WCF 中有四種行為：</span><span class="sxs-lookup"><span data-stu-id="a1771-129">There are four kinds of behaviors in WCF:</span></span>  
  
- <span data-ttu-id="a1771-130">服務行為 (<xref:System.ServiceModel.Description.IServiceBehavior> 類型) 讓整個服務執行階段 (包括 <xref:System.ServiceModel.ServiceHostBase>) 能夠進行自訂。</span><span class="sxs-lookup"><span data-stu-id="a1771-130">Service behaviors (<xref:System.ServiceModel.Description.IServiceBehavior> types) enable the customization of the entire service runtime including <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
- <span data-ttu-id="a1771-131">端點行為 (<xref:System.ServiceModel.Description.IEndpointBehavior> 類型) 讓服務端點及其關聯的 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 物件能夠進行自訂。</span><span class="sxs-lookup"><span data-stu-id="a1771-131">Endpoint behaviors (<xref:System.ServiceModel.Description.IEndpointBehavior> types) enable the customization of service endpoints and their associated <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objects.</span></span>  
  
- <span data-ttu-id="a1771-132">合約行為 (<xref:System.ServiceModel.Description.IContractBehavior> 類型) 讓 <xref:System.ServiceModel.Dispatcher.ClientRuntime> 與 <xref:System.ServiceModel.Dispatcher.DispatchRuntime> 類別能夠分別在用戶端及服務應用程式中進行自訂。</span><span class="sxs-lookup"><span data-stu-id="a1771-132">Contract behaviors (<xref:System.ServiceModel.Description.IContractBehavior> types) enable the customization of both the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes in client and service applications, respectively.</span></span>  
  
- <span data-ttu-id="a1771-133">作業行為 (<xref:System.ServiceModel.Description.IOperationBehavior> 類型) 同樣地讓 <xref:System.ServiceModel.Dispatcher.ClientOperation> 與 <xref:System.ServiceModel.Dispatcher.DispatchOperation> 類別能在用戶端及服務上進行自訂。</span><span class="sxs-lookup"><span data-stu-id="a1771-133">Operation behaviors (<xref:System.ServiceModel.Description.IOperationBehavior> types) enable the customization of the <xref:System.ServiceModel.Dispatcher.ClientOperation> and <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes, again, on the client and service.</span></span>  
  
 <span data-ttu-id="a1771-134">將這些行為新增到各種描述物件的作業，可以透過實作自訂屬性、使用應用程式組態檔來完成，或是將這些行為直接新增到適當描述物件的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="a1771-134">You can add these behaviors to the various description objects by implementing custom attributes, using application configuration files, or directly by adding them to the behaviors collection on the appropriate description object.</span></span> <span data-ttu-id="a1771-135">不過，在呼叫  或 上的  之前，這些行為一定要先新增到服務描述或服務端點描述物件。</span><span class="sxs-lookup"><span data-stu-id="a1771-135">The must, however, be added to a service description or service endpoint description object prior to calling <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on the <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>.</span></span>  
  
### <a name="behavior-scopes"></a><span data-ttu-id="a1771-136">行為範圍</span><span class="sxs-lookup"><span data-stu-id="a1771-136">Behavior Scopes</span></span>  
 <span data-ttu-id="a1771-137">這四個行為類型都會分別對應到執行階段存取的特定範圍。</span><span class="sxs-lookup"><span data-stu-id="a1771-137">There are four behavior types, each of which corresponds to a particular scope of runtime access.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="a1771-138">服務行為</span><span class="sxs-lookup"><span data-stu-id="a1771-138">Service Behaviors</span></span>  
 <span data-ttu-id="a1771-139">實作 <xref:System.ServiceModel.Description.IServiceBehavior> 的服務行為，是您用來修改整個服務執行階段的主要機制。</span><span class="sxs-lookup"><span data-stu-id="a1771-139">Service behaviors, which implement <xref:System.ServiceModel.Description.IServiceBehavior>, are the primary mechanism by which you modify the entire service runtime.</span></span> <span data-ttu-id="a1771-140">將服務行為新增到服務時可使用三種機制。</span><span class="sxs-lookup"><span data-stu-id="a1771-140">There are three mechanisms for adding service behaviors to a service.</span></span>  
  
1. <span data-ttu-id="a1771-141">在服務類別上使用屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-141">Using an attribute on the service class.</span></span>  <span data-ttu-id="a1771-142">當已建構 <xref:System.ServiceModel.ServiceHost> 時，<xref:System.ServiceModel.ServiceHost> 實作 (Implementation) 會使用反映 (Reflection) 來找出該服務類型上的一組屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-142">When a <xref:System.ServiceModel.ServiceHost> is constructed, the <xref:System.ServiceModel.ServiceHost> implementation uses reflection to discover the set of attributes on the type of the service.</span></span> <span data-ttu-id="a1771-143">如果其中任何一個屬性是 <xref:System.ServiceModel.Description.IServiceBehavior> 的實作，這組屬性便會新增到 <xref:System.ServiceModel.Description.ServiceDescription> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="a1771-143">If any of those attributes are implementations of <xref:System.ServiceModel.Description.IServiceBehavior>, they are added to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="a1771-144">這樣便可讓這些行為參與建構服務執行階段的程序。</span><span class="sxs-lookup"><span data-stu-id="a1771-144">This allows those behaviors to participate in the construction of the service run time.</span></span>  
  
2. <span data-ttu-id="a1771-145">以程式設計方式將行為新增到 <xref:System.ServiceModel.Description.ServiceDescription> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="a1771-145">Programmatically adding the behavior to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="a1771-146">運用下列幾行程式碼即可達成這點：</span><span class="sxs-lookup"><span data-stu-id="a1771-146">This can be accomplished with the following lines of code:</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. <span data-ttu-id="a1771-147">實作會擴充組態的自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>。</span><span class="sxs-lookup"><span data-stu-id="a1771-147">Implementing a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span> <span data-ttu-id="a1771-148">這樣便可從應用程式組態檔使用服務行為。</span><span class="sxs-lookup"><span data-stu-id="a1771-148">This enables the use of the service behavior from application configuration files.</span></span>  
  
 <span data-ttu-id="a1771-149">WCF 中的服務行為範例包括 <xref:System.ServiceModel.ServiceBehaviorAttribute> 屬性、 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> 和 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 行為。</span><span class="sxs-lookup"><span data-stu-id="a1771-149">Examples of service behaviors in WCF include the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute, the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>, and the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="a1771-150">合約行為</span><span class="sxs-lookup"><span data-stu-id="a1771-150">Contract Behaviors</span></span>  
 <span data-ttu-id="a1771-151">實作 <xref:System.ServiceModel.Description.IContractBehavior> 介面的合約行為，可用於擴充整個合約的用戶端與服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="a1771-151">Contract behaviors, which implement the <xref:System.ServiceModel.Description.IContractBehavior> interface, are used to extend both the client and service runtime across a contract.</span></span>  
  
 <span data-ttu-id="a1771-152">將合約行為新增到合約時可以使用兩種機制。</span><span class="sxs-lookup"><span data-stu-id="a1771-152">There are two mechanisms for adding contract behaviors to a contract.</span></span>  <span data-ttu-id="a1771-153">第一種機制是建立要在合約介面上使用的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-153">The first mechanism is to create a custom attribute to be used on the contract interface.</span></span> <span data-ttu-id="a1771-154">當合約介面傳遞至 <xref:System.ServiceModel.ServiceHost> 或時 <xref:System.ServiceModel.ChannelFactory%601> ，WCF 會檢查介面上的屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-154">When a contract interface is passed to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>, WCF examines the attributes on the interface.</span></span> <span data-ttu-id="a1771-155">如果其中任何一個屬性是 <xref:System.ServiceModel.Description.IContractBehavior> 的實作，這些屬性便會新增到為該介面建立之 <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="a1771-155">If any attributes are implementations of <xref:System.ServiceModel.Description.IContractBehavior>, those are added to the behaviors collection on the <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> created for that interface.</span></span>  
  
 <span data-ttu-id="a1771-156">您也可以在自訂合約行為屬性上實作 <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="a1771-156">You can also implement the <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> on the custom contract behavior attribute.</span></span> <span data-ttu-id="a1771-157">在此情況下，將依套用對象產生類似下列的行為：</span><span class="sxs-lookup"><span data-stu-id="a1771-157">In this case, the behavior is as follows when applied to:</span></span>  
  
 <span data-ttu-id="a1771-158">•合約介面。</span><span class="sxs-lookup"><span data-stu-id="a1771-158">•A contract interface.</span></span> <span data-ttu-id="a1771-159">在此情況下，行為會套用至任何端點中該類型的所有合約，而 WCF 會忽略屬性的值 <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="a1771-159">In this case, the behavior is applied to all contracts of that type in any endpoint and WCF ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="a1771-160">•服務類別。</span><span class="sxs-lookup"><span data-stu-id="a1771-160">•A service class.</span></span> <span data-ttu-id="a1771-161">在此情況下，行為只會套用至其中合約為 <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> 屬性值的端點。</span><span class="sxs-lookup"><span data-stu-id="a1771-161">In this case, the behavior is applied only to endpoints the contract of which is the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="a1771-162">•回呼類別。</span><span class="sxs-lookup"><span data-stu-id="a1771-162">•A callback class.</span></span> <span data-ttu-id="a1771-163">在此情況下，行為會套用至雙工用戶端的端點，而 WCF 會忽略屬性的值 <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a1771-163">In this case, the behavior is applied to the duplex client's endpoint and WCF ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="a1771-164">第二種機制是將行為新增至 <xref:System.ServiceModel.Description.ContractDescription> 上的行為集合。</span><span class="sxs-lookup"><span data-stu-id="a1771-164">The second mechanism is to add the behavior to the behaviors collection on a <xref:System.ServiceModel.Description.ContractDescription>.</span></span>  
  
 <span data-ttu-id="a1771-165">WCF 中的合約行為範例包括 <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-165">Examples of contract behaviors in WCF include the <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="a1771-166">如需詳細資訊和範例，請參閱參考主題。</span><span class="sxs-lookup"><span data-stu-id="a1771-166">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="endpoint-behaviors"></a><span data-ttu-id="a1771-167">端點行為</span><span class="sxs-lookup"><span data-stu-id="a1771-167">Endpoint Behaviors</span></span>  
 <span data-ttu-id="a1771-168">實作 <xref:System.ServiceModel.Description.IEndpointBehavior> 的端點行為，是您用來針對特定端點修改整個服務或用戶端執行階段的主要機制。</span><span class="sxs-lookup"><span data-stu-id="a1771-168">Endpoint behaviors, which implement <xref:System.ServiceModel.Description.IEndpointBehavior>, are the primary mechanism by which you modify the entire service or client run time for a specific endpoint.</span></span>  
  
 <span data-ttu-id="a1771-169">將端點行為新增到服務時可以使用兩種機制。</span><span class="sxs-lookup"><span data-stu-id="a1771-169">There are two mechanisms for adding endpoint behaviors to a service.</span></span>  
  
1. <span data-ttu-id="a1771-170">將行為新增到 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-170">Add the behavior to the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property.</span></span>  
  
2. <span data-ttu-id="a1771-171">實作會擴充組態的自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>。</span><span class="sxs-lookup"><span data-stu-id="a1771-171">Implement a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span>  
  
 <span data-ttu-id="a1771-172">如需詳細資訊和範例，請參閱參考主題。</span><span class="sxs-lookup"><span data-stu-id="a1771-172">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="a1771-173">作業行為</span><span class="sxs-lookup"><span data-stu-id="a1771-173">Operation Behaviors</span></span>  
 <span data-ttu-id="a1771-174">實作 <xref:System.ServiceModel.Description.IOperationBehavior> 介面的作業行為，可用來擴充每個作業的用戶端與服務執行階段。</span><span class="sxs-lookup"><span data-stu-id="a1771-174">Operation behaviors, which implement the <xref:System.ServiceModel.Description.IOperationBehavior> interface, are used to extend both the client and service runtime for each operation.</span></span>  
  
 <span data-ttu-id="a1771-175">將作業行為新增到作業時可以使用兩種機制。</span><span class="sxs-lookup"><span data-stu-id="a1771-175">There are two mechanisms for adding operation behaviors to an operation.</span></span> <span data-ttu-id="a1771-176">第一種機制是建立要用於建立作業模型之方法的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-176">The first mechanism is to create a custom attribute to be used on the method that models the operation.</span></span> <span data-ttu-id="a1771-177">將作業新增至 <xref:System.ServiceModel.ServiceHost> 或時 <xref:System.ServiceModel.ChannelFactory> ，WCF 會將任何 <xref:System.ServiceModel.Description.IOperationBehavior> 屬性新增至針對該作業所建立之上的行為集合 <xref:System.ServiceModel.Description.OperationDescription> 。</span><span class="sxs-lookup"><span data-stu-id="a1771-177">When an operation is added to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory>, WCF adds any  <xref:System.ServiceModel.Description.IOperationBehavior> attributes to the behaviors collection on the <xref:System.ServiceModel.Description.OperationDescription> created for that operation.</span></span>  
  
 <span data-ttu-id="a1771-178">第二種機制是將行為直接新增至已建構 <xref:System.ServiceModel.Description.OperationDescription> 上的行為集合中。</span><span class="sxs-lookup"><span data-stu-id="a1771-178">The second mechanism is by directly adding the behavior to the behaviors collection on a constructed <xref:System.ServiceModel.Description.OperationDescription>.</span></span>  
  
 <span data-ttu-id="a1771-179">WCF 中的作業行為範例包括 <xref:System.ServiceModel.OperationBehaviorAttribute> 和 <xref:System.ServiceModel.TransactionFlowAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="a1771-179">Examples of operation behaviors in WCF include the <xref:System.ServiceModel.OperationBehaviorAttribute> and the <xref:System.ServiceModel.TransactionFlowAttribute>.</span></span>  
  
 <span data-ttu-id="a1771-180">如需詳細資訊和範例，請參閱參考主題。</span><span class="sxs-lookup"><span data-stu-id="a1771-180">For more information and an example, see the reference topic.</span></span>  
  
### <a name="using-configuration-to-create-behaviors"></a><span data-ttu-id="a1771-181">使用組態來建立行為</span><span class="sxs-lookup"><span data-stu-id="a1771-181">Using Configuration to Create Behaviors</span></span>  
 <span data-ttu-id="a1771-182">服務行為、端點行為以及合約行為都可以設計成透過程式碼或使用屬性來加以指定；只有服務行為和端點行為可以使用應用程式或 Web 組態檔來加以設定。</span><span class="sxs-lookup"><span data-stu-id="a1771-182">Service and endpoint, and contract behaviors can by designed to be specified in code or using attributes; only service and endpoint behaviors can be configured using application or Web configuration files.</span></span> <span data-ttu-id="a1771-183">使用屬性公開行為，可讓開發人員在編譯時期指定在執行階段時所無法新增、移除或修改的行為。</span><span class="sxs-lookup"><span data-stu-id="a1771-183">Exposing behaviors using attributes allows developers to specify a behavior at compilation-time that cannot be added, removed, or modified at runtime.</span></span> <span data-ttu-id="a1771-184">這種做法往往適用於正確服務作業一定需要的行為 (例如，<xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> 屬性的異動相關參數)。</span><span class="sxs-lookup"><span data-stu-id="a1771-184">This is often suitable for behaviors that are always required for the correct operation of a service (for example, the transaction-related parameters to the <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> attribute).</span></span> <span data-ttu-id="a1771-185">使用組態公開行為，可讓開發人員將這些行為的規格和組態留給部署該服務的人員來決定。</span><span class="sxs-lookup"><span data-stu-id="a1771-185">Exposing behaviors using configuration allows developers to leave the specification and configuration of those behaviors to those who deploy the service.</span></span> <span data-ttu-id="a1771-186">這種做法適用於屬於選擇性元件或其他部署特定組態的行為，例如是否要向服務公開中繼資料，或是服務的特定授權組態。</span><span class="sxs-lookup"><span data-stu-id="a1771-186">This is suitable for behaviors that are optional components or other deployment-specific configuration, such as whether metadata is exposed for the service or the particular authorization configuration for a service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1771-187">您也可以使用支援組態強制公司應用程式原則的行為，使用方法是將這些行為插入 machine.config 組態檔，並鎖定這些項目。</span><span class="sxs-lookup"><span data-stu-id="a1771-187">You can also use behaviors that support configuration to enforce company application policies by inserting them into the machine.config configuration file and locking those items down.</span></span> <span data-ttu-id="a1771-188">如需說明和範例，請參閱[如何：鎖定企業中的端點](how-to-lock-down-endpoints-in-the-enterprise.md)。</span><span class="sxs-lookup"><span data-stu-id="a1771-188">For a description and an example, see [How to: Lock Down Endpoints in the Enterprise](how-to-lock-down-endpoints-in-the-enterprise.md).</span></span>  
  
 <span data-ttu-id="a1771-189">若要使用組態公開行為，開發人員必須建立 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 的衍生類別 (Derived Class)，然後再向組態註冊該延伸。</span><span class="sxs-lookup"><span data-stu-id="a1771-189">To expose a behavior using configuration, a developer must create a derived class of <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> and then register that extension with configuration.</span></span>  
  
 <span data-ttu-id="a1771-190">下列程式碼範例會示範 <xref:System.ServiceModel.Description.IEndpointBehavior> 如何實作 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>：</span><span class="sxs-lookup"><span data-stu-id="a1771-190">The following code example shows how an  <xref:System.ServiceModel.Description.IEndpointBehavior> implements <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:</span></span>  
  
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
  
 <span data-ttu-id="a1771-191">為了讓組態系統載入自訂 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>，此項目必須註冊為延伸。</span><span class="sxs-lookup"><span data-stu-id="a1771-191">In order for the configuration system to load a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, it must be registered as an extension.</span></span> <span data-ttu-id="a1771-192">下列程式碼範例顯示了前述端點行為的組態檔：</span><span class="sxs-lookup"><span data-stu-id="a1771-192">The following code example shows the configuration file for the preceding endpoint behavior:</span></span>  
  
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
  
 <span data-ttu-id="a1771-193">其中， `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` 是行為延伸型別，而 `HostApplication` 是該類別已編譯成的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="a1771-193">Where `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` is the behavior extension type and `HostApplication` is the name of the assembly into which that class has been compiled.</span></span>  
  
### <a name="evaluation-order"></a><span data-ttu-id="a1771-194">評估順序</span><span class="sxs-lookup"><span data-stu-id="a1771-194">Evaluation Order</span></span>  
 <span data-ttu-id="a1771-195"><xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 和 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 會負責從程式設計模型及描述來建置執行階段。</span><span class="sxs-lookup"><span data-stu-id="a1771-195">The <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> and the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> are responsible for building the runtime from the programming model and description.</span></span> <span data-ttu-id="a1771-196">正如先前所述，行為會作用於位在服務、端點、合約及作業時的建置程序。</span><span class="sxs-lookup"><span data-stu-id="a1771-196">Behaviors, as previously described, contribute to that build process at the service, endpoint, contract, and operation.</span></span>  
  
 <span data-ttu-id="a1771-197"><xref:System.ServiceModel.ServiceHost> 會依照下列順序來套用行為：</span><span class="sxs-lookup"><span data-stu-id="a1771-197">The <xref:System.ServiceModel.ServiceHost> applies behaviors in the following order:</span></span>  
  
1. <span data-ttu-id="a1771-198">服務</span><span class="sxs-lookup"><span data-stu-id="a1771-198">Service</span></span>  
  
2. <span data-ttu-id="a1771-199">合約</span><span class="sxs-lookup"><span data-stu-id="a1771-199">Contract</span></span>  
  
3. <span data-ttu-id="a1771-200">端點</span><span class="sxs-lookup"><span data-stu-id="a1771-200">Endpoint</span></span>  
  
4. <span data-ttu-id="a1771-201">作業</span><span class="sxs-lookup"><span data-stu-id="a1771-201">Operation</span></span>  
  
 <span data-ttu-id="a1771-202">在任何行為集合內，並不會保證任何順序。</span><span class="sxs-lookup"><span data-stu-id="a1771-202">Within any collection of behaviors, no order is guaranteed.</span></span>  
  
 <span data-ttu-id="a1771-203"><xref:System.ServiceModel.ChannelFactory%601> 會依照下列順序來套用行為：</span><span class="sxs-lookup"><span data-stu-id="a1771-203">The <xref:System.ServiceModel.ChannelFactory%601> applies behaviors in the following order:</span></span>  
  
1. <span data-ttu-id="a1771-204">合約</span><span class="sxs-lookup"><span data-stu-id="a1771-204">Contract</span></span>  
  
2. <span data-ttu-id="a1771-205">端點</span><span class="sxs-lookup"><span data-stu-id="a1771-205">Endpoint</span></span>  
  
3. <span data-ttu-id="a1771-206">作業</span><span class="sxs-lookup"><span data-stu-id="a1771-206">Operation</span></span>  
  
 <span data-ttu-id="a1771-207">同樣地，在任何行為集合內，並不會保證任何順序。</span><span class="sxs-lookup"><span data-stu-id="a1771-207">Within any collection of behaviors, again, no order is guaranteed.</span></span>  
  
### <a name="adding-behaviors-programmatically"></a><span data-ttu-id="a1771-208">以程式設計方式來新增行為</span><span class="sxs-lookup"><span data-stu-id="a1771-208">Adding Behaviors Programmatically</span></span>  
 <span data-ttu-id="a1771-209">在服務應用程式中 <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> 的屬性，絕對不能在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> 方法之後遭到修改。</span><span class="sxs-lookup"><span data-stu-id="a1771-209">Properties of the <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> method on <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a1771-210">有些方法在通過該點後若遭到修改，就會擲回例外狀況，這些方法包括 <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> 屬性，以及在 `AddServiceEndpoint` 與 <xref:System.ServiceModel.ServiceHostBase> 上的 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="a1771-210">Some members, like the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, throw an exception if modified past that point.</span></span> <span data-ttu-id="a1771-211">其他成員可讓您加以修改，但結果仍未定義。</span><span class="sxs-lookup"><span data-stu-id="a1771-211">Others permit you to modify them, but the result is undefined.</span></span>  
  
 <span data-ttu-id="a1771-212">同樣地，您不可以在呼叫 <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> 上的 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 之後修改用戶端上的 <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 值。</span><span class="sxs-lookup"><span data-stu-id="a1771-212">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a1771-213">如果 <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> 屬性在通過該點之後遭到修改，它便會擲回例外狀況，不過其他用戶端描述值在遭到修改時並不會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="a1771-213">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> property throws an exception if modified past that point, but the other client description values can be modified without error.</span></span> <span data-ttu-id="a1771-214">不過產生結果將會是未定義的。</span><span class="sxs-lookup"><span data-stu-id="a1771-214">The result, however, is undefined.</span></span>  
  
 <span data-ttu-id="a1771-215">無論是在服務或是用戶端，建議的做法都是在呼叫 <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> 之前修改說明。</span><span class="sxs-lookup"><span data-stu-id="a1771-215">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="inheritance-rules-for-behavior-attributes"></a><span data-ttu-id="a1771-216">行為屬性的繼承規則</span><span class="sxs-lookup"><span data-stu-id="a1771-216">Inheritance Rules for Behavior Attributes</span></span>  
 <span data-ttu-id="a1771-217">這四種行為都可以使用屬性 (服務行為與合約行為) 來填入。</span><span class="sxs-lookup"><span data-stu-id="a1771-217">All four types of behaviors can be populated using attributes – service behaviors and contract behaviors.</span></span> <span data-ttu-id="a1771-218">由於屬性是定義在 Managed 物件與成員上，而 Managed 物件與成員會支援繼承 (Inheritance)，所以這時必須定義行為屬性在繼承內容中的運作方式。</span><span class="sxs-lookup"><span data-stu-id="a1771-218">Because attributes are defined on managed objects and members, and managed objects and members support inheritance, it is necessary to define how behavior attributes work in the context of inheritance.</span></span>  
  
 <span data-ttu-id="a1771-219">在高層級的規則是指針對特定範圍 (例如，服務、合約或作業) 的規則，而繼承階層架構 (Inheritance Hierarchy) 中的所有行為屬性是指針對該範圍所套用的行為屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-219">At a high level, the rule is that for a particular scope (for example, service, contract, or operation), all behavior attributes in the inheritance hierarchy for that scope are applied.</span></span> <span data-ttu-id="a1771-220">如果這時出現兩個相同型別的行為屬性，將只套用最末層衍生型別。</span><span class="sxs-lookup"><span data-stu-id="a1771-220">If there are two behavior attributes of the same type, only the most-derived type is used.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="a1771-221">服務行為</span><span class="sxs-lookup"><span data-stu-id="a1771-221">Service Behaviors</span></span>  
 <span data-ttu-id="a1771-222">對於特定的服務類別，將套用該類別及其父代 (Parent) 上的所有服務行為屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-222">For a given service class, all service behavior attributes on that class, and on parents of that class, are applied.</span></span> <span data-ttu-id="a1771-223">如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。</span><span class="sxs-lookup"><span data-stu-id="a1771-223">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 <span data-ttu-id="a1771-224">例如，在上述範例中，服務 B 最後產生 的 、 的  模式，以及  的 。</span><span class="sxs-lookup"><span data-stu-id="a1771-224">For example, in the preceding case, the service B ends up with an <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.Single>, an <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> mode of <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, and a <xref:System.ServiceModel.ConcurrencyMode> of <xref:System.ServiceModel.ConcurrencyMode.Single>.</span></span> <span data-ttu-id="a1771-225">由於服務 B 上的 <xref:System.ServiceModel.ConcurrencyMode> 屬性比服務 A 上的相同屬性「更具衍生性」，所以 <xref:System.ServiceModel.ConcurrencyMode.Single> 會是 <xref:System.ServiceModel.ServiceBehaviorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="a1771-225">The <xref:System.ServiceModel.ConcurrencyMode> is <xref:System.ServiceModel.ConcurrencyMode.Single>, because <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute on service B is on "more derived" than that on service A.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="a1771-226">合約行為</span><span class="sxs-lookup"><span data-stu-id="a1771-226">Contract Behaviors</span></span>  
 <span data-ttu-id="a1771-227">對於指定的合約，將套用該介面及其父代上的所有合約行為屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-227">For a given contract, all contract behavior attributes on that interface and on parents of that interface, are applied.</span></span> <span data-ttu-id="a1771-228">如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。</span><span class="sxs-lookup"><span data-stu-id="a1771-228">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="a1771-229">作業行為</span><span class="sxs-lookup"><span data-stu-id="a1771-229">Operation Behaviors</span></span>  
 <span data-ttu-id="a1771-230">如果指定的作業沒有覆寫現有的抽象或虛擬作業，就不會套用任何繼承規則。</span><span class="sxs-lookup"><span data-stu-id="a1771-230">If a given operation does not override an existing abstract or virtual operation, no inheritance rules apply.</span></span>  
  
 <span data-ttu-id="a1771-231">如果作業確實覆寫了現有的作業，這時將套用該作業及其父代上的所有作業行為屬性。</span><span class="sxs-lookup"><span data-stu-id="a1771-231">If an operation does override an existing operation, then all operation behavior attributes on that operation and on parents of that operation, are applied.</span></span>  <span data-ttu-id="a1771-232">如果相同型別的屬性套用在繼承階層架構的多個位置，這時會使用最具衍生性的型別。</span><span class="sxs-lookup"><span data-stu-id="a1771-232">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>
