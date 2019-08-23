---
title: <supportPortability> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1848db96b8f466f617c58f0fdd879ffe3b2022bd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927253"
---
# <a name="supportportability-element"></a><span data-ttu-id="67ff1-102">\<Supportportability> > 元素</span><span class="sxs-lookup"><span data-stu-id="67ff1-102">\<supportPortability> Element</span></span>
<span data-ttu-id="67ff1-103">指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。</span><span class="sxs-lookup"><span data-stu-id="67ff1-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="67ff1-104">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="67ff1-104">\<configuration> Element</span></span>  
<span data-ttu-id="67ff1-105">\<執行時間 > 元素</span><span class="sxs-lookup"><span data-stu-id="67ff1-105">\<runtime> Element</span></span>  
<span data-ttu-id="67ff1-106">\<assemblyBinding > 元素</span><span class="sxs-lookup"><span data-stu-id="67ff1-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="67ff1-107">\<Supportportability> > 元素</span><span class="sxs-lookup"><span data-stu-id="67ff1-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ff1-108">語法</span><span class="sxs-lookup"><span data-stu-id="67ff1-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67ff1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67ff1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="67ff1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="67ff1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67ff1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="67ff1-111">Attributes</span></span>  
  
|<span data-ttu-id="67ff1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="67ff1-112">Attribute</span></span>|<span data-ttu-id="67ff1-113">描述</span><span class="sxs-lookup"><span data-stu-id="67ff1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="67ff1-114">PKT</span><span class="sxs-lookup"><span data-stu-id="67ff1-114">PKT</span></span>|<span data-ttu-id="67ff1-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="67ff1-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="67ff1-116">以字串的形式, 指定受影響元件的公開金鑰 token。</span><span class="sxs-lookup"><span data-stu-id="67ff1-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="67ff1-117">enabled</span><span class="sxs-lookup"><span data-stu-id="67ff1-117">enabled</span></span>|<span data-ttu-id="67ff1-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="67ff1-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="67ff1-119">指定是否應該啟用指定之 .NET Framework 元件的執行之間的可攜性支援。</span><span class="sxs-lookup"><span data-stu-id="67ff1-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="67ff1-120">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="67ff1-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="67ff1-121">值</span><span class="sxs-lookup"><span data-stu-id="67ff1-121">Value</span></span>|<span data-ttu-id="67ff1-122">描述</span><span class="sxs-lookup"><span data-stu-id="67ff1-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="67ff1-123">true</span><span class="sxs-lookup"><span data-stu-id="67ff1-123">true</span></span>|<span data-ttu-id="67ff1-124">啟用指定 .NET Framework 元件的執行之間的可攜性支援。</span><span class="sxs-lookup"><span data-stu-id="67ff1-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="67ff1-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="67ff1-125">This is the default.</span></span>|  
|<span data-ttu-id="67ff1-126">false</span><span class="sxs-lookup"><span data-stu-id="67ff1-126">false</span></span>|<span data-ttu-id="67ff1-127">停用指定之 .NET Framework 元件的執行之間的可攜性支援。</span><span class="sxs-lookup"><span data-stu-id="67ff1-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="67ff1-128">這可讓應用程式參考指定元件的多個執行。</span><span class="sxs-lookup"><span data-stu-id="67ff1-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="67ff1-129">子元素</span><span class="sxs-lookup"><span data-stu-id="67ff1-129">Child Elements</span></span>  
 <span data-ttu-id="67ff1-130">無。</span><span class="sxs-lookup"><span data-stu-id="67ff1-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="67ff1-131">父項目</span><span class="sxs-lookup"><span data-stu-id="67ff1-131">Parent Elements</span></span>  
  
|<span data-ttu-id="67ff1-132">項目</span><span class="sxs-lookup"><span data-stu-id="67ff1-132">Element</span></span>|<span data-ttu-id="67ff1-133">描述</span><span class="sxs-lookup"><span data-stu-id="67ff1-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="67ff1-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="67ff1-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="67ff1-135">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="67ff1-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="67ff1-136">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="67ff1-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ff1-137">備註</span><span class="sxs-lookup"><span data-stu-id="67ff1-137">Remarks</span></span>  
 <span data-ttu-id="67ff1-138">從 .NET Framework 4 開始, 會自動為可使用 .NET Framework 的兩個實作為之一的應用程式提供支援, 例如, .NET Framework 的執行或 Silverlight 執行的 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="67ff1-138">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="67ff1-139">元件系結器會將這兩個特定 .NET Framework 元件的執行視為對等。</span><span class="sxs-lookup"><span data-stu-id="67ff1-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="67ff1-140">在少數情況下, 此應用程式可攜性功能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="67ff1-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="67ff1-141">在這些情況下, `<supportPortability>`可以使用專案來停用此功能。</span><span class="sxs-lookup"><span data-stu-id="67ff1-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="67ff1-142">其中一個案例是必須同時參考 .NET Framework 執行的元件, 以及特定參考元件的 Silverlight 執行 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="67ff1-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="67ff1-143">例如, 以 Windows Presentation Foundation (WPF) 撰寫的 XAML 設計工具可能需要參考 WPF 桌上型電腦的程式設計人員的使用者介面, 以及包含在 Silverlight 執行中的 WPF 子集。</span><span class="sxs-lookup"><span data-stu-id="67ff1-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="67ff1-144">根據預設，不同的參考會導致編譯器錯誤，因為組件繫結關係會將兩個組件視為對等項目。</span><span class="sxs-lookup"><span data-stu-id="67ff1-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="67ff1-145">這個元素會停用預設行為, 並允許編譯成功。</span><span class="sxs-lookup"><span data-stu-id="67ff1-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="67ff1-146">為了讓編譯器將資訊傳遞給 common language runtime 的元件系結邏輯, 您必須使用`/appconfig`編譯器選項來指定 app.config 檔案中包含此專案的位置。</span><span class="sxs-lookup"><span data-stu-id="67ff1-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67ff1-147">範例</span><span class="sxs-lookup"><span data-stu-id="67ff1-147">Example</span></span>  
 <span data-ttu-id="67ff1-148">下列範例可讓應用程式同時參考同時存在於兩個執行中之任何 .NET Framework 元件的 .NET Framework 實和 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="67ff1-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="67ff1-149">`/appconfig`編譯器選項必須用來指定此 app.config 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="67ff1-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="67ff1-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67ff1-150">See also</span></span>

- [<span data-ttu-id="67ff1-151">/appconfig (C#編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="67ff1-151">/appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="67ff1-152">[.NET Framework 元件統一總覽](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="67ff1-152">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
