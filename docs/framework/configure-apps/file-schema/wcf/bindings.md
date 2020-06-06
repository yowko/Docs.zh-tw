---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139671"
---
# \<bindings>

<span data-ttu-id="81be7-101">您可以使用 `bindings` 元素來設定 Windows Communication Foundation （WCF）的標準和自訂系結集合。</span><span class="sxs-lookup"><span data-stu-id="81be7-101">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="81be7-102">每個項目都是 `binding` 項目，可由其唯一的 `name` 所識別。</span><span class="sxs-lookup"><span data-stu-id="81be7-102">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="81be7-103">服務會使用 `name` 來連結繫結，以便利用繫結。</span><span class="sxs-lookup"><span data-stu-id="81be7-103">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="81be7-104">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="81be7-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="81be7-105">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="81be7-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="81be7-106">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="81be7-106">System-provided bindings</span></span>

<span data-ttu-id="81be7-107">系統提供的繫結會隱藏 WCF 訊息堆疊的複雜性。</span><span class="sxs-lookup"><span data-stu-id="81be7-107">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="81be7-108">使用系統提供之繫結的應用程式不需要對堆疊有完整控制權。</span><span class="sxs-lookup"><span data-stu-id="81be7-108">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="81be7-109">在每個系統提供之繫結上公開的屬性，最適合繫結所處理的使用案例。</span><span class="sxs-lookup"><span data-stu-id="81be7-109">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="81be7-110">每個系統提供之繫結的組態區段可定義用於設定繫結的多個組態。</span><span class="sxs-lookup"><span data-stu-id="81be7-110">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="81be7-111">每個組態是由唯一的名稱來識別。</span><span class="sxs-lookup"><span data-stu-id="81be7-111">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="81be7-112">您無法將元素或屬性加入至系統提供的系結。</span><span class="sxs-lookup"><span data-stu-id="81be7-112">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="81be7-113">若要這樣做，您應該執行自訂系結，如[自訂](#custom-bindings)系結一節中所述。</span><span class="sxs-lookup"><span data-stu-id="81be7-113">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="81be7-114">您可以定義自訂系結，以完美模擬系統提供的系結，並新增使用者應用程式想要控制的幾個設定。</span><span class="sxs-lookup"><span data-stu-id="81be7-114">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="81be7-115">如需系統提供之系結的清單，請參閱[系統提供](../../../wcf/system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="81be7-115">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="81be7-116">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="81be7-116">Custom bindings</span></span>

<span data-ttu-id="81be7-117">自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="81be7-117">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="81be7-118">個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。</span><span class="sxs-lookup"><span data-stu-id="81be7-118">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="81be7-119">每個元素都會定義和設定堆疊的一個元素。</span><span class="sxs-lookup"><span data-stu-id="81be7-119">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="81be7-120">各個自訂繫結中一定要出現一個而且是唯一一個 `transport` 項目。</span><span class="sxs-lookup"><span data-stu-id="81be7-120">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="81be7-121">如果沒有這個項目，訊息堆疊就不完整。</span><span class="sxs-lookup"><span data-stu-id="81be7-121">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="81be7-122">項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。</span><span class="sxs-lookup"><span data-stu-id="81be7-122">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="81be7-123">建議的堆疊項目順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="81be7-123">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="81be7-124">交易 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="81be7-124">Transactions (optional)</span></span>  

2. <span data-ttu-id="81be7-125">可靠的訊息處理（選擇性）</span><span class="sxs-lookup"><span data-stu-id="81be7-125">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="81be7-126">安全性 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="81be7-126">Security (optional)</span></span>  

4. <span data-ttu-id="81be7-127">編碼器</span><span class="sxs-lookup"><span data-stu-id="81be7-127">Encoder</span></span>  

5. <span data-ttu-id="81be7-128">傳輸</span><span class="sxs-lookup"><span data-stu-id="81be7-128">Transport</span></span>  

 <span data-ttu-id="81be7-129">自訂繫結是由其 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="81be7-129">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="81be7-130">如需自訂系結的詳細資訊，請參閱[自訂](../../../wcf/extending/custom-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="81be7-130">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="81be7-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81be7-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="81be7-132">繫結</span><span class="sxs-lookup"><span data-stu-id="81be7-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="81be7-133">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="81be7-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
