---
title: <NetFx40_PInvokeStackResilience> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 318473d2913d62404c58b9d3681800ae22a9ecbf
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689858"
---
# <a name="netfx40pinvokestackresilience-element"></a><span data-ttu-id="81c1f-102">\<NetFx40_PInvokeStackResilience > 項目</span><span class="sxs-lookup"><span data-stu-id="81c1f-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="81c1f-103">指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。</span><span class="sxs-lookup"><span data-stu-id="81c1f-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

<span data-ttu-id="81c1f-104">\<configuration>\\</span><span class="sxs-lookup"><span data-stu-id="81c1f-104">\<configuration>\\</span></span>
<span data-ttu-id="81c1f-105">\<runtime>\\</span><span class="sxs-lookup"><span data-stu-id="81c1f-105">\<runtime>\\</span></span>
<span data-ttu-id="81c1f-106">\<NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="81c1f-106">\<NetFx40_PInvokeStackResilience></span></span>

## <a name="syntax"></a><span data-ttu-id="81c1f-107">語法</span><span class="sxs-lookup"><span data-stu-id="81c1f-107">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="81c1f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="81c1f-108">Attributes and Elements</span></span>

<span data-ttu-id="81c1f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="81c1f-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="81c1f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="81c1f-110">Attributes</span></span>

|<span data-ttu-id="81c1f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="81c1f-111">Attribute</span></span>|<span data-ttu-id="81c1f-112">描述</span><span class="sxs-lookup"><span data-stu-id="81c1f-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="81c1f-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="81c1f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="81c1f-114">指定是否執行階段偵測到不正確的平台叫用宣告，並在 32 位元平台上自動修正在執行階段的堆疊。</span><span class="sxs-lookup"><span data-stu-id="81c1f-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="81c1f-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="81c1f-115">enabled Attribute</span></span>

|<span data-ttu-id="81c1f-116">值</span><span class="sxs-lookup"><span data-stu-id="81c1f-116">Value</span></span>|<span data-ttu-id="81c1f-117">描述</span><span class="sxs-lookup"><span data-stu-id="81c1f-117">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="81c1f-118">執行階段會使用更快速的 interop 封送處理不會偵測.NET Framework 4 中導入的架構，並修正不正確的平台叫用宣告。</span><span class="sxs-lookup"><span data-stu-id="81c1f-118">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="81c1f-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="81c1f-119">This is the default.</span></span>|
|`1`|<span data-ttu-id="81c1f-120">執行階段使用的轉換變慢，偵測並修正不正確的平台叫用宣告。</span><span class="sxs-lookup"><span data-stu-id="81c1f-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="81c1f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="81c1f-121">Child Elements</span></span>

<span data-ttu-id="81c1f-122">無。</span><span class="sxs-lookup"><span data-stu-id="81c1f-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="81c1f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="81c1f-123">Parent Elements</span></span>

|<span data-ttu-id="81c1f-124">項目</span><span class="sxs-lookup"><span data-stu-id="81c1f-124">Element</span></span>|<span data-ttu-id="81c1f-125">描述</span><span class="sxs-lookup"><span data-stu-id="81c1f-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="81c1f-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="81c1f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="81c1f-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="81c1f-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="81c1f-128">備註</span><span class="sxs-lookup"><span data-stu-id="81c1f-128">Remarks</span></span>

<span data-ttu-id="81c1f-129">這個項目可讓您更快 interop 封送處理的執行階段彈性，針對不正確的平台叫用宣告的交換。</span><span class="sxs-lookup"><span data-stu-id="81c1f-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="81c1f-130">從.NET Framework 4 開始，簡化的 interop 封送處理架構，提供從 managed 程式碼會轉換成 unmanaged 程式碼的顯著效能改善。</span><span class="sxs-lookup"><span data-stu-id="81c1f-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="81c1f-131">在舊版的.NET Framework 中，封送處理層偵測到不正確的平台叫用 32 位元平台上的宣告，並自動修正堆疊。</span><span class="sxs-lookup"><span data-stu-id="81c1f-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="81c1f-132">新的封送處理架構會移除此步驟。</span><span class="sxs-lookup"><span data-stu-id="81c1f-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="81c1f-133">如此一來，轉換會非常快速，但不正確的平台叫用宣告可能會導致程式失敗。</span><span class="sxs-lookup"><span data-stu-id="81c1f-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="81c1f-134">若要讓您輕鬆地在開發期間偵測不正確的宣告，已改善 Visual Studio 偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="81c1f-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="81c1f-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed 偵錯助理 (MDA) 會通知您有不正確的平台叫用宣告，以附加偵錯工具在您的應用程式執行時。</span><span class="sxs-lookup"><span data-stu-id="81c1f-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="81c1f-136">若要解決此類情況： 您的應用程式使用元件，您無法重新編譯，，有不正確的平台叫用宣告，您可以使用`NetFx40_PInvokeStackResilience`項目。</span><span class="sxs-lookup"><span data-stu-id="81c1f-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="81c1f-137">將這個項目新增至您的應用程式組態檔`enabled="1"`相容性模式與舊版.NET Framework 中，但要付出的轉換變慢的行為。</span><span class="sxs-lookup"><span data-stu-id="81c1f-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="81c1f-138">針對舊版.NET Framework 的已編譯的組件會自動加入此相容性模式中，而且不需要這個項目。</span><span class="sxs-lookup"><span data-stu-id="81c1f-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="81c1f-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="81c1f-139">Configuration File</span></span>

<span data-ttu-id="81c1f-140">此元素只用於應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="81c1f-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="81c1f-141">範例</span><span class="sxs-lookup"><span data-stu-id="81c1f-141">Example</span></span>

<span data-ttu-id="81c1f-142">下列範例示範如何針對不正確的提升恢復能力選擇平台叫用的應用程式，但代價是之間的轉換變慢的宣告 managed 和 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="81c1f-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="81c1f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81c1f-143">See also</span></span>

- [<span data-ttu-id="81c1f-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="81c1f-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="81c1f-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="81c1f-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="81c1f-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="81c1f-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
