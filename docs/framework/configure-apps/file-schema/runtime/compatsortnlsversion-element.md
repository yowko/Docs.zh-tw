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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3a348ac8da855e458b6208c51f9c51b48da3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927441"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="aff8a-102">\<CompatSortNLSVersion > 元素</span><span class="sxs-lookup"><span data-stu-id="aff8a-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="aff8a-103">指定執行階段在執行字串比較時，應使用舊版排序次序。</span><span class="sxs-lookup"><span data-stu-id="aff8a-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="aff8a-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="aff8a-104">\<configuration></span></span>  
<span data-ttu-id="aff8a-105">\<執行時間 ></span><span class="sxs-lookup"><span data-stu-id="aff8a-105">\<runtime></span></span>  
<span data-ttu-id="aff8a-106">\<CompatSortNLSVersion > 元素</span><span class="sxs-lookup"><span data-stu-id="aff8a-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aff8a-107">語法</span><span class="sxs-lookup"><span data-stu-id="aff8a-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aff8a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aff8a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="aff8a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aff8a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aff8a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="aff8a-110">Attributes</span></span>  
  
|<span data-ttu-id="aff8a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="aff8a-111">Attribute</span></span>|<span data-ttu-id="aff8a-112">描述</span><span class="sxs-lookup"><span data-stu-id="aff8a-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="aff8a-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="aff8a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="aff8a-114">指定要使用其排序次序的地區設定 ID。</span><span class="sxs-lookup"><span data-stu-id="aff8a-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="aff8a-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="aff8a-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="aff8a-116">值</span><span class="sxs-lookup"><span data-stu-id="aff8a-116">Value</span></span>|<span data-ttu-id="aff8a-117">描述</span><span class="sxs-lookup"><span data-stu-id="aff8a-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aff8a-118">4096</span><span class="sxs-lookup"><span data-stu-id="aff8a-118">4096</span></span>|<span data-ttu-id="aff8a-119">表示替代排序次序的地區設定 ID。</span><span class="sxs-lookup"><span data-stu-id="aff8a-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="aff8a-120">在此情況下, 4096 代表 .NET Framework 3.5 及舊版的排序次序。</span><span class="sxs-lookup"><span data-stu-id="aff8a-120">In this case, 4096 represents the sort order of the .NET Framework 3.5 and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aff8a-121">子元素</span><span class="sxs-lookup"><span data-stu-id="aff8a-121">Child Elements</span></span>  
 <span data-ttu-id="aff8a-122">無。</span><span class="sxs-lookup"><span data-stu-id="aff8a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aff8a-123">父項目</span><span class="sxs-lookup"><span data-stu-id="aff8a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="aff8a-124">項目</span><span class="sxs-lookup"><span data-stu-id="aff8a-124">Element</span></span>|<span data-ttu-id="aff8a-125">說明</span><span class="sxs-lookup"><span data-stu-id="aff8a-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="aff8a-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="aff8a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="aff8a-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="aff8a-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aff8a-128">備註</span><span class="sxs-lookup"><span data-stu-id="aff8a-128">Remarks</span></span>  
 <span data-ttu-id="aff8a-129">由於 .NET Framework 4 中的類別所<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>執行的字串比較、排序和大小寫作業符合 Unicode 5.1 標準, 因此字串比較方法<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> (例如和<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> ) 的結果可能會與舊版的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="aff8a-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the .NET Framework 4 conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="aff8a-130">如果您的應用程式相依于舊版行為, 您可以在應用程式的設定檔中包含`<CompatSortNLSVersion>`專案, 以還原 .NET Framework 3.5 和更早版本中使用的字串比較和排序規則。</span><span class="sxs-lookup"><span data-stu-id="aff8a-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the .NET Framework 3.5 and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aff8a-131">還原舊版字串比較和排序規則也必須要有可在本機系統上提供的 sort00001000.dll 動態連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="aff8a-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="aff8a-132">您也可以在建立應用程式定義域時，將字串 "NetFx40_Legacy20SortingBehavior" 傳遞給 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，這樣做就可以在特定應用程式定義域中使用舊版字串排序和比較規則。</span><span class="sxs-lookup"><span data-stu-id="aff8a-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aff8a-133">範例</span><span class="sxs-lookup"><span data-stu-id="aff8a-133">Example</span></span>  
 <span data-ttu-id="aff8a-134">下列範例會將兩個 <xref:System.String> 物件具現化，並呼叫 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以使用目前文化特性的慣例比較這兩個物件。</span><span class="sxs-lookup"><span data-stu-id="aff8a-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="aff8a-135">當您執行 .NET Framework 4 上的範例時, 它會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="aff8a-135">When you run the example on the .NET Framework 4, it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="aff8a-136">這與您在 .NET Framework 3.5 上執行範例時所顯示的輸出完全不同。</span><span class="sxs-lookup"><span data-stu-id="aff8a-136">This is completely different from the output that is displayed when you run the example on the .NET Framework 3.5.</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="aff8a-137">不過, 如果您將下列設定檔新增至範例的目錄, 然後在 .NET Framework 4 上執行範例, 則輸出會與範例在 .NET Framework 3.5 上執行時所產生的相同。</span><span class="sxs-lookup"><span data-stu-id="aff8a-137">However, if you add the following configuration file to the example's directory and then run the example on the .NET Framework 4, the output is identical to that produced by the example when it is run on the .NET Framework 3.5.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aff8a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aff8a-138">See also</span></span>

- [<span data-ttu-id="aff8a-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="aff8a-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="aff8a-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="aff8a-140">Configuration File Schema</span></span>](../index.md)
