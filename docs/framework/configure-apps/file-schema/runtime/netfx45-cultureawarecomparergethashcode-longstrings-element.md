---
title: <NetFx45_CultureAwareComparerGetHashCode_LongStrings> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
ms.openlocfilehash: 413eb6c6e61b509135601c65cf045eabd849e8b3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74802120"
---
# <a name="netfx45_cultureawarecomparergethashcode_longstrings-element"></a><span data-ttu-id="24337-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> 項目</span><span class="sxs-lookup"><span data-stu-id="24337-102">\<NetFx45_CultureAwareComparerGetHashCode_LongStrings> Element</span></span>

<span data-ttu-id="24337-103">指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="24337-103">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>**  

## <a name="syntax"></a><span data-ttu-id="24337-104">語法</span><span class="sxs-lookup"><span data-stu-id="24337-104">Syntax</span></span>

```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">
```

## <a name="attributes-and-elements"></a><span data-ttu-id="24337-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="24337-105">Attributes and Elements</span></span>

<span data-ttu-id="24337-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="24337-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="24337-107">屬性</span><span class="sxs-lookup"><span data-stu-id="24337-107">Attributes</span></span>

|<span data-ttu-id="24337-108">屬性</span><span class="sxs-lookup"><span data-stu-id="24337-108">Attribute</span></span>|<span data-ttu-id="24337-109">描述</span><span class="sxs-lookup"><span data-stu-id="24337-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="24337-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="24337-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="24337-111">指定通用語言執行平台是否會在計算雜湊碼時配置固定數量的記憶體。</span><span class="sxs-lookup"><span data-stu-id="24337-111">Specifies whether the common language runtime allocates a fixed amount of memory when calculating hash codes.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="24337-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="24337-112">enabled Attribute</span></span>

|<span data-ttu-id="24337-113">值</span><span class="sxs-lookup"><span data-stu-id="24337-113">Value</span></span>|<span data-ttu-id="24337-114">描述</span><span class="sxs-lookup"><span data-stu-id="24337-114">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="24337-115">0</span><span class="sxs-lookup"><span data-stu-id="24337-115">0</span></span>|<span data-ttu-id="24337-116">通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置可變的記憶體數量來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="24337-116">The common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span> <span data-ttu-id="24337-117">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="24337-117">This is the default.</span></span>|
|<span data-ttu-id="24337-118">1</span><span class="sxs-lookup"><span data-stu-id="24337-118">1</span></span>|<span data-ttu-id="24337-119">通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置固定的記憶體數量來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="24337-119">The common language runtime allocates a fixed amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method to calculate hash codes.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="24337-120">子元素</span><span class="sxs-lookup"><span data-stu-id="24337-120">Child Elements</span></span>

<span data-ttu-id="24337-121">無。</span><span class="sxs-lookup"><span data-stu-id="24337-121">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="24337-122">父項目</span><span class="sxs-lookup"><span data-stu-id="24337-122">Parent Elements</span></span>

|<span data-ttu-id="24337-123">元素</span><span class="sxs-lookup"><span data-stu-id="24337-123">Element</span></span>|<span data-ttu-id="24337-124">描述</span><span class="sxs-lookup"><span data-stu-id="24337-124">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="24337-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="24337-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="24337-126">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="24337-126">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="24337-127">備註</span><span class="sxs-lookup"><span data-stu-id="24337-127">Remarks</span></span>

<span data-ttu-id="24337-128">根據預設，通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法配置可變的記憶體數量，因此，當方法嘗試計算長度超過數百萬個字元的超大型字串雜湊碼時，就可能擲回 <xref:System.ArgumentException> 。</span><span class="sxs-lookup"><span data-stu-id="24337-128">By default, the common language runtime allocates a variable amount of memory for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method, and an <xref:System.ArgumentException> can be thrown when the method attempts to compute the hash code of very large strings (over several million characters long).</span></span> <span data-ttu-id="24337-129">藉由將這個項目加入至應用程式組態檔，並將其 `enabled` 屬性設定為 "1"，就可以指定 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法使用替代演算法配置固定的記憶體數量來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="24337-129">By adding this element to an application configuration file and setting its `enabled` attribute to "1", you can specify that the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method use an alternate algorithm that allocates a fixed amount of memory for the computation of hash codes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24337-130">`<NetFx45_CultureAwareComparerGetHashCode_LongStrings>`Windows 8 和更新版本中不會使用此元素。</span><span class="sxs-lookup"><span data-stu-id="24337-130">The `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` element is not used in Windows 8 and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="24337-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24337-131">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- [<span data-ttu-id="24337-132">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="24337-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="24337-133">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="24337-133">Configuration File Schema</span></span>](../index.md)
