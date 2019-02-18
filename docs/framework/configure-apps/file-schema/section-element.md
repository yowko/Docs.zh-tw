---
title: <section> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 58f823ce0c128f30e361b4a631d41286533b5f0f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259211"
---
# <a name="section-element"></a><span data-ttu-id="18ace-102">\<區段 > 項目</span><span class="sxs-lookup"><span data-stu-id="18ace-102">\<section> element</span></span>

<span data-ttu-id="18ace-103">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="18ace-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="18ace-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="18ace-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="18ace-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="18ace-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="18ace-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span><span class="sxs-lookup"><span data-stu-id="18ace-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="18ace-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="18ace-107">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="18ace-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="18ace-108">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="18ace-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="18ace-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="18ace-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span><span class="sxs-lookup"><span data-stu-id="18ace-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="18ace-111">語法</span><span class="sxs-lookup"><span data-stu-id="18ace-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="18ace-112">必要屬性</span><span class="sxs-lookup"><span data-stu-id="18ace-112">Required attributes</span></span>

|           | <span data-ttu-id="18ace-113">描述</span><span class="sxs-lookup"><span data-stu-id="18ace-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="18ace-114">**name**</span><span class="sxs-lookup"><span data-stu-id="18ace-114">**name**</span></span>  | <span data-ttu-id="18ace-115">指定的組態區段名稱。</span><span class="sxs-lookup"><span data-stu-id="18ace-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="18ace-116">**type**</span><span class="sxs-lookup"><span data-stu-id="18ace-116">**type**</span></span>  | <span data-ttu-id="18ace-117">指定讀取組態檔區段的組態區段處理常式類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="18ace-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="18ace-118">型別值的語法 」 fully-qualified-section-handler-class-name，簡單組件名稱 」。</span><span class="sxs-lookup"><span data-stu-id="18ace-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="18ace-119">簡單的組件名稱是根檔案名稱，而不需要 *.dll*副檔名。</span><span class="sxs-lookup"><span data-stu-id="18ace-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="18ace-120">選擇性的屬性</span><span class="sxs-lookup"><span data-stu-id="18ace-120">Optional attributes</span></span>

<span data-ttu-id="18ace-121">以下為屬性只適用於 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="18ace-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="18ace-122">組態系統會忽略這些屬性的其他應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="18ace-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="18ace-123">描述</span><span class="sxs-lookup"><span data-stu-id="18ace-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="18ace-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="18ace-124">**allowDefinition**</span></span> | <span data-ttu-id="18ace-125">指定區段可以用在哪一個組態檔。</span><span class="sxs-lookup"><span data-stu-id="18ace-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="18ace-126">使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="18ace-126">Use one of the following values:</span></span><br><br><span data-ttu-id="18ace-127">**Everywhere**</span><span class="sxs-lookup"><span data-stu-id="18ace-127">**Everywhere**</span></span><br><span data-ttu-id="18ace-128">允許使用任何組態檔中區段。</span><span class="sxs-lookup"><span data-stu-id="18ace-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="18ace-129">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="18ace-129">This is the default.</span></span><br><span data-ttu-id="18ace-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="18ace-130">**MachineOnly**</span></span><br><span data-ttu-id="18ace-131">允許區段只能用在電腦組態檔 (*Machine.config*)。</span><span class="sxs-lookup"><span data-stu-id="18ace-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="18ace-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="18ace-132">**MachineToApplication**</span></span><br><span data-ttu-id="18ace-133">允許可用於電腦組態檔或應用程式組態檔區段。</span><span class="sxs-lookup"><span data-stu-id="18ace-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="18ace-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="18ace-134">**allowLocation**</span></span>   | <span data-ttu-id="18ace-135">判斷是否可以使用區段內 **\<位置>** 項目。</span><span class="sxs-lookup"><span data-stu-id="18ace-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="18ace-136">使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="18ace-136">Use one of the following values:</span></span><br><br><span data-ttu-id="18ace-137">**true**</span><span class="sxs-lookup"><span data-stu-id="18ace-137">**true**</span></span><br><span data-ttu-id="18ace-138">允許使用於區段 **\<位置>** 項目。</span><span class="sxs-lookup"><span data-stu-id="18ace-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="18ace-139">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="18ace-139">This is the default.</span></span><br><span data-ttu-id="18ace-140">**false**</span><span class="sxs-lookup"><span data-stu-id="18ace-140">**false**</span></span><br><span data-ttu-id="18ace-141">不允許使用於區段 **\<位置>** 項目。</span><span class="sxs-lookup"><span data-stu-id="18ace-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="18ace-142">父元素</span><span class="sxs-lookup"><span data-stu-id="18ace-142">Parent elements</span></span>

|     | <span data-ttu-id="18ace-143">描述</span><span class="sxs-lookup"><span data-stu-id="18ace-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="18ace-144">**\<configSections >** 項目</span><span class="sxs-lookup"><span data-stu-id="18ace-144">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="18ace-145">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="18ace-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="18ace-146">**\<sectionGroup>** Element</span><span class="sxs-lookup"><span data-stu-id="18ace-146">**\<sectionGroup>** Element</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="18ace-147">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="18ace-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="18ace-148">A **\<一節 >** 項目是可能的子項目 **\<configSections >** 或 **\<sectionGroup >** 但不是兩者。</span><span class="sxs-lookup"><span data-stu-id="18ace-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="18ace-149">子元素</span><span class="sxs-lookup"><span data-stu-id="18ace-149">Child elements</span></span>

<span data-ttu-id="18ace-150">無</span><span class="sxs-lookup"><span data-stu-id="18ace-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="18ace-151">備註</span><span class="sxs-lookup"><span data-stu-id="18ace-151">Remarks</span></span>

<span data-ttu-id="18ace-152">本質上宣告組態區段會定義組態檔的新項目。</span><span class="sxs-lookup"><span data-stu-id="18ace-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="18ace-153">新的項目包含的組態區段處理常式的設定 (也就是一個類別，實作<xref:System.Configuration.IConfigurationSectionHandler>介面) 讀取。</span><span class="sxs-lookup"><span data-stu-id="18ace-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="18ace-154">屬性和子項目的區段中定義取決於您用來讀取您的設定區段處理常式。</span><span class="sxs-lookup"><span data-stu-id="18ace-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="18ace-155">宣告中的組態區段處理常式*Machine.config*檔可讓您使用 [設定] 區段中任何應用程式組態檔，該電腦上，除非**allowDefinition**屬性指定不同的情況。</span><span class="sxs-lookup"><span data-stu-id="18ace-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="18ace-156">範例</span><span class="sxs-lookup"><span data-stu-id="18ace-156">Example</span></span>

<span data-ttu-id="18ace-157">下列範例示範如何定義組態區段，並定義該區段的設定：</span><span class="sxs-lookup"><span data-stu-id="18ace-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="18ace-158">組態檔</span><span class="sxs-lookup"><span data-stu-id="18ace-158">Configuration file</span></span>

<span data-ttu-id="18ace-159">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="18ace-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="18ace-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18ace-160">See also</span></span>

- [<span data-ttu-id="18ace-161">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="18ace-161">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
