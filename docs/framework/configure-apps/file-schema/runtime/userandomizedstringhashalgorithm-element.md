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
ms.openlocfilehash: cc9708b8cca6520932fbf0e1975a05cad5fad485
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115047"
---
# <a name="userandomizedstringhashalgorithm-element"></a><span data-ttu-id="af9af-102">\<UseRandomizedStringHashAlgorithm > 元素</span><span class="sxs-lookup"><span data-stu-id="af9af-102">\<UseRandomizedStringHashAlgorithm> Element</span></span>
<span data-ttu-id="af9af-103">判斷 common language runtime 是否會針對每個應用程式網域，計算字串的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="af9af-103">Determines whether the common language runtime calculates hash codes for strings on a per application domain basis.</span></span>  
  
<span data-ttu-id="af9af-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="af9af-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="af9af-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="af9af-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="af9af-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm >**</span><span class="sxs-lookup"><span data-stu-id="af9af-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9af-107">語法</span><span class="sxs-lookup"><span data-stu-id="af9af-107">Syntax</span></span>  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af9af-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="af9af-108">Attributes and Elements</span></span>  
 <span data-ttu-id="af9af-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="af9af-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af9af-110">屬性</span><span class="sxs-lookup"><span data-stu-id="af9af-110">Attributes</span></span>  
  
|<span data-ttu-id="af9af-111">屬性</span><span class="sxs-lookup"><span data-stu-id="af9af-111">Attribute</span></span>|<span data-ttu-id="af9af-112">描述</span><span class="sxs-lookup"><span data-stu-id="af9af-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="af9af-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="af9af-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="af9af-114">指定是否要根據每個應用程式域來計算字串的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="af9af-114">Specifies whether hash codes for strings are calculated on a per application domain basis.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="af9af-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="af9af-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="af9af-116">值</span><span class="sxs-lookup"><span data-stu-id="af9af-116">Value</span></span>|<span data-ttu-id="af9af-117">描述</span><span class="sxs-lookup"><span data-stu-id="af9af-117">Description</span></span>|  
|-----------|-----------------|  
|`0`|<span data-ttu-id="af9af-118">通用語言執行平臺不會針對每個應用程式網域來計算字串的雜湊碼。單一演算法用來計算字串雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="af9af-118">The common language runtime does not compute hash codes for strings on a per application domain basis; a single algorithm is used to calculate string hash codes.</span></span> <span data-ttu-id="af9af-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="af9af-119">This is the default.</span></span>|  
|`1`|<span data-ttu-id="af9af-120">通用語言執行時間會針對每個應用程式網域，計算字串的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="af9af-120">The common language runtime computes hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="af9af-121">不同應用程式域和不同進程中的相同字串會有不同的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="af9af-121">Identical strings in different application domains and in different processes will have different hash codes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af9af-122">子項目</span><span class="sxs-lookup"><span data-stu-id="af9af-122">Child Elements</span></span>  
 <span data-ttu-id="af9af-123">無。</span><span class="sxs-lookup"><span data-stu-id="af9af-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af9af-124">父項目</span><span class="sxs-lookup"><span data-stu-id="af9af-124">Parent Elements</span></span>  
  
