---
title: <supportPortability> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2295ebd919a91ae9942ec225f2bfe784e5ee151
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267790"
---
# <a name="supportportability-element"></a><span data-ttu-id="792e3-102">\<Supportportability> > 項目</span><span class="sxs-lookup"><span data-stu-id="792e3-102">\<supportPortability> Element</span></span>
<span data-ttu-id="792e3-103">指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。</span><span class="sxs-lookup"><span data-stu-id="792e3-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="792e3-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="792e3-104">\<configuration> Element</span></span>  
<span data-ttu-id="792e3-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="792e3-105">\<runtime> Element</span></span>  
<span data-ttu-id="792e3-106">\<Assemblybinding> > 項目</span><span class="sxs-lookup"><span data-stu-id="792e3-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="792e3-107">\<Supportportability> > 項目</span><span class="sxs-lookup"><span data-stu-id="792e3-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="792e3-108">語法</span><span class="sxs-lookup"><span data-stu-id="792e3-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="792e3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="792e3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="792e3-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="792e3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="792e3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="792e3-111">Attributes</span></span>  
  
|<span data-ttu-id="792e3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="792e3-112">Attribute</span></span>|<span data-ttu-id="792e3-113">描述</span><span class="sxs-lookup"><span data-stu-id="792e3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="792e3-114">PKT</span><span class="sxs-lookup"><span data-stu-id="792e3-114">PKT</span></span>|<span data-ttu-id="792e3-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="792e3-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="792e3-116">以字串形式指定的受影響的組件的公開金鑰 token。</span><span class="sxs-lookup"><span data-stu-id="792e3-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="792e3-117">enabled</span><span class="sxs-lookup"><span data-stu-id="792e3-117">enabled</span></span>|<span data-ttu-id="792e3-118">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="792e3-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="792e3-119">指定是否應該啟用之間實作指定的.NET Framework 組件的可攜性的支援。</span><span class="sxs-lookup"><span data-stu-id="792e3-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="792e3-120">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="792e3-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="792e3-121">值</span><span class="sxs-lookup"><span data-stu-id="792e3-121">Value</span></span>|<span data-ttu-id="792e3-122">描述</span><span class="sxs-lookup"><span data-stu-id="792e3-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="792e3-123">true</span><span class="sxs-lookup"><span data-stu-id="792e3-123">true</span></span>|<span data-ttu-id="792e3-124">啟用指定的.NET Framework 組件的實作之間的可攜性的支援。</span><span class="sxs-lookup"><span data-stu-id="792e3-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="792e3-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="792e3-125">This is the default.</span></span>|  
|<span data-ttu-id="792e3-126">False</span><span class="sxs-lookup"><span data-stu-id="792e3-126">false</span></span>|<span data-ttu-id="792e3-127">停用指定的.NET Framework 組件的實作之間的可攜性的支援。</span><span class="sxs-lookup"><span data-stu-id="792e3-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="792e3-128">這可讓應用程式有多個指定的組件實作的參考。</span><span class="sxs-lookup"><span data-stu-id="792e3-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="792e3-129">子元素</span><span class="sxs-lookup"><span data-stu-id="792e3-129">Child Elements</span></span>  
 <span data-ttu-id="792e3-130">無。</span><span class="sxs-lookup"><span data-stu-id="792e3-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="792e3-131">父項目</span><span class="sxs-lookup"><span data-stu-id="792e3-131">Parent Elements</span></span>  
  
|<span data-ttu-id="792e3-132">項目</span><span class="sxs-lookup"><span data-stu-id="792e3-132">Element</span></span>|<span data-ttu-id="792e3-133">描述</span><span class="sxs-lookup"><span data-stu-id="792e3-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="792e3-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="792e3-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="792e3-135">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="792e3-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="792e3-136">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="792e3-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="792e3-137">備註</span><span class="sxs-lookup"><span data-stu-id="792e3-137">Remarks</span></span>  
 <span data-ttu-id="792e3-138">開頭為[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，支援自動提供的應用程式可以使用其中一個的.NET Framework 中，兩個實作，例如.NET Framework 實作或.NET Framework for Silverlight 實作。</span><span class="sxs-lookup"><span data-stu-id="792e3-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="792e3-139">組件繫結器會將兩個實作特定的.NET Framework 組件視為對等項目。</span><span class="sxs-lookup"><span data-stu-id="792e3-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="792e3-140">在少數情況下，此應用程式可攜性功能會造成問題。</span><span class="sxs-lookup"><span data-stu-id="792e3-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="792e3-141">在這些情況下，`<supportPortability>`項目可以用來停用此功能。</span><span class="sxs-lookup"><span data-stu-id="792e3-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="792e3-142">這類案例之一是具有參考.NET Framework 實作和.NET Framework for Silverlight 實作的特定參考組件的組件。</span><span class="sxs-lookup"><span data-stu-id="792e3-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="792e3-143">比方說，撰寫在 Windows Presentation Foundation (WPF) XAML 設計工具可能需要參考這兩個的 WPF 桌面實作，設計工具的使用者介面，並包含在 Silverlight 實作的 WPF 子集。</span><span class="sxs-lookup"><span data-stu-id="792e3-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="792e3-144">根據預設，不同的參考會導致編譯器錯誤，因為組件繫結關係會將兩個組件視為對等項目。</span><span class="sxs-lookup"><span data-stu-id="792e3-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="792e3-145">這個元素會停用預設行為，並可讓編譯成功。</span><span class="sxs-lookup"><span data-stu-id="792e3-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="792e3-146">為了讓編譯器將資訊傳遞給 common language runtime 的組件繫結邏輯，您必須使用`/appconfig`編譯器選項以指定包含此元素的 app.config 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="792e3-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="792e3-147">範例</span><span class="sxs-lookup"><span data-stu-id="792e3-147">Example</span></span>  
 <span data-ttu-id="792e3-148">下列範例會啟用應用程式的.NET Framework 實作和.NET Framework for Silverlight 實作任何存在於這兩種實作的.NET Framework 組件的參考。</span><span class="sxs-lookup"><span data-stu-id="792e3-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="792e3-149">`/appconfig`編譯器選項必須用來指定此 app.config 檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="792e3-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="792e3-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="792e3-150">See also</span></span>
- [<span data-ttu-id="792e3-151">/appconfig （C# 編譯器選項）</span><span class="sxs-lookup"><span data-stu-id="792e3-151">/appconfig (C# Compiler Options)</span></span>](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [<span data-ttu-id="792e3-152">.NET framework 組件統一概觀</span><span class="sxs-lookup"><span data-stu-id="792e3-152">.NET Framework Assembly Unification Overview</span></span>](https://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
