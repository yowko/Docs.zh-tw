---
title: <Library> 元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: f642276b-33fb-4a81-b882-8808c31ba69e
ms.openlocfilehash: f94bfe047fa7a95b6f24264bae0b27112c589dfd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128360"
---
# <a name="library-element-net-native"></a><span data-ttu-id="6cf0e-102">\<程式庫 > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="6cf0e-102">\<Library> Element (.NET Native)</span></span>
<span data-ttu-id="6cf0e-103">定義包含類型和類型成員的組件，這些類型和類型成員的中繼資料可在執行階段用於反映。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-103">Defines the assembly that contains types and type members whose metadata is available for reflection at run time.</span></span>  
  
 <span data-ttu-id="6cf0e-104">\<Directives> 項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-104">\<Directives> Element</span></span>  
<span data-ttu-id="6cf0e-105">\<Library> 項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-105">\<Library> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf0e-106">語法</span><span class="sxs-lookup"><span data-stu-id="6cf0e-106">Syntax</span></span>  
  
```xml  
<Library Name="assembly_name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6cf0e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="6cf0e-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6cf0e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="6cf0e-109">Attributes</span></span>  
  
|<span data-ttu-id="6cf0e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6cf0e-110">Attribute</span></span>|<span data-ttu-id="6cf0e-111">描述</span><span class="sxs-lookup"><span data-stu-id="6cf0e-111">Description</span></span>|  
|---------------|-----------------|  
|`Name`|<span data-ttu-id="6cf0e-112">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-112">Required attribute.</span></span> <span data-ttu-id="6cf0e-113">指定組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-113">Specifies the name of an assembly.</span></span> <span data-ttu-id="6cf0e-114">這個 `<Library>` 項目的子項目可針對這個組件中找到的類型和類型成員，定義其執行階段反映原則。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-114">Child elements of this `<Library>` element define the runtime reflection policy for types and type members found in this assembly.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="6cf0e-115">Name 屬性</span><span class="sxs-lookup"><span data-stu-id="6cf0e-115">Name attribute</span></span>  
  
|<span data-ttu-id="6cf0e-116">值</span><span class="sxs-lookup"><span data-stu-id="6cf0e-116">Value</span></span>|<span data-ttu-id="6cf0e-117">描述</span><span class="sxs-lookup"><span data-stu-id="6cf0e-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6cf0e-118">*assembly_name*</span><span class="sxs-lookup"><span data-stu-id="6cf0e-118">*assembly_name*</span></span>|<span data-ttu-id="6cf0e-119">組件的簡單名稱，不包含其副檔名。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-119">The simple name of the assembly, without its file extension.</span></span> <span data-ttu-id="6cf0e-120">這個屬性 (Attribute) 會對應至 <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-120">This attribute corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="6cf0e-121">例如，名為 Extensions.dll 之組件的名稱是 "Extensions"。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-121">For example, the name of an assembly named Extensions.dll is "Extensions".</span></span> <span data-ttu-id="6cf0e-122">如需支援從組件條件式包含中繼資料之 *assembly_name* 的特殊格式，請參閱＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-122">See the Remarks section for a special form of *assembly_name* that supports conditional inclusion of metadata from the assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6cf0e-123">子項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-123">Child Elements</span></span>  
  
|<span data-ttu-id="6cf0e-124">項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-124">Element</span></span>|<span data-ttu-id="6cf0e-125">描述</span><span class="sxs-lookup"><span data-stu-id="6cf0e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cf0e-126">\<Assembly></span><span class="sxs-lookup"><span data-stu-id="6cf0e-126">\<Assembly></span></span>](assembly-element-net-native.md)|<span data-ttu-id="6cf0e-127">將原則套用至特定組件中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-127">Applies policy to all the types in a particular assembly.</span></span>|  
|[<span data-ttu-id="6cf0e-128">\<Namespace></span><span class="sxs-lookup"><span data-stu-id="6cf0e-128">\<Namespace></span></span>](namespace-element-net-native.md)|<span data-ttu-id="6cf0e-129">將原則套用至特定命名空間中的所有類型。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-129">Applies policy to all the types in a particular namespace.</span></span>|  
|[<span data-ttu-id="6cf0e-130">\<Type></span><span class="sxs-lookup"><span data-stu-id="6cf0e-130">\<Type></span></span>](type-element-net-native.md)|<span data-ttu-id="6cf0e-131">將原則套用至特定類型，例如類別或結構。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-131">Applies policy to a particular type, such as a class or structure.</span></span>|  
|[<span data-ttu-id="6cf0e-132">\<TypeInstantiation></span><span class="sxs-lookup"><span data-stu-id="6cf0e-132">\<TypeInstantiation></span></span>](typeinstantiation-element-net-native.md)|<span data-ttu-id="6cf0e-133">將原則套用至建構的泛型類型。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-133">Applies policy to a constructed generic type.</span></span> <span data-ttu-id="6cf0e-134">例如，[\<TypeInstantiation>](typeinstantiation-element-net-native.md) 項目可用來定義 `List<String>` 類型的原則。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-134">For example, a [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element could be used to define policy for a `List<String>` type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6cf0e-135">父項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-135">Parent Elements</span></span>  
  
|<span data-ttu-id="6cf0e-136">項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-136">Element</span></span>|<span data-ttu-id="6cf0e-137">描述</span><span class="sxs-lookup"><span data-stu-id="6cf0e-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6cf0e-138">\<Directives></span><span class="sxs-lookup"><span data-stu-id="6cf0e-138">\<Directives></span></span>](directives-element-net-native.md)|<span data-ttu-id="6cf0e-139">執行階段指示詞檔案的根項目。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-139">The root element of a runtime directives file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cf0e-140">備註</span><span class="sxs-lookup"><span data-stu-id="6cf0e-140">Remarks</span></span>  
 <span data-ttu-id="6cf0e-141">[\<Directives>](directives-element-net-native.md) 項目可包含零、一或多個 `<Library>` 元素。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-141">The [\<Directives>](directives-element-net-native.md) element can contain zero, one, or more `<Library>` elements.</span></span>  
  
 <span data-ttu-id="6cf0e-142">`<Library>` 項目可當做容器來使用，以定義在執行階段需要中繼資料的程式項目；這個項目不會表示原則。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-142">The `<Library>` element serves as a container to define the program elements whose metadata is needed at run time; this element doesn't express policy.</span></span> <span data-ttu-id="6cf0e-143">在編譯時期，編譯器工具只會在 `<Library>` 項目所指定的程式庫中，搜尋其子項目所識別的程式項目。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-143">At compile time, compiler tools search only the library designated by the `<Library>` element for program elements identified by its child elements.</span></span> <span data-ttu-id="6cf0e-144">在其他情況下，編譯器工具會在所有程式庫 (包含 .NET Framework 核心程式庫) 中，搜尋 [\<Application>](application-element-net-native.md) 項目的子項目所識別的程式項目。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-144">In contrast, compiler tools search all libraries, including.NET Framework core libraries, for program elements identified by child elements of the [\<Application>](application-element-net-native.md) element.</span></span>  
  
 <span data-ttu-id="6cf0e-145">您可以有條件地利用 `<Library>` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-145">`<Library>` directives may be conditionally utilized.</span></span> <span data-ttu-id="6cf0e-146">如果 `<Library>` 專案的名稱的開頭和結尾都是星號（\*），只有在應用程式參考星號之間指定的元件時，`<Library>` 指示詞才會生效。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-146">If the name of the `<Library>` element starts and ends with an asterisk (\*), the `<Library>` directive has an effect only if the assembly specified between the asterisks is referenced by the app.</span></span> <span data-ttu-id="6cf0e-147">例如，下列執行時間指示詞僅適用于應用程式參考的公用程式 .dll 元件。</span><span class="sxs-lookup"><span data-stu-id="6cf0e-147">For example, the following runtime directive applies only if the Utilities.dll assembly is referenced by the app.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Library Name="*Utilities*">  
   ...  
  </Library>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6cf0e-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf0e-148">See also</span></span>

- [<span data-ttu-id="6cf0e-149">\<應用程式 > 元素</span><span class="sxs-lookup"><span data-stu-id="6cf0e-149">\<Application> Element</span></span>](application-element-net-native.md)
- [<span data-ttu-id="6cf0e-150">\<指示詞 > 元素</span><span class="sxs-lookup"><span data-stu-id="6cf0e-150">\<Directives> Element</span></span>](directives-element-net-native.md)
- [<span data-ttu-id="6cf0e-151">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="6cf0e-151">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="6cf0e-152">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="6cf0e-152">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
