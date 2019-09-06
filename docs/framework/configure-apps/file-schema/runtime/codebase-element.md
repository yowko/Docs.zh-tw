---
title: <codeBase> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#codeBase
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly/codeBase
helpviewer_keywords:
- <codeBase> element
- container tags, <codeBase> element
- codeBase element
ms.assetid: d48a3983-2297-43ff-a14d-1f29d3995822
ms.openlocfilehash: bd170b817c5ccc337711f8f79968653c29f3eda4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252749"
---
# <a name="codebase-element"></a><span data-ttu-id="2c989-102">\<程式碼基底 > 元素</span><span class="sxs-lookup"><span data-stu-id="2c989-102">\<codeBase> Element</span></span>

<span data-ttu-id="2c989-103">指定通用語言執行時間可以找到元件的位置。</span><span class="sxs-lookup"><span data-stu-id="2c989-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="2c989-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c989-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2c989-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c989-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2c989-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<assemblyBinding >** ](assemblybinding-element-for-runtime.md)</span><span class="sxs-lookup"><span data-stu-id="2c989-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="2c989-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dependentAssembly >** ](dependentassembly-element.md)</span><span class="sxs-lookup"><span data-stu-id="2c989-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dependentAssembly>**](dependentassembly-element.md)</span></span>\
<span data-ttu-id="2c989-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<codeBase>**</span><span class="sxs-lookup"><span data-stu-id="2c989-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<codeBase>**</span></span>

## <a name="syntax"></a><span data-ttu-id="2c989-109">語法</span><span class="sxs-lookup"><span data-stu-id="2c989-109">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2c989-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2c989-110">Attributes and Elements</span></span>

<span data-ttu-id="2c989-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2c989-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2c989-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2c989-112">Attributes</span></span>

|<span data-ttu-id="2c989-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2c989-113">Attribute</span></span>|<span data-ttu-id="2c989-114">說明</span><span class="sxs-lookup"><span data-stu-id="2c989-114">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="2c989-115">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2c989-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="2c989-116">指定執行時間可以找到元件之指定版本的 URL。</span><span class="sxs-lookup"><span data-stu-id="2c989-116">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="2c989-117">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2c989-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="2c989-118">指定程式碼基底適用的元件版本。</span><span class="sxs-lookup"><span data-stu-id="2c989-118">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="2c989-119">元件版本號碼的格式為 [*主要. 次要. 組建. 修訂*]。</span><span class="sxs-lookup"><span data-stu-id="2c989-119">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="2c989-120">version 屬性</span><span class="sxs-lookup"><span data-stu-id="2c989-120">version Attribute</span></span>

|<span data-ttu-id="2c989-121">值</span><span class="sxs-lookup"><span data-stu-id="2c989-121">Value</span></span>|<span data-ttu-id="2c989-122">描述</span><span class="sxs-lookup"><span data-stu-id="2c989-122">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="2c989-123">版本號碼的每個部分的有效值為0到65535。</span><span class="sxs-lookup"><span data-stu-id="2c989-123">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="2c989-124">不適用。</span><span class="sxs-lookup"><span data-stu-id="2c989-124">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2c989-125">子元素</span><span class="sxs-lookup"><span data-stu-id="2c989-125">Child Elements</span></span>

<span data-ttu-id="2c989-126">無。</span><span class="sxs-lookup"><span data-stu-id="2c989-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2c989-127">父項目</span><span class="sxs-lookup"><span data-stu-id="2c989-127">Parent Elements</span></span>

|<span data-ttu-id="2c989-128">項目</span><span class="sxs-lookup"><span data-stu-id="2c989-128">Element</span></span>|<span data-ttu-id="2c989-129">描述</span><span class="sxs-lookup"><span data-stu-id="2c989-129">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="2c989-130">定義用來編譯自訂資源檔的組建提供者集合。</span><span class="sxs-lookup"><span data-stu-id="2c989-130">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="2c989-131">組建提供者的數量不限。</span><span class="sxs-lookup"><span data-stu-id="2c989-131">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="2c989-132">設定 ASP.NET 使用的所有編譯設定。</span><span class="sxs-lookup"><span data-stu-id="2c989-132">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="2c989-133">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2c989-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="2c989-134">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="2c989-134">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2c989-135">備註</span><span class="sxs-lookup"><span data-stu-id="2c989-135">Remarks</span></span>

<span data-ttu-id="2c989-136">若要使用執行階段 **\<程式碼基底>**  設定在電腦組態檔或發行者原則檔中，檔案也必須重新導向組件版本。</span><span class="sxs-lookup"><span data-stu-id="2c989-136">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="2c989-137">應用程式佈建檔可以有 codebase 設定，而不需要重新導向元件版本。</span><span class="sxs-lookup"><span data-stu-id="2c989-137">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="2c989-138">決定要使用哪個元件版本之後，執行時間會從判斷版本的檔案套用程式碼基底設定。</span><span class="sxs-lookup"><span data-stu-id="2c989-138">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="2c989-139">如果未指出程式碼基底，則執行時間會以一般方式探查元件。</span><span class="sxs-lookup"><span data-stu-id="2c989-139">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="2c989-140">如果元件具有強式名稱，則程式碼基底設定可以是近端內部網路或網際網路上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="2c989-140">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="2c989-141">如果元件是私用元件，則程式碼基底設定必須是相對於應用程式目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="2c989-141">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="2c989-142">針對沒有強式名稱的元件，會忽略 version，而載入器會在 dependentAssembly > \<內\<使用程式碼基底的第一個外觀 >。</span><span class="sxs-lookup"><span data-stu-id="2c989-142">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="2c989-143">如果應用程式佈建檔中有一個專案會將系結重新導向至另一個元件，則即使元件版本不符合系結要求，重新導向也會優先。</span><span class="sxs-lookup"><span data-stu-id="2c989-143">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="2c989-144">範例</span><span class="sxs-lookup"><span data-stu-id="2c989-144">Example</span></span>

<span data-ttu-id="2c989-145">下列範例顯示如何指定執行時間可以找到元件的位置。</span><span class="sxs-lookup"><span data-stu-id="2c989-145">The following example shows how to specify where the runtime can find an assembly.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly"
                              publicKeyToken="32ab4ba45e0a69a1"
                              culture="neutral" />
            <codeBase version="2.0.0.0"
                      href="http://www.litwareinc.com/myAssembly.dll"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2c989-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c989-146">See also</span></span>

- [<span data-ttu-id="2c989-147">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2c989-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2c989-148">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2c989-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2c989-149">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="2c989-149">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="2c989-150">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="2c989-150">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
