---
title: <CompatSortNLSVersion> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154266"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="c0075-102">\<CompatSortNLSVersion> 項目</span><span class="sxs-lookup"><span data-stu-id="c0075-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="c0075-103">指定執行階段在執行字串比較時，應使用舊版排序次序。</span><span class="sxs-lookup"><span data-stu-id="c0075-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a><span data-ttu-id="c0075-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0075-104">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0075-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0075-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c0075-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c0075-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0075-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c0075-107">Attributes</span></span>  
  
|<span data-ttu-id="c0075-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c0075-108">Attribute</span></span>|<span data-ttu-id="c0075-109">描述</span><span class="sxs-lookup"><span data-stu-id="c0075-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c0075-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c0075-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="c0075-111">指定要使用其排序次序的地區設定 ID。</span><span class="sxs-lookup"><span data-stu-id="c0075-111">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c0075-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="c0075-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="c0075-113">值</span><span class="sxs-lookup"><span data-stu-id="c0075-113">Value</span></span>|<span data-ttu-id="c0075-114">描述</span><span class="sxs-lookup"><span data-stu-id="c0075-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c0075-115">4096</span><span class="sxs-lookup"><span data-stu-id="c0075-115">4096</span></span>|<span data-ttu-id="c0075-116">表示替代排序次序的地區設定 ID。</span><span class="sxs-lookup"><span data-stu-id="c0075-116">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="c0075-117">在此情況下，4096代表 .NET Framework 3.5 及舊版的排序次序。</span><span class="sxs-lookup"><span data-stu-id="c0075-117">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0075-118">子元素</span><span class="sxs-lookup"><span data-stu-id="c0075-118">Child Elements</span></span>  
 <span data-ttu-id="c0075-119">無。</span><span class="sxs-lookup"><span data-stu-id="c0075-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0075-120">父項目</span><span class="sxs-lookup"><span data-stu-id="c0075-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c0075-121">元素</span><span class="sxs-lookup"><span data-stu-id="c0075-121">Element</span></span>|<span data-ttu-id="c0075-122">描述</span><span class="sxs-lookup"><span data-stu-id="c0075-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c0075-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c0075-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c0075-124">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="c0075-124">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0075-125">備註</span><span class="sxs-lookup"><span data-stu-id="c0075-125">Remarks</span></span>  
 <span data-ttu-id="c0075-126">由於 .NET Framework 4 中的類別所執行的字串比較、排序和大小寫作業 <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> 符合 Unicode 5.1 標準，因此字串比較方法（例如和）的結果 <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> 可能會與舊版的 .NET Framework 不同。</span><span class="sxs-lookup"><span data-stu-id="c0075-126">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="c0075-127">如果您的應用程式相依于舊版行為，您可以在 `<CompatSortNLSVersion>` 應用程式的設定檔中包含專案，以還原 .NET Framework 3.5 和更早版本中使用的字串比較和排序規則。</span><span class="sxs-lookup"><span data-stu-id="c0075-127">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c0075-128">還原舊版字串比較和排序規則也必須要有可在本機系統上提供的 sort00001000.dll 動態連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="c0075-128">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="c0075-129">您也可以在建立應用程式定義域時，將字串 "NetFx40_Legacy20SortingBehavior" 傳遞給 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，這樣做就可以在特定應用程式定義域中使用舊版字串排序和比較規則。</span><span class="sxs-lookup"><span data-stu-id="c0075-129">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0075-130">範例</span><span class="sxs-lookup"><span data-stu-id="c0075-130">Example</span></span>  
 <span data-ttu-id="c0075-131">下列範例會將兩個 <xref:System.String> 物件具現化，並呼叫 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以使用目前文化特性的慣例比較這兩個物件。</span><span class="sxs-lookup"><span data-stu-id="c0075-131">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="c0075-132">當您執行 .NET Framework 4 上的範例時，它會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="c0075-132">When you run the example on the .NET Framework 4, it displays the following output:</span></span>
  
```console
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="c0075-133">這與您在 .NET Framework 3.5 上執行範例時所顯示的輸出完全不同：</span><span class="sxs-lookup"><span data-stu-id="c0075-133">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5:</span></span>
  
```console
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="c0075-134">不過，如果您將下列設定檔新增至範例的目錄，然後在 .NET Framework 4 上執行範例，則輸出會與範例在 .NET Framework 3.5 上執行時所產生的相同。</span><span class="sxs-lookup"><span data-stu-id="c0075-134">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0075-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0075-135">See also</span></span>

- [<span data-ttu-id="c0075-136">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="c0075-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c0075-137">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="c0075-137">Configuration File Schema</span></span>](../index.md)
