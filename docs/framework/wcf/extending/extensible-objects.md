---
title: 可延伸物件
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: 1af44f2394bbf27f9219831612b4e73d7a1759e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220275"
---
# <a name="extensible-objects"></a><span data-ttu-id="dd06a-102">可延伸物件</span><span class="sxs-lookup"><span data-stu-id="dd06a-102">Extensible Objects</span></span>
<span data-ttu-id="dd06a-103">可延伸物件模式是用於以新功能延伸現有的執行階段類別，或將新狀態新增至物件。</span><span class="sxs-lookup"><span data-stu-id="dd06a-103">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="dd06a-104">附加至其中一個可擴充物件的擴充功能會在處理程序中的各種不同階段啟用行為，以存取附加至它們可存取之一般可擴充物件的共用狀態與功能。</span><span class="sxs-lookup"><span data-stu-id="dd06a-104">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
## <a name="the-iextensibleobjectt-pattern"></a><span data-ttu-id="dd06a-105">IExtensibleObject\<T > 模式</span><span class="sxs-lookup"><span data-stu-id="dd06a-105">The IExtensibleObject\<T> Pattern</span></span>  
 <span data-ttu-id="dd06a-106">在可延伸物件模式中有三種介面：<xref:System.ServiceModel.IExtensibleObject%601>、<xref:System.ServiceModel.IExtension%601> 和 <xref:System.ServiceModel.IExtensionCollection%601>。</span><span class="sxs-lookup"><span data-stu-id="dd06a-106">There are three interfaces in the extensible object pattern: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, and <xref:System.ServiceModel.IExtensionCollection%601>.</span></span>  
  
 <span data-ttu-id="dd06a-107"><xref:System.ServiceModel.IExtensibleObject%601> 介面是由允許 <xref:System.ServiceModel.IExtension%601> 物件自訂其功能的類型所實作的。</span><span class="sxs-lookup"><span data-stu-id="dd06a-107">The <xref:System.ServiceModel.IExtensibleObject%601> interface is implemented by types that allow <xref:System.ServiceModel.IExtension%601> objects to customize their functionality.</span></span>  
  
 <span data-ttu-id="dd06a-108">可延伸物件允許 <xref:System.ServiceModel.IExtension%601> 物件的動態彙總。</span><span class="sxs-lookup"><span data-stu-id="dd06a-108">Extensible objects allow dynamic aggregation of <xref:System.ServiceModel.IExtension%601> objects.</span></span> <xref:System.ServiceModel.IExtension%601> <span data-ttu-id="dd06a-109">物件是由下列介面描述特徵：</span><span class="sxs-lookup"><span data-stu-id="dd06a-109">objects are characterized by the following interface:</span></span>  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 <span data-ttu-id="dd06a-110">類型限制可保證只能定義做為 <xref:System.ServiceModel.IExtensibleObject%601> 之類別的延伸。</span><span class="sxs-lookup"><span data-stu-id="dd06a-110">The type restriction guarantees that extensions can only be defined for classes that are <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <xref:System.ServiceModel.IExtension%601.Attach%2A> <span data-ttu-id="dd06a-111">和<xref:System.ServiceModel.IExtension%601.Detach%2A>提供彙總或分解的通知。</span><span class="sxs-lookup"><span data-stu-id="dd06a-111">and <xref:System.ServiceModel.IExtension%601.Detach%2A> provide notification of aggregation or disaggregation.</span></span>  
  
 <span data-ttu-id="dd06a-112">對於限制何時可新增及從擁有者中移除的實作是有效的。</span><span class="sxs-lookup"><span data-stu-id="dd06a-112">It is valid for implementations to restrict when they may be added and removed from an owner.</span></span> <span data-ttu-id="dd06a-113">例如，您可以不允許整個移除、不允許在擁有者或延伸處於特定狀態時新增或移除延伸、不允許同時新增多個擁有者，或只允許單一新增後接著單一移除。</span><span class="sxs-lookup"><span data-stu-id="dd06a-113">For example, you can disallow removal entirely, disallowing adding or removing extensions when the owner or extension are in a certain state, disallow adding to multiple owners concurrently, or allow only a single addition followed by a single remove.</span></span>  
  
 <xref:System.ServiceModel.IExtension%601> <span data-ttu-id="dd06a-114">不代表任何其他標準 managed 介面的互動。</span><span class="sxs-lookup"><span data-stu-id="dd06a-114">does not imply any interactions with other standard managed interfaces.</span></span> <span data-ttu-id="dd06a-115">特別是，擁有者物件上的 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 方法通常不會中斷連結它的延伸。</span><span class="sxs-lookup"><span data-stu-id="dd06a-115">Specifically, the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> method on the owner object does not normally detach its extensions.</span></span>  
  
 <span data-ttu-id="dd06a-116">當延伸新增至集合中，<xref:System.ServiceModel.IExtension%601.Attach%2A>它進入集合之前呼叫。</span><span class="sxs-lookup"><span data-stu-id="dd06a-116">When an extension is added to the collection, <xref:System.ServiceModel.IExtension%601.Attach%2A> is called before it goes into the collection.</span></span> <span data-ttu-id="dd06a-117">從集合中，移除延伸模組時<xref:System.ServiceModel.IExtension%601.Detach%2A>移除後予以呼叫。</span><span class="sxs-lookup"><span data-stu-id="dd06a-117">When an extension is removed from the collection, <xref:System.ServiceModel.IExtension%601.Detach%2A> is called after it is removed.</span></span> <span data-ttu-id="dd06a-118">這表示 （假定適當的同步處理） 延伸模組可以倚賴只有要在集合中找到時是之間<xref:System.ServiceModel.IExtension%601.Attach%2A>和<xref:System.ServiceModel.IExtension%601.Detach%2A>。</span><span class="sxs-lookup"><span data-stu-id="dd06a-118">This means (assuming appropriate synchronization) an extension can count on only being found in the collection while it is between <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A>.</span></span>  
  
 <span data-ttu-id="dd06a-119">傳遞至 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> 或 <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> 的物件不需要是 <xref:System.ServiceModel.IExtension%601> (例如，您可以傳遞任何物件)，但是傳回的延伸是 <xref:System.ServiceModel.IExtension%601>。</span><span class="sxs-lookup"><span data-stu-id="dd06a-119">The object passed to <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> or <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> need not be <xref:System.ServiceModel.IExtension%601> (for example, you can pass any object), but the returned extension is an <xref:System.ServiceModel.IExtension%601>.</span></span>  
  
 <span data-ttu-id="dd06a-120">如果在集合中的不含副檔名<xref:System.ServiceModel.IExtension%601>，<xref:System.ServiceModel.IExtensionCollection%601.Find%2A>會傳回 null，和<xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A>傳回空集合。</span><span class="sxs-lookup"><span data-stu-id="dd06a-120">If no extension in the collection is an <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> returns null, and <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> returns an empty collection.</span></span> <span data-ttu-id="dd06a-121">如果多個延伸模組實作<xref:System.ServiceModel.IExtension%601>，<xref:System.ServiceModel.IExtensionCollection%601.Find%2A>傳回其中一個。</span><span class="sxs-lookup"><span data-stu-id="dd06a-121">If multiple extensions implement <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> returns one of them.</span></span> <span data-ttu-id="dd06a-122">從 <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> 傳回的值是快照。</span><span class="sxs-lookup"><span data-stu-id="dd06a-122">The value returned from <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> is a snapshot.</span></span>
  
 <span data-ttu-id="dd06a-123">有兩個主要案例。</span><span class="sxs-lookup"><span data-stu-id="dd06a-123">There are two main scenarios.</span></span> <span data-ttu-id="dd06a-124">第一個案例是使用 <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> 屬性做為型別字典，將狀態插入物件，讓另一個元件可使用型別來查閱它。</span><span class="sxs-lookup"><span data-stu-id="dd06a-124">The first scenario uses the <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> property as a type-based dictionary to insert state on an object to enable another component to look it up using the type.</span></span>  
  
 <span data-ttu-id="dd06a-125">第二個案例是使用 <xref:System.ServiceModel.IExtension%601.Attach%2A> 和 <xref:System.ServiceModel.IExtension%601.Detach%2A> 屬性，讓物件可參與自訂行為，例如註冊事件、監看狀態轉換等等。</span><span class="sxs-lookup"><span data-stu-id="dd06a-125">The second scenario uses the <xref:System.ServiceModel.IExtension%601.Attach%2A> and <xref:System.ServiceModel.IExtension%601.Detach%2A> properties to enable an object to participate in custom behavior, such as registering for events, watching state transitions, and so on.</span></span>  
  
 <span data-ttu-id="dd06a-126"><xref:System.ServiceModel.IExtensionCollection%601> 介面是 <xref:System.ServiceModel.IExtension%601> 物件的集合，這些物件允許依據 <xref:System.ServiceModel.IExtension%601> 的型別將其擷取。</span><span class="sxs-lookup"><span data-stu-id="dd06a-126">The <xref:System.ServiceModel.IExtensionCollection%601> interface is a collection of the <xref:System.ServiceModel.IExtension%601> objects that allow for retrieving the <xref:System.ServiceModel.IExtension%601> by its type.</span></span> <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> <span data-ttu-id="dd06a-127">傳回最近新增的物件，該物件<xref:System.ServiceModel.IExtension%601>該類型。</span><span class="sxs-lookup"><span data-stu-id="dd06a-127">returns the most recently added object that is an <xref:System.ServiceModel.IExtension%601> of that type.</span></span>  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a><span data-ttu-id="dd06a-128">Windows Communication Foundation 中的可延伸物件</span><span class="sxs-lookup"><span data-stu-id="dd06a-128">Extensible Objects in Windows Communication Foundation</span></span>  
 <span data-ttu-id="dd06a-129">Windows Communication Foundation (WCF) 中有四個可延伸的物件：</span><span class="sxs-lookup"><span data-stu-id="dd06a-129">There are four extensible objects in Windows Communication Foundation (WCF):</span></span>  
  
