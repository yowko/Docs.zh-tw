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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a51b9fb485da605effbad0e81b8baf5e05e382a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087790"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="66d35-102">\<UseRandomizedStringHashAlgorithm > 項目</span><span class="sxs-lookup"><span data-stu-id="66d35-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="66d35-103">判斷 common language runtime 是否會計算字串的雜湊碼，在每個應用程式定義域為基準。</span><span class="sxs-lookup"><span data-stu-id="66d35-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
 <span data-ttu-id="66d35-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="66d35-104">\<configuration></span></span>  
<span data-ttu-id="66d35-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="66d35-105">\<runtime></span></span>  
<span data-ttu-id="66d35-106">\<UseRandomizedStringHashAlgorithm></span><span class="sxs-lookup"><span data-stu-id="66d35-106">\<UseRandomizedStringHashAlgorithm></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66d35-107">語法</span><span class="sxs-lookup"><span data-stu-id="66d35-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66d35-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66d35-108">Attributes and Elements</span></span>  
 <span data-ttu-id="66d35-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="66d35-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66d35-110">屬性</span><span class="sxs-lookup"><span data-stu-id="66d35-110">Attributes</span></span>  
  
|<span data-ttu-id="66d35-111">屬性</span><span class="sxs-lookup"><span data-stu-id="66d35-111">Attribute</span></span>|<span data-ttu-id="66d35-112">描述</span><span class="sxs-lookup"><span data-stu-id="66d35-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="66d35-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="66d35-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="66d35-114">指定是否計算字串的雜湊碼，以在每個應用程式定義域為基準。</span><span class="sxs-lookup"><span data-stu-id="66d35-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="66d35-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="66d35-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="66d35-116">值</span><span class="sxs-lookup"><span data-stu-id="66d35-116">Value</span></span>|<span data-ttu-id="66d35-117">描述</span><span class="sxs-lookup"><span data-stu-id="66d35-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="66d35-118">Common language runtime 不會計算字串的雜湊碼在每個應用程式網域進行;單一的演算法用來計算字串的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="66d35-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="66d35-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="66d35-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="66d35-120">Common language runtime 計算字串的雜湊碼在每個應用程式定義域為基準。</span><span class="sxs-lookup"><span data-stu-id="66d35-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="66d35-121">相同的字串，在不同的應用程式定義域和不同的處理序中會有不同的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="66d35-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66d35-122">子元素</span><span class="sxs-lookup"><span data-stu-id="66d35-122">Child Elements</span></span>  
 <span data-ttu-id="66d35-123">無。</span><span class="sxs-lookup"><span data-stu-id="66d35-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="66d35-124">父項目</span><span class="sxs-lookup"><span data-stu-id="66d35-124">Parent Elements</span></span>  
  
|<span data-ttu-id="66d35-125">項目</span><span class="sxs-lookup"><span data-stu-id="66d35-125">Element</span></span>|<span data-ttu-id="66d35-126">描述</span><span class="sxs-lookup"><span data-stu-id="66d35-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="66d35-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="66d35-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="66d35-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="66d35-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="66d35-129">備註</span><span class="sxs-lookup"><span data-stu-id="66d35-129">Remarks</span></span>  
 <span data-ttu-id="66d35-130">根據預設，<xref:System.StringComparer>類別和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法使用單一的雜湊演算法可跨應用程式定義域產生一致雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="66d35-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="66d35-131">這相當於設定`enabled`的屬性`<UseRandomizedStringHashAlgorithm>`項目`0`。</span><span class="sxs-lookup"><span data-stu-id="66d35-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="66d35-132">這是用於雜湊演算法[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="66d35-132">This is the hashing algorithm used in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span>  
  
 <span data-ttu-id="66d35-133"><xref:System.StringComparer>類別和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法也可以使用不同的雜湊演算法來計算雜湊程式碼在每個應用程式定義域為基準。</span><span class="sxs-lookup"><span data-stu-id="66d35-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="66d35-134">如此一來，對等字串的雜湊程式碼會在應用程式定義域而有所不同。</span><span class="sxs-lookup"><span data-stu-id="66d35-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="66d35-135">這是選用的功能;若要充分利用它，您必須設定`enabled`的屬性`<UseRandomizedStringHashAlgorithm>`項目`1`。</span><span class="sxs-lookup"><span data-stu-id="66d35-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="66d35-136">雜湊表中的字串查閱通常是 o （1） 的作業。</span><span class="sxs-lookup"><span data-stu-id="66d35-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="66d35-137">不過，當發生大量碰撞，查閱可能會變成 O (n<sup>2</sup>) 作業。</span><span class="sxs-lookup"><span data-stu-id="66d35-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="66d35-138">您可以使用`<UseRandomizedStringHashAlgorithm>`組態項目來產生隨機的雜湊演算法，每個應用程式定義域，進而限制可能發生的衝突數目，特別是當導出的雜湊碼的索引鍵為基礎的資料輸入由使用者。</span><span class="sxs-lookup"><span data-stu-id="66d35-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="66d35-139">範例</span><span class="sxs-lookup"><span data-stu-id="66d35-139">Example</span></span>  
 <span data-ttu-id="66d35-140">下列範例會定義`DisplayString`類別，其中包含私用的字串常數， `s`，其值為"This is 字串"。</span><span class="sxs-lookup"><span data-stu-id="66d35-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="66d35-141">它也包含`ShowStringHashCode`方法，以顯示的字串值和其雜湊程式碼，以及用來執行此方法的應用程式定義域的名稱。</span><span class="sxs-lookup"><span data-stu-id="66d35-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="66d35-142">當您執行範例，而不需要提供組態檔時，它會顯示類似下列的輸出。</span><span class="sxs-lookup"><span data-stu-id="66d35-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="66d35-143">請注意，字串的雜湊碼相同的兩個應用程式定義域中。</span><span class="sxs-lookup"><span data-stu-id="66d35-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="66d35-144">不過，如果您將下列組態檔新增至範例的目錄，然後執行範例的相同字串的雜湊碼將會因應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="66d35-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="66d35-145">當組態檔存在時，此範例會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="66d35-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="66d35-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66d35-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
