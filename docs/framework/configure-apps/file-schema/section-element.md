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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 94f7709f4bd273515d9fcdd727354ec579c46207
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927220"
---
# <a name="section-element"></a><span data-ttu-id="a119f-102">\<區段 > 元素</span><span class="sxs-lookup"><span data-stu-id="a119f-102">\<section> element</span></span>

<span data-ttu-id="a119f-103">包含設定區段宣告。</span><span class="sxs-lookup"><span data-stu-id="a119f-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="a119f-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a119f-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="a119f-105">&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a119f-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="a119f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<section>**</span><span class="sxs-lookup"><span data-stu-id="a119f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="a119f-107">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="a119f-107">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="a119f-108">&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="a119f-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="a119f-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup>** ](sectiongroup-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="a119f-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md) </span></span>  
<span data-ttu-id="a119f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<section>**</span><span class="sxs-lookup"><span data-stu-id="a119f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="a119f-111">語法</span><span class="sxs-lookup"><span data-stu-id="a119f-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="a119f-112">必要屬性</span><span class="sxs-lookup"><span data-stu-id="a119f-112">Required attributes</span></span>

|           | <span data-ttu-id="a119f-113">說明</span><span class="sxs-lookup"><span data-stu-id="a119f-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a119f-114">**name**</span><span class="sxs-lookup"><span data-stu-id="a119f-114">**name**</span></span>  | <span data-ttu-id="a119f-115">指定設定區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="a119f-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="a119f-116">**type**</span><span class="sxs-lookup"><span data-stu-id="a119f-116">**type**</span></span>  | <span data-ttu-id="a119f-117">指定在設定檔案中讀取區段的設定區段處理常式類別名稱。</span><span class="sxs-lookup"><span data-stu-id="a119f-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="a119f-118">類型值的語法為「完整區段-處理常式類別名稱, 簡單元件名稱」。</span><span class="sxs-lookup"><span data-stu-id="a119f-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="a119f-119">簡單元件名稱是不含 *.dll*副檔名的根檔案名。</span><span class="sxs-lookup"><span data-stu-id="a119f-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="a119f-120">選擇性屬性</span><span class="sxs-lookup"><span data-stu-id="a119f-120">Optional attributes</span></span>

<span data-ttu-id="a119f-121">下列屬性僅適用于 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a119f-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="a119f-122">設定系統會忽略其他應用程式類型的這些屬性。</span><span class="sxs-lookup"><span data-stu-id="a119f-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="a119f-123">描述</span><span class="sxs-lookup"><span data-stu-id="a119f-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="a119f-124">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="a119f-124">**allowDefinition**</span></span> | <span data-ttu-id="a119f-125">指定區段可以用於哪一個設定檔。</span><span class="sxs-lookup"><span data-stu-id="a119f-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="a119f-126">使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="a119f-126">Use one of the following values:</span></span><br><br><span data-ttu-id="a119f-127">**位置**</span><span class="sxs-lookup"><span data-stu-id="a119f-127">**Everywhere**</span></span><br><span data-ttu-id="a119f-128">允許在任何設定檔案中使用區段。</span><span class="sxs-lookup"><span data-stu-id="a119f-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="a119f-129">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a119f-129">This is the default.</span></span><br><span data-ttu-id="a119f-130">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="a119f-130">**MachineOnly**</span></span><br><span data-ttu-id="a119f-131">允許區段僅用於電腦設定檔 (*machine.config*)。</span><span class="sxs-lookup"><span data-stu-id="a119f-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="a119f-132">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="a119f-132">**MachineToApplication**</span></span><br><span data-ttu-id="a119f-133">允許在電腦設定檔或應用程式佈建檔中使用區段。</span><span class="sxs-lookup"><span data-stu-id="a119f-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="a119f-134">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="a119f-134">**allowLocation**</span></span>   | <span data-ttu-id="a119f-135">判斷是否可以使用區段內 **\<位置>** 項目。</span><span class="sxs-lookup"><span data-stu-id="a119f-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="a119f-136">使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="a119f-136">Use one of the following values:</span></span><br><br><span data-ttu-id="a119f-137">**true**</span><span class="sxs-lookup"><span data-stu-id="a119f-137">**true**</span></span><br><span data-ttu-id="a119f-138">允許使用於區段 **\<位置>** 項目。</span><span class="sxs-lookup"><span data-stu-id="a119f-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="a119f-139">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a119f-139">This is the default.</span></span><br><span data-ttu-id="a119f-140">**false**</span><span class="sxs-lookup"><span data-stu-id="a119f-140">**false**</span></span><br><span data-ttu-id="a119f-141">不允許使用於區段 **\<位置>** 項目。</span><span class="sxs-lookup"><span data-stu-id="a119f-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="a119f-142">父元素</span><span class="sxs-lookup"><span data-stu-id="a119f-142">Parent elements</span></span>

|     | <span data-ttu-id="a119f-143">說明</span><span class="sxs-lookup"><span data-stu-id="a119f-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="a119f-144"> **configSections>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="a119f-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="a119f-145">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="a119f-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="a119f-146"> **sectionGroup>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="a119f-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="a119f-147">定義設定區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a119f-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="a119f-148">區段 > 元素是 **\<configSections >** 或 **\<sectionGroup >** 的子項目, 但不能同時是兩者。 **\<**</span><span class="sxs-lookup"><span data-stu-id="a119f-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="a119f-149">子元素</span><span class="sxs-lookup"><span data-stu-id="a119f-149">Child elements</span></span>

<span data-ttu-id="a119f-150">無</span><span class="sxs-lookup"><span data-stu-id="a119f-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a119f-151">備註</span><span class="sxs-lookup"><span data-stu-id="a119f-151">Remarks</span></span>

<span data-ttu-id="a119f-152">宣告設定區段基本上會定義設定檔的新元素。</span><span class="sxs-lookup"><span data-stu-id="a119f-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="a119f-153">新專案包含設定區段處理常式 (也就是執行<xref:System.Configuration.IConfigurationSectionHandler>介面的類別) 會讀取的設定。</span><span class="sxs-lookup"><span data-stu-id="a119f-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="a119f-154">您所定義之區段的屬性和子專案, 取決於您用來讀取設定的區段處理常式。</span><span class="sxs-lookup"><span data-stu-id="a119f-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="a119f-155">在*machine.config*檔案中宣告設定區段處理常式, 可讓您在該電腦上的任何應用程式佈建檔中使用 configuration 區段, 除非**allowDefinition**屬性另行指定。</span><span class="sxs-lookup"><span data-stu-id="a119f-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="a119f-156">範例</span><span class="sxs-lookup"><span data-stu-id="a119f-156">Example</span></span>

<span data-ttu-id="a119f-157">下列範例顯示如何定義設定區段, 並定義該區段的設定:</span><span class="sxs-lookup"><span data-stu-id="a119f-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="a119f-158">組態檔</span><span class="sxs-lookup"><span data-stu-id="a119f-158">Configuration file</span></span>

<span data-ttu-id="a119f-159">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="a119f-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a119f-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a119f-160">See also</span></span>

- [<span data-ttu-id="a119f-161">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="a119f-161">Configuration file schema for the .NET Framework</span></span>](index.md)