-   <xref:System.ServiceModel.ServiceHostBase> <span data-ttu-id="dd06a-130">– 這是服務的主控件的基底類別。</span><span class="sxs-lookup"><span data-stu-id="dd06a-130">– This is the base class for the service’s host.</span></span>  <span data-ttu-id="dd06a-131">這個類別的延伸可用於延伸 <xref:System.ServiceModel.ServiceHostBase> 本身的行為，或儲存各服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="dd06a-131">Extensions of this class can be used to extend the behavior of the <xref:System.ServiceModel.ServiceHostBase> itself or to store the state for each service.</span></span>  
  
-   <xref:System.ServiceModel.InstanceContext> <span data-ttu-id="dd06a-132">– 這個類別會與服務執行階段連接的服務類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd06a-132">– This class connects an instance of the service’s type with the service runtime.</span></span>  <span data-ttu-id="dd06a-133">其中包含有關執行個體的資訊，以及包含 <xref:System.ServiceModel.InstanceContext> 之 <xref:System.ServiceModel.ServiceHostBase> 的參照。</span><span class="sxs-lookup"><span data-stu-id="dd06a-133">It contains information about the instance as well as a reference to the <xref:System.ServiceModel.InstanceContext>'s containing <xref:System.ServiceModel.ServiceHostBase>.</span></span> <span data-ttu-id="dd06a-134">這個類別的延伸可用於延伸 <xref:System.ServiceModel.InstanceContext> 的行為，或儲存各服務的狀態。</span><span class="sxs-lookup"><span data-stu-id="dd06a-134">Extensions of this class can be used to extend the behavior of the <xref:System.ServiceModel.InstanceContext> or to store the state for each service.</span></span>  
  
