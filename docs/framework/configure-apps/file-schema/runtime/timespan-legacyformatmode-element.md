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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31e2a075f9202439cd62c81a06528b20c4971656
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489343"
---
# <a name="timespanlegacyformatmode-element"></a><span data-ttu-id="5a478-102">\<TimeSpan_LegacyFormatMode > 項目</span><span class="sxs-lookup"><span data-stu-id="5a478-102">\<TimeSpan_LegacyFormatMode> Element</span></span>
<span data-ttu-id="5a478-103">決定是否執行階段會保留舊版行為，在格式化作業與<xref:System.TimeSpan?displayProperty=nameWithType>值。</span><span class="sxs-lookup"><span data-stu-id="5a478-103">Determines whether the runtime preserves legacy behavior in formatting operations with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>  
  
 <span data-ttu-id="5a478-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5a478-104">\<configuration></span></span>  
<span data-ttu-id="5a478-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="5a478-105">\<runtime></span></span>  
<span data-ttu-id="5a478-106"><TimeSpan_LegacyFormatMode></span><span class="sxs-lookup"><span data-stu-id="5a478-106"><TimeSpan_LegacyFormatMode></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a478-107">語法</span><span class="sxs-lookup"><span data-stu-id="5a478-107">Syntax</span></span>  
  
