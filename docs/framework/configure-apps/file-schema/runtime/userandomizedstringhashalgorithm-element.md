---
title: <UseRandomizedStringHashAlgorithm> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153773"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="55817-102">\<使用隨機字串雜湊演算法>元素</span><span class="sxs-lookup"><span data-stu-id="55817-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="55817-103">確定通用語言運行時是否根據每個應用程式域計算字串的雜湊代碼。</span><span class="sxs-lookup"><span data-stu-id="55817-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="55817-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="55817-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="55817-105">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="55817-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="55817-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<使用隨機字串雜湊演算法>**</span><span class="sxs-lookup"><span data-stu-id="55817-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55817-107">語法</span><span class="sxs-lookup"><span data-stu-id="55817-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55817-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="55817-108">Attributes and Elements</span></span>  
 <span data-ttu-id="55817-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="55817-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55817-110">屬性</span><span class="sxs-lookup"><span data-stu-id="55817-110">Attributes</span></span>  
  
|<span data-ttu-id="55817-111">屬性</span><span class="sxs-lookup"><span data-stu-id="55817-111">Attribute</span></span>|<span data-ttu-id="55817-112">描述</span><span class="sxs-lookup"><span data-stu-id="55817-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="55817-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="55817-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="55817-114">指定字串的雜湊代碼是否根據應用程式域計算。</span><span class="sxs-lookup"><span data-stu-id="55817-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="55817-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="55817-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="55817-116">值</span><span class="sxs-lookup"><span data-stu-id="55817-116">Value</span></span>|<span data-ttu-id="55817-117">描述</span><span class="sxs-lookup"><span data-stu-id="55817-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="55817-118">通用語言運行時不根據每個應用程式域計算字串的雜湊代碼;因此，不計算字串的雜湊代碼。單個演算法用於計算字串雜湊代碼。</span><span class="sxs-lookup"><span data-stu-id="55817-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="55817-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="55817-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="55817-120">通用語言運行時根據每個應用程式域計算字串的雜湊代碼。</span><span class="sxs-lookup"><span data-stu-id="55817-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="55817-121">不同應用程式域和不同進程中的相同字串將具有不同的雜湊代碼。</span><span class="sxs-lookup"><span data-stu-id="55817-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="55817-122">子元素</span><span class="sxs-lookup"><span data-stu-id="55817-122">Child Elements</span></span>  
 <span data-ttu-id="55817-123">無。</span><span class="sxs-lookup"><span data-stu-id="55817-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="55817-124">父項目</span><span class="sxs-lookup"><span data-stu-id="55817-124">Parent Elements</span></span>  
  
|<span data-ttu-id="55817-125">元素</span><span class="sxs-lookup"><span data-stu-id="55817-125">Element</span></span>|<span data-ttu-id="55817-126">描述</span><span class="sxs-lookup"><span data-stu-id="55817-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="55817-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="55817-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="55817-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="55817-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55817-129">備註</span><span class="sxs-lookup"><span data-stu-id="55817-129">Remarks</span></span>  
 <span data-ttu-id="55817-130">預設情況下，<xref:System.StringComparer>類<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>和方法使用單個雜湊演算法，該演算法跨應用程式域生成一致的雜湊代碼。</span><span class="sxs-lookup"><span data-stu-id="55817-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="55817-131">這相當於將`enabled``<UseRandomizedStringHashAlgorithm>`元素的屬性設置為`0`。</span><span class="sxs-lookup"><span data-stu-id="55817-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="55817-132">這是 .NET 框架 4 中使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="55817-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="55817-133">類<xref:System.StringComparer>和方法<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>還可以使用不同的雜湊演算法，該演算法根據每個應用程式域計算雜湊代碼。</span><span class="sxs-lookup"><span data-stu-id="55817-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="55817-134">因此，等效字串的雜湊代碼將因應用程式域而異。</span><span class="sxs-lookup"><span data-stu-id="55817-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="55817-135">這是一個加入宣告功能;要利用它，必須將`enabled``<UseRandomizedStringHashAlgorithm>`元素的屬性設置為`1`。</span><span class="sxs-lookup"><span data-stu-id="55817-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="55817-136">雜湊表中的字串查找通常是 O（1） 操作。</span><span class="sxs-lookup"><span data-stu-id="55817-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="55817-137">但是，當發生大量衝突時，查找可能會成為 O（n<sup>2</sup>） 操作。</span><span class="sxs-lookup"><span data-stu-id="55817-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="55817-138">您可以使用`<UseRandomizedStringHashAlgorithm>`配置元素生成每個應用程式域的隨機雜湊演算法，從而限制潛在衝突的數量，尤其是當計算雜湊代碼的鍵基於使用者輸入的資料時。</span><span class="sxs-lookup"><span data-stu-id="55817-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55817-139">範例</span><span class="sxs-lookup"><span data-stu-id="55817-139">Example</span></span>  
 <span data-ttu-id="55817-140">下面的示例定義一個`DisplayString`類，該類包含私有字串常量`s`，其值為"這是一個字串"。</span><span class="sxs-lookup"><span data-stu-id="55817-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="55817-141">它也包含 `ShowStringHashCode` 方法，這個方法會將字串值及其雜湊碼與方法執行所在之應用程式定義域的名稱一起顯示。</span><span class="sxs-lookup"><span data-stu-id="55817-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="55817-142">當您在沒有提供組態檔的情況下執行此範例，它會顯示類似下列的輸出。</span><span class="sxs-lookup"><span data-stu-id="55817-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="55817-143">請注意，字串的雜湊碼在兩個應用程式定義域中相同。</span><span class="sxs-lookup"><span data-stu-id="55817-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="55817-144">不過，如果您將下列組態檔加入至範例的目錄，然後執行這個範例，相同字串的雜湊碼將會因為應用程式定義域不同而有所不同。</span><span class="sxs-lookup"><span data-stu-id="55817-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="55817-145">當組態檔存在時，這個範例會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="55817-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="55817-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55817-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
