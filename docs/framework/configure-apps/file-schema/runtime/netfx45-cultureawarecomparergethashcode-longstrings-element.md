---
title: '&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 41fc4bc7a6a10a6f99752112f951b66f80d493fe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754180"
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a><span data-ttu-id="188be-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt;項目</span><span class="sxs-lookup"><span data-stu-id="188be-102">&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; Element</span></span>
<span data-ttu-id="188be-103">指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="188be-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="188be-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="188be-104">\<configuration></span></span>  
<span data-ttu-id="188be-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="188be-105">\<runtime></span></span>  
<span data-ttu-id="188be-106">< NetFx45_CultureAwareComparerGetHashCode_LongStrings ></span><span class="sxs-lookup"><span data-stu-id="188be-106"><NetFx45_CultureAwareComparerGetHashCode_LongStrings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="188be-107">語法</span><span class="sxs-lookup"><span data-stu-id="188be-107">Syntax</span></span>  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="188be-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="188be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="188be-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="188be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="188be-110">屬性</span><span class="sxs-lookup"><span data-stu-id="188be-110">Attributes</span></span>  
  
|<span data-ttu-id="188be-111">屬性</span><span class="sxs-lookup"><span data-stu-id="188be-111">Attribute</span></span>|<span data-ttu-id="188be-112">描述</span><span class="sxs-lookup"><span data-stu-id="188be-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="188be-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="188be-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="188be-114">指定通用語言執行平台是否會在計算雜湊碼時配置固定數量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="188be-114">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="188be-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="188be-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="188be-116">值</span><span class="sxs-lookup"><span data-stu-id="188be-116">Value</span></span>|<span data-ttu-id="188be-117">描述</span><span class="sxs-lookup"><span data-stu-id="188be-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="188be-118">0</span><span class="sxs-lookup"><span data-stu-id="188be-118">0</span></span>|<span data-ttu-id="188be-119">通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置可變的記憶體數量來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="188be-119">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="188be-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="188be-120">This is the default.</span></span>|  
|<span data-ttu-id="188be-121">1</span><span class="sxs-lookup"><span data-stu-id="188be-121">1</span></span>|<span data-ttu-id="188be-122">通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置固定的記憶體數量來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="188be-122">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="188be-123">子項目</span><span class="sxs-lookup"><span data-stu-id="188be-123">Child Elements</span></span>  
 <span data-ttu-id="188be-124">無。</span><span class="sxs-lookup"><span data-stu-id="188be-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="188be-125">父項目</span><span class="sxs-lookup"><span data-stu-id="188be-125">Parent Elements</span></span>  
  
|<span data-ttu-id="188be-126">項目</span><span class="sxs-lookup"><span data-stu-id="188be-126">Element</span></span>|<span data-ttu-id="188be-127">描述</span><span class="sxs-lookup"><span data-stu-id="188be-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="188be-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="188be-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="188be-129">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="188be-129">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="188be-130">備註</span><span class="sxs-lookup"><span data-stu-id="188be-130">Remarks</span></span>  
 <span data-ttu-id="188be-131">根據預設，通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置可變的記憶體數量，因此，當方法嘗試計算長度超過數百萬個字元的超大型字串雜湊碼時，就可能擲回 <xref:System.ArgumentException>。</span><span class="sxs-lookup"><span data-stu-id="188be-131">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="188be-132">藉由將這個項目加入至應用程式組態檔，並將其 `enabled` 屬性設定為 "1"，就可以指定 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法使用替代演算法配置固定的記憶體數量來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="188be-132">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="188be-133">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` 項目不會在 [!INCLUDE[win8](../../../../../includes/win8-md.md)] (含) 以後版本中使用。</span><span class="sxs-lookup"><span data-stu-id="188be-133">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in [!INCLUDE[win8](../../../../../includes/win8-md.md)] and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="188be-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="188be-134">See Also</span></span>  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="188be-135">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="188be-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="188be-136">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="188be-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
