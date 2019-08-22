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
ms.openlocfilehash: a06daa0b2aa5374c9959cbbe778d62856819a40e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663858"
---
# <a name="codebase-element"></a><span data-ttu-id="40467-102">\<程式碼基底 > 元素</span><span class="sxs-lookup"><span data-stu-id="40467-102">\<codeBase> Element</span></span>

<span data-ttu-id="40467-103">指定通用語言執行時間可以找到元件的位置。</span><span class="sxs-lookup"><span data-stu-id="40467-103">Specifies where the common language runtime can find an assembly.</span></span>

<span data-ttu-id="40467-104">\<configuration > \<執行時間\<> assemblyBinding \<> dependentAssembly \<> 程式碼基底 ></span><span class="sxs-lookup"><span data-stu-id="40467-104">\<configuration> \<runtime> \<assemblyBinding> \<dependentAssembly> \<codeBase></span></span>

## <a name="syntax"></a><span data-ttu-id="40467-105">語法</span><span class="sxs-lookup"><span data-stu-id="40467-105">Syntax</span></span>

```xml
   <codeBase
        version="Assembly version"
        href="URL of assembly"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40467-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="40467-106">Attributes and Elements</span></span>

<span data-ttu-id="40467-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="40467-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="40467-108">屬性</span><span class="sxs-lookup"><span data-stu-id="40467-108">Attributes</span></span>

|<span data-ttu-id="40467-109">屬性</span><span class="sxs-lookup"><span data-stu-id="40467-109">Attribute</span></span>|<span data-ttu-id="40467-110">描述</span><span class="sxs-lookup"><span data-stu-id="40467-110">Description</span></span>|
|---------------|-----------------|
|`href`|<span data-ttu-id="40467-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="40467-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="40467-112">指定執行時間可以找到元件之指定版本的 URL。</span><span class="sxs-lookup"><span data-stu-id="40467-112">Specifies the URL where the runtime can find the specified version of the assembly.</span></span>|
|`version`|<span data-ttu-id="40467-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="40467-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="40467-114">指定程式碼基底適用的元件版本。</span><span class="sxs-lookup"><span data-stu-id="40467-114">Specifies the version of the assembly the codebase applies to.</span></span> <span data-ttu-id="40467-115">元件版本號碼的格式為 [*主要. 次要. 組建. 修訂*]。</span><span class="sxs-lookup"><span data-stu-id="40467-115">The format of an assembly version number is *major.minor.build.revision*.</span></span>|

## <a name="version-attribute"></a><span data-ttu-id="40467-116">version 屬性</span><span class="sxs-lookup"><span data-stu-id="40467-116">version Attribute</span></span>

|<span data-ttu-id="40467-117">值</span><span class="sxs-lookup"><span data-stu-id="40467-117">Value</span></span>|<span data-ttu-id="40467-118">描述</span><span class="sxs-lookup"><span data-stu-id="40467-118">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="40467-119">版本號碼的每個部分的有效值為0到65535。</span><span class="sxs-lookup"><span data-stu-id="40467-119">Valid values for each part of the version number are 0 to 65535.</span></span>|<span data-ttu-id="40467-120">不適用。</span><span class="sxs-lookup"><span data-stu-id="40467-120">Not applicable.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="40467-121">子元素</span><span class="sxs-lookup"><span data-stu-id="40467-121">Child Elements</span></span>

<span data-ttu-id="40467-122">無。</span><span class="sxs-lookup"><span data-stu-id="40467-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40467-123">父項目</span><span class="sxs-lookup"><span data-stu-id="40467-123">Parent Elements</span></span>

|<span data-ttu-id="40467-124">項目</span><span class="sxs-lookup"><span data-stu-id="40467-124">Element</span></span>|<span data-ttu-id="40467-125">描述</span><span class="sxs-lookup"><span data-stu-id="40467-125">Description</span></span>|
|-------------|-----------------|
|`buildproviders`|<span data-ttu-id="40467-126">定義用來編譯自訂資源檔的組建提供者集合。</span><span class="sxs-lookup"><span data-stu-id="40467-126">Defines a collection of build providers used to compile custom resource files.</span></span> <span data-ttu-id="40467-127">組建提供者的數量不限。</span><span class="sxs-lookup"><span data-stu-id="40467-127">You can have any number of build providers.</span></span>|
|`compilation`|<span data-ttu-id="40467-128">設定 ASP.NET 使用的所有編譯設定。</span><span class="sxs-lookup"><span data-stu-id="40467-128">Configures all the compilation settings that ASP.NET uses.</span></span>|
|`configuration`|<span data-ttu-id="40467-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="40467-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`System.web`|<span data-ttu-id="40467-130">指定 ASP.NET 組態區段的根項目。</span><span class="sxs-lookup"><span data-stu-id="40467-130">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="40467-131">備註</span><span class="sxs-lookup"><span data-stu-id="40467-131">Remarks</span></span>

<span data-ttu-id="40467-132">若要使用執行階段 **\<程式碼基底>**  設定在電腦組態檔或發行者原則檔中，檔案也必須重新導向組件版本。</span><span class="sxs-lookup"><span data-stu-id="40467-132">For the runtime to use the **\<codeBase>** setting in a machine configuration file or publisher policy file, the file must also redirect the assembly version.</span></span> <span data-ttu-id="40467-133">應用程式佈建檔可以有 codebase 設定, 而不需要重新導向元件版本。</span><span class="sxs-lookup"><span data-stu-id="40467-133">Application configuration files can have a codebase setting without redirecting the assembly version.</span></span> <span data-ttu-id="40467-134">決定要使用哪個元件版本之後, 執行時間會從判斷版本的檔案套用程式碼基底設定。</span><span class="sxs-lookup"><span data-stu-id="40467-134">After determining which assembly version to use, the runtime applies the codebase setting from the file that determines the version.</span></span> <span data-ttu-id="40467-135">如果未指出程式碼基底, 則執行時間會以一般方式探查元件。</span><span class="sxs-lookup"><span data-stu-id="40467-135">If no codebase is indicated, the runtime probes for the assembly in the usual way.</span></span>

<span data-ttu-id="40467-136">如果元件具有強式名稱, 則程式碼基底設定可以是近端內部網路或網際網路上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="40467-136">If the assembly has a strong name, the codebase setting can be anywhere on the local intranet or the Internet.</span></span> <span data-ttu-id="40467-137">如果元件是私用元件, 則程式碼基底設定必須是相對於應用程式目錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="40467-137">If the assembly is a private assembly, the codebase setting must be a path relative to the application's directory.</span></span>

<span data-ttu-id="40467-138">針對沒有強式名稱的元件, 會忽略 version, 而載入器會在 dependentAssembly > \<內\<使用程式碼基底的第一個外觀 >。</span><span class="sxs-lookup"><span data-stu-id="40467-138">For assemblies without a strong name, version is ignored and the loader uses the first appearance of \<codebase> inside \<dependentAssembly>.</span></span> <span data-ttu-id="40467-139">如果應用程式佈建檔中有一個專案會將系結重新導向至另一個元件, 則即使元件版本不符合系結要求, 重新導向也會優先。</span><span class="sxs-lookup"><span data-stu-id="40467-139">If there is an entry in the application configuration file that redirects binding to another assembly, the redirection will take precedence even if the assembly version doesn't match the binding request.</span></span>

## <a name="example"></a><span data-ttu-id="40467-140">範例</span><span class="sxs-lookup"><span data-stu-id="40467-140">Example</span></span>

<span data-ttu-id="40467-141">下列範例顯示如何指定執行時間可以找到元件的位置。</span><span class="sxs-lookup"><span data-stu-id="40467-141">The following example shows how to specify where the runtime can find an assembly.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="40467-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40467-142">See also</span></span>

- [<span data-ttu-id="40467-143">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="40467-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="40467-144">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="40467-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="40467-145">指定組件的位置</span><span class="sxs-lookup"><span data-stu-id="40467-145">Specifying an Assembly's Location</span></span>](../../specify-assembly-location.md)
- [<span data-ttu-id="40467-146">執行階段如何找出組件</span><span class="sxs-lookup"><span data-stu-id="40467-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
