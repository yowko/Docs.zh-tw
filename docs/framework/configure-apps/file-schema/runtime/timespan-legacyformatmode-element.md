---
title: <TimeSpan_LegacyFormatMode> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <TimeSpan_LegacyFormatMode> element
- TimeSpan_LegacyFormatMode element
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
ms.openlocfilehash: 9d9eedf52f5d711412e4549e39e6ea23abb68ff3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73968899"
---
# <a name="timespan_legacyformatmode-element"></a><span data-ttu-id="bd618-102">\<TimeSpan_LegacyFormatMode> 項目</span><span class="sxs-lookup"><span data-stu-id="bd618-102">\<TimeSpan_LegacyFormatMode> Element</span></span>

<span data-ttu-id="bd618-103">判斷執行時間是否會以值來保留格式化作業的舊版行為 <xref:System.TimeSpan?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="bd618-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<TimeSpan_LegacyFormatMode>**  

## <a name="syntax"></a><span data-ttu-id="bd618-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd618-104">Syntax</span></span>

```xml
<TimeSpan_LegacyFormatMode
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bd618-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bd618-105">Attributes and Elements</span></span>

<span data-ttu-id="bd618-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bd618-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="bd618-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bd618-107">Attributes</span></span>

|<span data-ttu-id="bd618-108">屬性</span><span class="sxs-lookup"><span data-stu-id="bd618-108">Attribute</span></span>|<span data-ttu-id="bd618-109">描述</span><span class="sxs-lookup"><span data-stu-id="bd618-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="bd618-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bd618-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="bd618-111">指定執行時間是否使用具有值的舊版格式行為 <xref:System.TimeSpan?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="bd618-111">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="bd618-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="bd618-112">enabled Attribute</span></span>

|<span data-ttu-id="bd618-113">值</span><span class="sxs-lookup"><span data-stu-id="bd618-113">Value</span></span>|<span data-ttu-id="bd618-114">描述</span><span class="sxs-lookup"><span data-stu-id="bd618-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="bd618-115">執行時間不會還原舊版格式設定行為。</span><span class="sxs-lookup"><span data-stu-id="bd618-115">The runtime does not restore legacy formatting behavior.</span></span>|
|`true`|<span data-ttu-id="bd618-116">執行時間會還原舊版格式設定行為。</span><span class="sxs-lookup"><span data-stu-id="bd618-116">The runtime restores legacy formatting behavior.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="bd618-117">子元素</span><span class="sxs-lookup"><span data-stu-id="bd618-117">Child Elements</span></span>

<span data-ttu-id="bd618-118">無。</span><span class="sxs-lookup"><span data-stu-id="bd618-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="bd618-119">父項目</span><span class="sxs-lookup"><span data-stu-id="bd618-119">Parent Elements</span></span>

|<span data-ttu-id="bd618-120">元素</span><span class="sxs-lookup"><span data-stu-id="bd618-120">Element</span></span>|<span data-ttu-id="bd618-121">描述</span><span class="sxs-lookup"><span data-stu-id="bd618-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="bd618-122">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="bd618-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="bd618-123">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="bd618-123">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bd618-124">備註</span><span class="sxs-lookup"><span data-stu-id="bd618-124">Remarks</span></span>

<span data-ttu-id="bd618-125">從 .NET Framework 4 開始，結構會執行 <xref:System.TimeSpan?displayProperty=nameWithType> 介面， <xref:System.IFormattable> 並支援標準和自訂格式字串的格式化作業。</span><span class="sxs-lookup"><span data-stu-id="bd618-125">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="bd618-126">如果剖析方法遇到不支援的格式規範或格式字串，它會擲回 <xref:System.FormatException> 。</span><span class="sxs-lookup"><span data-stu-id="bd618-126">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>

<span data-ttu-id="bd618-127">在舊版的 .NET Framework 中， <xref:System.TimeSpan> 結構不會執行， <xref:System.IFormattable> 且不支援格式字串。</span><span class="sxs-lookup"><span data-stu-id="bd618-127">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="bd618-128">不過，許多開發人員 <xref:System.TimeSpan> 不小心認為的確支援一組格式字串，而且在[複合格式作業](../../../../standard/base-types/composite-formatting.md)中，使用像是的方法 <xref:System.String.Format%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="bd618-128">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bd618-129">一般來說，如果型別會實作為 <xref:System.IFormattable> 並支援格式字串，則使用不支援的格式字串呼叫格式化方法通常會擲回 <xref:System.FormatException> 。</span><span class="sxs-lookup"><span data-stu-id="bd618-129">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="bd618-130">不過，因為並未 <xref:System.TimeSpan> 執行，所以執行時間會 <xref:System.IFormattable> 忽略格式字串，而改為呼叫 <xref:System.TimeSpan.ToString?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bd618-130">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bd618-131">這表示，雖然格式字串不會影響格式化作業，但它們的存在並不會產生 <xref:System.FormatException> 。</span><span class="sxs-lookup"><span data-stu-id="bd618-131">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>

<span data-ttu-id="bd618-132">若是舊版程式碼傳遞複合格式化方法和不正確格式字串，而且該程式碼無法重新編譯的情況，您可以使用專案 `<TimeSpan_LegacyFormatMode>` 來還原舊版 <xref:System.TimeSpan> 行為。</span><span class="sxs-lookup"><span data-stu-id="bd618-132">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="bd618-133">當您將 `enabled` 這個元素的屬性設定為時 `true` ，複合格式化方法會導致的呼叫， <xref:System.TimeSpan.ToString?displayProperty=nameWithType> 而不是 <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType> ，而且 <xref:System.FormatException> 不會擲回。</span><span class="sxs-lookup"><span data-stu-id="bd618-133">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>

## <a name="example"></a><span data-ttu-id="bd618-134">範例</span><span class="sxs-lookup"><span data-stu-id="bd618-134">Example</span></span>

<span data-ttu-id="bd618-135">下列範例 <xref:System.TimeSpan> 會具現化物件，並 <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> 使用不支援的標準格式字串，嘗試使用方法將它格式化。</span><span class="sxs-lookup"><span data-stu-id="bd618-135">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>

[!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
[!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]

<span data-ttu-id="bd618-136">當您在 .NET Framework 3.5 或較舊版本上執行此範例時，會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="bd618-136">When you run the example on the .NET Framework 3.5 or on an earlier version, it displays the following output:</span></span>

```console
12:30:45
```

<span data-ttu-id="bd618-137">如果您在 .NET Framework 4 或更新版本上執行範例，則與輸出的差異明顯不同：</span><span class="sxs-lookup"><span data-stu-id="bd618-137">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>

```console
Invalid Format
```

<span data-ttu-id="bd618-138">不過，如果您將下列設定檔新增至範例的目錄，然後在 .NET Framework 4 或更新版本上執行範例，則輸出會與範例在 .NET Framework 3.5 上執行時所產生的相同。</span><span class="sxs-lookup"><span data-stu-id="bd618-138">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on .NET Framework 3.5.</span></span>

```xml
<?xml version ="1.0"?>
<configuration>
   <runtime>
      <TimeSpan_LegacyFormatMode enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="bd618-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd618-139">See also</span></span>

- [<span data-ttu-id="bd618-140">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="bd618-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bd618-141">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="bd618-141">Configuration File Schema</span></span>](../index.md)