-   <xref:System.ServiceModel.OperationContext> <span data-ttu-id="dd06a-135">-此類別代表執行階段會收集每個作業的作業資訊。</span><span class="sxs-lookup"><span data-stu-id="dd06a-135">– This class represents the operation information that the runtime gathers for each operation.</span></span>  <span data-ttu-id="dd06a-136">其中包括的資訊如傳入訊息標頭、傳入訊息屬性、傳入安全性身分識別和其他資訊。</span><span class="sxs-lookup"><span data-stu-id="dd06a-136">This includes information such as the incoming message headers, the incoming message properties, the incoming security identity, and other information.</span></span>  <span data-ttu-id="dd06a-137">這個類別的延伸可以延伸 <xref:System.ServiceModel.OperationContext> 的行為，或儲存各作業的狀態。</span><span class="sxs-lookup"><span data-stu-id="dd06a-137">Extensions of this class can either extend the behavior of <xref:System.ServiceModel.OperationContext> or store the state for each operation.</span></span>  
  
-   <xref:System.ServiceModel.IContextChannel> <span data-ttu-id="dd06a-138">– 這個介面可讓每一個狀態的通道和 proxy 由 WCF 執行階段檢查。</span><span class="sxs-lookup"><span data-stu-id="dd06a-138">– This interface allows for the inspection of each state for the channels and proxies built by the WCF runtime.</span></span>  <span data-ttu-id="dd06a-139">這個類別的延伸可以延伸 <xref:System.ServiceModel.IClientChannel> 的行為，或可用它來儲存各通道的狀態。</span><span class="sxs-lookup"><span data-stu-id="dd06a-139">Extensions of this class can either extend the behavior of <xref:System.ServiceModel.IClientChannel> or can use it to store the state for each channel.</span></span>  
  
-  
  
 <span data-ttu-id="dd06a-140">下列程式碼範例將示範如何使用簡單的延伸來追蹤 <xref:System.ServiceModel.InstanceContext> 物件。</span><span class="sxs-lookup"><span data-stu-id="dd06a-140">The following code example shows the use of a simple extension to track <xref:System.ServiceModel.InstanceContext> objects.</span></span>  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="dd06a-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd06a-141">See also</span></span>

- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>
