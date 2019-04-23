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
ms.openlocfilehash: dfd241056947fbf1daf48b84ff41e3f74ff7b8de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59195770"
---
# <a name="compatsortnlsversion-element"></a><span data-ttu-id="6d49f-102">\<CompatSortNLSVersion > 項目</span><span class="sxs-lookup"><span data-stu-id="6d49f-102">\<CompatSortNLSVersion> Element</span></span>
<span data-ttu-id="6d49f-103">指定執行階段在執行字串比較時，應使用舊版排序次序。</span><span class="sxs-lookup"><span data-stu-id="6d49f-103">Specifies that the runtime should use legacy sort orders when performing string comparisons.</span></span>  
  
 <span data-ttu-id="6d49f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="6d49f-104">\<configuration></span></span>  
<span data-ttu-id="6d49f-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="6d49f-105">\<runtime></span></span>  
<span data-ttu-id="6d49f-106">\<CompatSortNLSVersion > 項目</span><span class="sxs-lookup"><span data-stu-id="6d49f-106">\<CompatSortNLSVersion> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d49f-107">語法</span><span class="sxs-lookup"><span data-stu-id="6d49f-107">Syntax</span></span>  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d49f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6d49f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6d49f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6d49f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d49f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6d49f-110">Attributes</span></span>  
  
|<span data-ttu-id="6d49f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6d49f-111">Attribute</span></span>|<span data-ttu-id="6d49f-112">描述</span><span class="sxs-lookup"><span data-stu-id="6d49f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="6d49f-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6d49f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="6d49f-114">指定要使用其排序次序的地區設定 ID。</span><span class="sxs-lookup"><span data-stu-id="6d49f-114">Specifies the locale ID whose sort order is to be used.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6d49f-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="6d49f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="6d49f-116">值</span><span class="sxs-lookup"><span data-stu-id="6d49f-116">Value</span></span>|<span data-ttu-id="6d49f-117">描述</span><span class="sxs-lookup"><span data-stu-id="6d49f-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d49f-118">4096</span><span class="sxs-lookup"><span data-stu-id="6d49f-118">4096</span></span>|<span data-ttu-id="6d49f-119">表示替代排序次序的地區設定 ID。</span><span class="sxs-lookup"><span data-stu-id="6d49f-119">The locale ID that represents an alternate sort order.</span></span> <span data-ttu-id="6d49f-120">在這個案例中，4096 表示 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] (含) 以前版本的排序次序。</span><span class="sxs-lookup"><span data-stu-id="6d49f-120">In this case, 4096 represents the sort order of the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d49f-121">子元素</span><span class="sxs-lookup"><span data-stu-id="6d49f-121">Child Elements</span></span>  
 <span data-ttu-id="6d49f-122">無。</span><span class="sxs-lookup"><span data-stu-id="6d49f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d49f-123">父項目</span><span class="sxs-lookup"><span data-stu-id="6d49f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="6d49f-124">項目</span><span class="sxs-lookup"><span data-stu-id="6d49f-124">Element</span></span>|<span data-ttu-id="6d49f-125">描述</span><span class="sxs-lookup"><span data-stu-id="6d49f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6d49f-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6d49f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6d49f-127">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="6d49f-127">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d49f-128">備註</span><span class="sxs-lookup"><span data-stu-id="6d49f-128">Remarks</span></span>  
 <span data-ttu-id="6d49f-129">因為由執行字串比較、 排序和大小寫作業<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>類別內[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]這類符合 Unicode 5.1 標準，字串比較方法的結果<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType>和<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>可能不同於舊版.NET Framework 中。</span><span class="sxs-lookup"><span data-stu-id="6d49f-129">Because string comparison, sorting, and casing operations performed by the <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> class in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] conform to the Unicode 5.1 standard, the results of string comparison methods such as <xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> and <xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> may differ from previous versions of the .NET Framework.</span></span> <span data-ttu-id="6d49f-130">如果您的應用程式依賴舊版的行為，您可以藉由在應用程式的組態檔中包含 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 項目的方式，還原 `<CompatSortNLSVersion>` (含) 以前版本中使用的字串比較和排序規則。</span><span class="sxs-lookup"><span data-stu-id="6d49f-130">If your application depends on legacy behavior, you can restore the string comparison and sorting rules used in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] and earlier versions by including the `<CompatSortNLSVersion>` element in your application's configuration file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6d49f-131">還原舊版字串比較和排序規則也必須要有可在本機系統上提供的 sort00001000.dll 動態連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="6d49f-131">Restoring legacy string comparison and sorting rules also requires the sort00001000.dll dynamic link library to be available on the local system.</span></span>  
  
 <span data-ttu-id="6d49f-132">您也可以在建立應用程式定義域時，將字串 "NetFx40_Legacy20SortingBehavior" 傳遞給 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，這樣做就可以在特定應用程式定義域中使用舊版字串排序和比較規則。</span><span class="sxs-lookup"><span data-stu-id="6d49f-132">You can also use legacy string sorting and comparison rules in a specific application domain by passing the string "NetFx40_Legacy20SortingBehavior" to the <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> method when you create the application domain.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d49f-133">範例</span><span class="sxs-lookup"><span data-stu-id="6d49f-133">Example</span></span>  
 <span data-ttu-id="6d49f-134">下列範例會將兩個 <xref:System.String> 物件具現化，並呼叫 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以使用目前文化特性的慣例比較這兩個物件。</span><span class="sxs-lookup"><span data-stu-id="6d49f-134">The following example instantiates two <xref:System.String> objects and calls the <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method to compare them by using the conventions of the current culture.</span></span>  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 <span data-ttu-id="6d49f-135">當您在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 上執行範例時，會顯示下列輸出。</span><span class="sxs-lookup"><span data-stu-id="6d49f-135">When you run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], it displays the following output.</span></span>  
  
```  
sta follows a in the sort order.  
```  
  
 <span data-ttu-id="6d49f-136">這與您在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上執行範例時顯示的輸出完全不同。</span><span class="sxs-lookup"><span data-stu-id="6d49f-136">This is completely different from the output that is displayed when you run the example on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```  
sta equals a in the sort order.  
```  
  
 <span data-ttu-id="6d49f-137">不過，如果您將下列組態檔加入範例的目錄中，然後在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 上執行該範例，則輸出會與在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上執行範例時所產生的輸出完全相同。</span><span class="sxs-lookup"><span data-stu-id="6d49f-137">However, if you add the following configuration file to the example's directory and then run the example on the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the output is identical to that produced by the example when it is run on the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6d49f-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6d49f-138">See also</span></span>

- [<span data-ttu-id="6d49f-139">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6d49f-139">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="6d49f-140">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6d49f-140">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