|<span data-ttu-id="af9af-125">項目</span><span class="sxs-lookup"><span data-stu-id="af9af-125">Element</span></span>|<span data-ttu-id="af9af-126">描述</span><span class="sxs-lookup"><span data-stu-id="af9af-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="af9af-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="af9af-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="af9af-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="af9af-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af9af-129">備註</span><span class="sxs-lookup"><span data-stu-id="af9af-129">Remarks</span></span>  
 <span data-ttu-id="af9af-130">根據預設，<xref:System.StringComparer> 類別和 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 方法會使用單一雜湊演算法，在應用程式域之間產生一致的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="af9af-130">By default, the <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method use a single hashing algorithm that produces a consistent hash code across application domains.</span></span> <span data-ttu-id="af9af-131">這相當於將 `<UseRandomizedStringHashAlgorithm>` 元素的 `enabled` 屬性設定為 [`0`]。</span><span class="sxs-lookup"><span data-stu-id="af9af-131">This is equivalent to setting the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `0`.</span></span> <span data-ttu-id="af9af-132">這是 .NET Framework 4 中使用的雜湊演算法。</span><span class="sxs-lookup"><span data-stu-id="af9af-132">This is the hashing algorithm used in the .NET Framework 4.</span></span>  
  
 <span data-ttu-id="af9af-133"><xref:System.StringComparer> 類別和 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 方法也可以使用不同的雜湊演算法，根據每個應用程式域來計算雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="af9af-133">The <xref:System.StringComparer> class and the <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> method can also use a different hashing algorithm that computes hash codes on a per application domain basis.</span></span> <span data-ttu-id="af9af-134">因此，對等字串的雜湊碼會在應用程式域之間有所不同。</span><span class="sxs-lookup"><span data-stu-id="af9af-134">As a result, hash codes for equivalent strings will differ across application domains.</span></span> <span data-ttu-id="af9af-135">這是可加入宣告的功能;若要利用它，您必須將 `<UseRandomizedStringHashAlgorithm>` 元素的 `enabled` 屬性設定為 [`1`]。</span><span class="sxs-lookup"><span data-stu-id="af9af-135">This is an opt-in feature; to take advantage of it, you must set the `enabled` attribute of the `<UseRandomizedStringHashAlgorithm>` element to `1`.</span></span>  
  
 <span data-ttu-id="af9af-136">雜湊表中的字串查詢通常是 O （1）運算。</span><span class="sxs-lookup"><span data-stu-id="af9af-136">The string lookup in a hash table is typically an O(1) operation.</span></span> <span data-ttu-id="af9af-137">不過，當發生大量衝突時，查閱可能會變成 O （n<sup>2</sup>）運算。</span><span class="sxs-lookup"><span data-stu-id="af9af-137">However, when a large number of collisions occur, the lookup can become an O(n<sup>2</sup>) operation.</span></span> <span data-ttu-id="af9af-138">您可以使用 `<UseRandomizedStringHashAlgorithm>` 設定專案，為每個應用程式域產生隨機的雜湊演算法，進而限制可能發生衝突的數目，特別是當計算雜湊碼的索引鍵是以輸入的資料為基礎時使用者.</span><span class="sxs-lookup"><span data-stu-id="af9af-138">You can use the `<UseRandomizedStringHashAlgorithm>` configuration element to generate a random hashing algorithm per application domain, which in turn limits the number of potential collisions, particularly when the keys from which the hash codes are calculated are based on data input by users.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af9af-139">範例</span><span class="sxs-lookup"><span data-stu-id="af9af-139">Example</span></span>  
 <span data-ttu-id="af9af-140">下列範例會定義包含私用字串常數的 `DisplayString` 類別，`s`，其值為 "This is a string"。</span><span class="sxs-lookup"><span data-stu-id="af9af-140">The following example defines a `DisplayString` class that includes a private string constant, `s`, whose value is "This is a string."</span></span> <span data-ttu-id="af9af-141">它也包含一個 `ShowStringHashCode` 方法，它會顯示字串值和其雜湊碼，以及方法執行所在之應用程式域的名稱。</span><span class="sxs-lookup"><span data-stu-id="af9af-141">It also includes a `ShowStringHashCode` method that displays the string value and its hash code along with the name of the application domain in which the method is executing.</span></span>  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 <span data-ttu-id="af9af-142">當您執行範例但未提供設定檔時，它會顯示類似下列的輸出。</span><span class="sxs-lookup"><span data-stu-id="af9af-142">When you run the example without supplying a configuration file, it displays output similar to the following.</span></span> <span data-ttu-id="af9af-143">請注意，字串的雜湊碼在兩個應用程式域中都相同。</span><span class="sxs-lookup"><span data-stu-id="af9af-143">Note that the hash codes for the string are identical in the two application domains.</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 <span data-ttu-id="af9af-144">不過，如果您將下列設定檔新增至範例的目錄，然後執行範例，則相同字串的雜湊碼將會因應用程式域而有所不同。</span><span class="sxs-lookup"><span data-stu-id="af9af-144">However, if you add the following configuration file to the example's directory and then run the example, the hash codes for the same string will differ by application domain.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="af9af-145">當設定檔存在時，此範例會顯示下列輸出：</span><span class="sxs-lookup"><span data-stu-id="af9af-145">When the configuration file is present, the example displays the following output:</span></span>  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a><span data-ttu-id="af9af-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="af9af-146">See also</span></span>

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
