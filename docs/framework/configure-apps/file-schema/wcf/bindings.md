---
title: <bindings>
ms.date: 03/30/2017
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 4a952ff5a8dd39a5615aa17f15229557bbd0f41f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257300"
---
# <a name="bindings"></a><span data-ttu-id="caa95-101">\<bindings></span><span class="sxs-lookup"><span data-stu-id="caa95-101">\<bindings></span></span>
<span data-ttu-id="caa95-102">這個區段保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="caa95-102">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="caa95-103">每個項目都是 `binding` 項目，可由其唯一的 `name` 所識別。</span><span class="sxs-lookup"><span data-stu-id="caa95-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="caa95-104">服務會使用 `name` 來連結繫結，以便利用繫結。</span><span class="sxs-lookup"><span data-stu-id="caa95-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="caa95-105">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="caa95-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="caa95-106">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="caa95-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="caa95-107">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="caa95-107">System-Provided Binding</span></span>  
 <span data-ttu-id="caa95-108">系統提供的繫結會隱藏 WCF 訊息堆疊的複雜性。</span><span class="sxs-lookup"><span data-stu-id="caa95-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="caa95-109">使用系統提供之繫結的應用程式不需要對堆疊有完整控制權。</span><span class="sxs-lookup"><span data-stu-id="caa95-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="caa95-110">在每個系統提供之繫結上公開的屬性，最適合繫結所處理的使用案例。</span><span class="sxs-lookup"><span data-stu-id="caa95-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="caa95-111">每個系統提供之繫結的組態區段可定義用於設定繫結的多個組態。</span><span class="sxs-lookup"><span data-stu-id="caa95-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="caa95-112">每個組態是由唯一的名稱來識別。</span><span class="sxs-lookup"><span data-stu-id="caa95-112">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="caa95-113">您無法在系統提供的繫結中加入項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="caa95-113">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="caa95-114">若要這麼做，您應實作自訂繫結，如本主題的「自訂繫結」一節所述。</span><span class="sxs-lookup"><span data-stu-id="caa95-114">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="caa95-115">您可以定義完全仿照系統提供之繫結的自訂繫結，並在其中加入一些使用者應用程式要有控制權的設定。</span><span class="sxs-lookup"><span data-stu-id="caa95-115">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="caa95-116">如需系統提供繫結的清單，請參閱 < [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="caa95-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="caa95-117">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="caa95-117">Custom Binding</span></span>  
 <span data-ttu-id="caa95-118">自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="caa95-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="caa95-119">個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。</span><span class="sxs-lookup"><span data-stu-id="caa95-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="caa95-120">每個項目都會定義及設定堆疊的一個項目。</span><span class="sxs-lookup"><span data-stu-id="caa95-120">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="caa95-121">各個自訂繫結中一定要出現一個而且是唯一一個 `transport` 項目。</span><span class="sxs-lookup"><span data-stu-id="caa95-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="caa95-122">如果沒有這個項目，訊息堆疊就不完整。</span><span class="sxs-lookup"><span data-stu-id="caa95-122">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="caa95-123">項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。</span><span class="sxs-lookup"><span data-stu-id="caa95-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="caa95-124">建議的堆疊項目順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="caa95-124">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="caa95-125">交易 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="caa95-125">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="caa95-126">可信賴傳訊 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="caa95-126">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="caa95-127">安全性 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="caa95-127">Security (optional)</span></span>  
  
4.  <span data-ttu-id="caa95-128">編碼器</span><span class="sxs-lookup"><span data-stu-id="caa95-128">Encoder</span></span>  
  
5.  <span data-ttu-id="caa95-129">Transport</span><span class="sxs-lookup"><span data-stu-id="caa95-129">Transport</span></span>  
  
 <span data-ttu-id="caa95-130">自訂繫結是由其 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="caa95-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="caa95-131">如需有關自訂繫結的詳細資訊，請參閱 <<c0> [ 自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="caa95-131">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caa95-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="caa95-132">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="caa95-133">繫結</span><span class="sxs-lookup"><span data-stu-id="caa95-133">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="caa95-134">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="caa95-134">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="caa95-135">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="caa95-135">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="caa95-136">\<binding></span><span class="sxs-lookup"><span data-stu-id="caa95-136">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
