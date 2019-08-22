---
title: <NetFx40_PInvokeStackResilience> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf97cc1ec544c7cf640c43b1b45760fca8cffe89
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663548"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="63f39-102">\<NetFx40_PInvokeStackResilience > 元素</span><span class="sxs-lookup"><span data-stu-id="63f39-102">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="63f39-103">指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。</span><span class="sxs-lookup"><span data-stu-id="63f39-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

<span data-ttu-id="63f39-104">\<configuration > </span><span class="sxs-lookup"><span data-stu-id="63f39-104">\<configuration></span></span>\
<span data-ttu-id="63f39-105">\<執行時間 > </span><span class="sxs-lookup"><span data-stu-id="63f39-105">\<runtime></span></span>\
<span data-ttu-id="63f39-106">\<NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="63f39-106">\<NetFx40_PInvokeStackResilience></span></span>

## <a name="syntax"></a><span data-ttu-id="63f39-107">語法</span><span class="sxs-lookup"><span data-stu-id="63f39-107">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="63f39-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="63f39-108">Attributes and Elements</span></span>

<span data-ttu-id="63f39-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="63f39-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="63f39-110">屬性</span><span class="sxs-lookup"><span data-stu-id="63f39-110">Attributes</span></span>

|<span data-ttu-id="63f39-111">屬性</span><span class="sxs-lookup"><span data-stu-id="63f39-111">Attribute</span></span>|<span data-ttu-id="63f39-112">描述</span><span class="sxs-lookup"><span data-stu-id="63f39-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="63f39-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="63f39-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="63f39-114">指定執行時間是否偵測到不正確的平台叫用宣告, 並在32位平臺上自動修正執行時間的堆疊。</span><span class="sxs-lookup"><span data-stu-id="63f39-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="63f39-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="63f39-115">enabled Attribute</span></span>

|<span data-ttu-id="63f39-116">值</span><span class="sxs-lookup"><span data-stu-id="63f39-116">Value</span></span>|<span data-ttu-id="63f39-117">描述</span><span class="sxs-lookup"><span data-stu-id="63f39-117">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="63f39-118">執行時間會使用 .NET Framework 4 中引進的更快 interop 封送處理架構, 這不會偵測並修正不正確的平台叫用宣告。</span><span class="sxs-lookup"><span data-stu-id="63f39-118">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="63f39-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="63f39-119">This is the default.</span></span>|
|`1`|<span data-ttu-id="63f39-120">執行時間會使用較慢的轉換來偵測並修正不正確的平台叫用宣告。</span><span class="sxs-lookup"><span data-stu-id="63f39-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="63f39-121">子元素</span><span class="sxs-lookup"><span data-stu-id="63f39-121">Child Elements</span></span>

<span data-ttu-id="63f39-122">無。</span><span class="sxs-lookup"><span data-stu-id="63f39-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="63f39-123">父項目</span><span class="sxs-lookup"><span data-stu-id="63f39-123">Parent Elements</span></span>

|<span data-ttu-id="63f39-124">項目</span><span class="sxs-lookup"><span data-stu-id="63f39-124">Element</span></span>|<span data-ttu-id="63f39-125">描述</span><span class="sxs-lookup"><span data-stu-id="63f39-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="63f39-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="63f39-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="63f39-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="63f39-127">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="63f39-128">備註</span><span class="sxs-lookup"><span data-stu-id="63f39-128">Remarks</span></span>

<span data-ttu-id="63f39-129">此元素可讓您針對執行時間復原, 針對不正確的平台叫用宣告, 進行更快速的 interop 封送處理。</span><span class="sxs-lookup"><span data-stu-id="63f39-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="63f39-130">從 .NET Framework 4 開始, 簡化的 interop 封送處理架構可大幅改善從 managed 程式碼轉換為非受控碼的效能。</span><span class="sxs-lookup"><span data-stu-id="63f39-130">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="63f39-131">在舊版的 .NET Framework 中, 封送處理層在32位平臺上偵測到不正確的平台叫用宣告, 並自動修正堆疊。</span><span class="sxs-lookup"><span data-stu-id="63f39-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="63f39-132">新的封送處理架構會消除此步驟。</span><span class="sxs-lookup"><span data-stu-id="63f39-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="63f39-133">因此, 轉換會非常快速, 但不正確的平台叫用宣告可能會導致程式失敗。</span><span class="sxs-lookup"><span data-stu-id="63f39-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="63f39-134">為了讓您在開發過程中輕鬆偵測不正確的宣告, 已改善 Visual Studio 的偵錯工具體驗。</span><span class="sxs-lookup"><span data-stu-id="63f39-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="63f39-135">當您的應用程式是以附加的偵錯工具執行時, [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed 偵錯工具 (MDA) 會通知您不正確的平台叫用宣告。</span><span class="sxs-lookup"><span data-stu-id="63f39-135">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="63f39-136">若要處理您的應用程式使用無法重新編譯的元件, 且其平台叫用宣告不正確的情況, 您`NetFx40_PInvokeStackResilience`可以使用元素。</span><span class="sxs-lookup"><span data-stu-id="63f39-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="63f39-137">將此專案新增至您的應用程式`enabled="1"`設定檔, 並使用舊版 .NET Framework 的行為, 以較慢的轉換為代價, 將其加入至相容性模式。</span><span class="sxs-lookup"><span data-stu-id="63f39-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="63f39-138">已針對舊版 .NET Framework 編譯的元件會自動選擇進入此相容性模式, 而且不需要此元素。</span><span class="sxs-lookup"><span data-stu-id="63f39-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="63f39-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="63f39-139">Configuration File</span></span>

<span data-ttu-id="63f39-140">這個元素只能用在應用程式佈建檔中。</span><span class="sxs-lookup"><span data-stu-id="63f39-140">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="63f39-141">範例</span><span class="sxs-lookup"><span data-stu-id="63f39-141">Example</span></span>

<span data-ttu-id="63f39-142">下列範例示範如何針對應用程式的不正確平台叫用宣告, 選擇增加的復原能力, 代價是 managed 和非受控碼之間的轉換速度較慢。</span><span class="sxs-lookup"><span data-stu-id="63f39-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="63f39-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63f39-143">See also</span></span>

- [<span data-ttu-id="63f39-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="63f39-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="63f39-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="63f39-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="63f39-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="63f39-146">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
