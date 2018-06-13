---
title: '&lt;NetFx40_PInvokeStackResilience&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cfd8c971edd4537de6e073c49f128f86eb8a042
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748993"
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a><span data-ttu-id="6ba7a-102">&lt;NetFx40_PInvokeStackResilience&gt;項目</span><span class="sxs-lookup"><span data-stu-id="6ba7a-102">&lt;NetFx40_PInvokeStackResilience&gt; Element</span></span>
<span data-ttu-id="6ba7a-103">指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-103">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="6ba7a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6ba7a-104">\<configuration></span></span>  
<span data-ttu-id="6ba7a-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="6ba7a-105">\<runtime></span></span>  
<span data-ttu-id="6ba7a-106">< NetFx40_PInvokeStackResilience ></span><span class="sxs-lookup"><span data-stu-id="6ba7a-106"><NetFx40_PInvokeStackResilience></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba7a-107">語法</span><span class="sxs-lookup"><span data-stu-id="6ba7a-107">Syntax</span></span>  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ba7a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6ba7a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6ba7a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ba7a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6ba7a-110">Attributes</span></span>  
  
|<span data-ttu-id="6ba7a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6ba7a-111">Attribute</span></span>|<span data-ttu-id="6ba7a-112">描述</span><span class="sxs-lookup"><span data-stu-id="6ba7a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6ba7a-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6ba7a-114">指定是否執行階段偵測到不正確的平台叫用宣告，並自動在執行階段在 32 位元平台上修正堆疊。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-114">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6ba7a-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="6ba7a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6ba7a-116">值</span><span class="sxs-lookup"><span data-stu-id="6ba7a-116">Value</span></span>|<span data-ttu-id="6ba7a-117">描述</span><span class="sxs-lookup"><span data-stu-id="6ba7a-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="6ba7a-118">執行階段會更快的 interop 封送處理架構中導入[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、 其中不會偵測及修正不正確的平台叫用宣告。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-118">The runtime uses the faster interop marshaling architecture introduced in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="6ba7a-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="6ba7a-120">執行階段會使用速度較慢轉換偵測及修正不正確的平台叫用宣告。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-120">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ba7a-121">子項目</span><span class="sxs-lookup"><span data-stu-id="6ba7a-121">Child Elements</span></span>  
 <span data-ttu-id="6ba7a-122">無。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ba7a-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6ba7a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6ba7a-124">項目</span><span class="sxs-lookup"><span data-stu-id="6ba7a-124">Element</span></span>|<span data-ttu-id="6ba7a-125">描述</span><span class="sxs-lookup"><span data-stu-id="6ba7a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6ba7a-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6ba7a-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ba7a-128">備註</span><span class="sxs-lookup"><span data-stu-id="6ba7a-128">Remarks</span></span>  
 <span data-ttu-id="6ba7a-129">這個項目可讓您更快速 interop 封送處理為執行時期恢復功能，針對不正確的平台叫用宣告進行交易。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-129">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>  
  
 <span data-ttu-id="6ba7a-130">從開始[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，簡化的 interop 封送處理架構提供從 managed 程式碼會轉換成 unmanaged 程式碼的效能大幅提升。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="6ba7a-131">在舊版的.NET Framework 中，封送處理的層級偵測到不正確平台叫用 32 位元平台上的宣告，並自動修正堆疊。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-131">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="6ba7a-132">新的封送處理架構會移除此步驟。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-132">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="6ba7a-133">如此一來，轉換會非常快速，但不正確的平台叫用宣告可能會導致程式失敗。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-133">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>  
  
 <span data-ttu-id="6ba7a-134">若要可讓您輕鬆偵測不正確的宣告，在開發期間，Visual Studio 偵錯體驗已經過改良。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-134">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="6ba7a-135">[PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed 偵錯助理 (MDA) 會通知您不正確的平台叫用宣告附加了偵錯工具執行您的應用程式時。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-135">The [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>  
  
 <span data-ttu-id="6ba7a-136">您的應用程式使用的元件，您無法重新編譯，，有不正確的平台叫用宣告，您可以使用位置的位址案例`NetFx40_PInvokeStackResilience`項目。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-136">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="6ba7a-137">將這個項目加入至應用程式組態檔與`enabled="1"`opts 為相容性模式，與舊版的.NET Framework 中，但要付出速度較慢的轉換行為。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-137">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="6ba7a-138">針對舊版.NET Framework 的已編譯的組件會自動選擇加入此相容性模式中，而且不需要這個項目。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-138">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="6ba7a-139">組態檔</span><span class="sxs-lookup"><span data-stu-id="6ba7a-139">Configuration File</span></span>  
 <span data-ttu-id="6ba7a-140">此項目只能用於應用程式組態檔中。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-140">This element can be used only in the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ba7a-141">範例</span><span class="sxs-lookup"><span data-stu-id="6ba7a-141">Example</span></span>  
 <span data-ttu-id="6ba7a-142">下列範例會示範如何針對不正確的增加彈性選擇平台叫用的應用程式，但要付出之間的速度較慢轉換宣告 managed 和 unmanaged 程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ba7a-142">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ba7a-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ba7a-143">See Also</span></span>  
 [<span data-ttu-id="6ba7a-144">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6ba7a-144">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="6ba7a-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6ba7a-145">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="6ba7a-146">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="6ba7a-146">pInvokeStackImbalance</span></span>](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