```xml  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a478-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a478-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a478-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a478-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a478-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5a478-110">Attributes</span></span>  
  
|<span data-ttu-id="5a478-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5a478-111">Attribute</span></span>|<span data-ttu-id="5a478-112">描述</span><span class="sxs-lookup"><span data-stu-id="5a478-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5a478-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5a478-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="5a478-114">指定執行階段是否使用舊版的格式化行為<xref:System.TimeSpan?displayProperty=nameWithType>值。</span><span class="sxs-lookup"><span data-stu-id="5a478-114">Specifies whether the runtime uses legacy formatting behavior with <xref:System.TimeSpan?displayProperty=nameWithType> values.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5a478-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="5a478-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="5a478-116">值</span><span class="sxs-lookup"><span data-stu-id="5a478-116">Value</span></span>|<span data-ttu-id="5a478-117">描述</span><span class="sxs-lookup"><span data-stu-id="5a478-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5a478-118">執行階段不會還原舊版的格式化行為。</span><span class="sxs-lookup"><span data-stu-id="5a478-118">The runtime does not restore legacy formatting behavior.</span></span>|  
|`true`|<span data-ttu-id="5a478-119">執行階段會還原舊版的格式化行為。</span><span class="sxs-lookup"><span data-stu-id="5a478-119">The runtime restores legacy formatting behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a478-120">子元素</span><span class="sxs-lookup"><span data-stu-id="5a478-120">Child Elements</span></span>  
 <span data-ttu-id="5a478-121">無。</span><span class="sxs-lookup"><span data-stu-id="5a478-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a478-122">父項目</span><span class="sxs-lookup"><span data-stu-id="5a478-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5a478-123">項目</span><span class="sxs-lookup"><span data-stu-id="5a478-123">Element</span></span>|<span data-ttu-id="5a478-124">描述</span><span class="sxs-lookup"><span data-stu-id="5a478-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5a478-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5a478-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5a478-126">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="5a478-126">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a478-127">備註</span><span class="sxs-lookup"><span data-stu-id="5a478-127">Remarks</span></span>  
 <span data-ttu-id="5a478-128">從.NET Framework 4<xref:System.TimeSpan?displayProperty=nameWithType>結構實作<xref:System.IFormattable>介面，並支援格式化以標準和自訂格式字串的作業。</span><span class="sxs-lookup"><span data-stu-id="5a478-128">Starting with the .NET Framework 4, the <xref:System.TimeSpan?displayProperty=nameWithType> structure implements the <xref:System.IFormattable> interface and supports formatting operations with standard and custom format strings.</span></span> <span data-ttu-id="5a478-129">如果剖析方法遇到不支援的格式規範 」 或 「 格式字串，則會擲回<xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="5a478-129">If a parsing method encounters an unsupported format specifier or format string, it throws a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="5a478-130">在舊版的.NET Framework 中，<xref:System.TimeSpan>結構未實作<xref:System.IFormattable>和不支援格式字串。</span><span class="sxs-lookup"><span data-stu-id="5a478-130">In previous versions of the .NET Framework, the <xref:System.TimeSpan> structure did not implement <xref:System.IFormattable> and did not support format strings.</span></span> <span data-ttu-id="5a478-131">不過，許多開發人員不小心假設<xref:System.TimeSpan>未支援的格式字串集，並使用它們在[格式化作業中的複合](../../../../../docs/standard/base-types/composite-formatting.md)之類的方法與<xref:System.String.Format%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="5a478-131">However, many developers mistakenly assumed that <xref:System.TimeSpan> did support a set of format strings and used them in [composite formatting operations](../../../../../docs/standard/base-types/composite-formatting.md) with methods such as <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5a478-132">一般情況下，如果型別會實作<xref:System.IFormattable>並支援格式字串，呼叫格式化方法使用不支援的格式字串通常會擲回<xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="5a478-132">Ordinarily, if a type implements <xref:System.IFormattable> and supports format strings, calls to formatting methods with unsupported format strings usually throw a <xref:System.FormatException>.</span></span> <span data-ttu-id="5a478-133">不過，因為<xref:System.TimeSpan>未實作<xref:System.IFormattable>，執行階段略過的格式字串，並改為呼叫<xref:System.TimeSpan.ToString?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="5a478-133">However, because <xref:System.TimeSpan> did not implement <xref:System.IFormattable>, the runtime ignored the format string and instead called the <xref:System.TimeSpan.ToString?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5a478-134">這表示，雖然格式字串已不會影響格式化作業，其目前狀態不會造成<xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="5a478-134">This means that, although the format strings had no effect on the formatting operation, their presence did not result in a <xref:System.FormatException>.</span></span>  
  
 <span data-ttu-id="5a478-135">在其中舊版程式碼會將傳遞的複合格式化方法，並以不正確的格式字串，並無法重新編譯該程式碼的情況下，您可以使用`<TimeSpan_LegacyFormatMode>`若要還原舊版的項目<xref:System.TimeSpan>行為。</span><span class="sxs-lookup"><span data-stu-id="5a478-135">For cases in which legacy code passes a composite formatting method and an invalid format string, and that code cannot be recompiled, you can use the `<TimeSpan_LegacyFormatMode>` element to restore the legacy <xref:System.TimeSpan> behavior.</span></span> <span data-ttu-id="5a478-136">當您設定`enabled`屬性，此項目的`true`，複合格式化方法的呼叫中的結果<xref:System.TimeSpan.ToString?displayProperty=nameWithType>而非<xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>，和<xref:System.FormatException>不會擲回。</span><span class="sxs-lookup"><span data-stu-id="5a478-136">When you set the `enabled` attribute of this element to `true`, the composite formatting method results in a call to <xref:System.TimeSpan.ToString?displayProperty=nameWithType> rather than <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=nameWithType>, and a <xref:System.FormatException> is not thrown.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a478-137">範例</span><span class="sxs-lookup"><span data-stu-id="5a478-137">Example</span></span>  
 <span data-ttu-id="5a478-138">下列範例會具現化<xref:System.TimeSpan>物件，並嘗試使用其格式化<xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType>使用不支援的標準格式字串的方法。</span><span class="sxs-lookup"><span data-stu-id="5a478-138">The following example instantiates a <xref:System.TimeSpan> object and attempts to format it with the <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=nameWithType> method by using an unsupported standard format string.</span></span>  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 <span data-ttu-id="5a478-139">當您在上執行範例時[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]或較早的版本，它會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5a478-139">When you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] or on an earlier version, it displays the following output:</span></span>  
  
```  
12:30:45  
```  
  
 <span data-ttu-id="5a478-140">這相當不同的輸出如果您在.NET Framework 4 或更新版本上執行的範例：</span><span class="sxs-lookup"><span data-stu-id="5a478-140">This differs markedly from the output if you run the example on the .NET Framework 4 or later version:</span></span>  
  
```  
Invalid Format  
```  
  
 <span data-ttu-id="5a478-141">不過，如果您將下列組態檔新增至範例的目錄，然後在 .NET Framework 4 或更新版本上執行範例的輸出完全相同上執行時，此範例所產生[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5a478-141">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4 or later version, the output is identical to that produced by the example when it is run on [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a478-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a478-142">See also</span></span>

- [<span data-ttu-id="5a478-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5a478-143">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="5a478-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5a478-144">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
