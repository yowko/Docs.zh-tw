---
title: <section> element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153722"
---
# <a name="section-element"></a><span data-ttu-id="4e860-102">\<節>元素</span><span class="sxs-lookup"><span data-stu-id="4e860-102">\<section> element</span></span>

<span data-ttu-id="4e860-103">包含配置部分聲明。</span><span class="sxs-lookup"><span data-stu-id="4e860-103">Contains a configuration section declaration.</span></span>

<span data-ttu-id="4e860-104">[**\<配置>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e860-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="4e860-105">&nbsp;&nbsp;[**\<配置部分>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="4e860-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="4e860-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<第>節**</span><span class="sxs-lookup"><span data-stu-id="4e860-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

<span data-ttu-id="4e860-107">[**\<配置>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4e860-107">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="4e860-108">&nbsp;&nbsp;[**\<配置部分>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="4e860-108">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="4e860-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<部分組>**](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="4e860-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>\
<span data-ttu-id="4e860-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<第>節**</span><span class="sxs-lookup"><span data-stu-id="4e860-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4e860-111">語法</span><span class="sxs-lookup"><span data-stu-id="4e860-111">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="4e860-112">必要的屬性</span><span class="sxs-lookup"><span data-stu-id="4e860-112">Required attributes</span></span>

|           | <span data-ttu-id="4e860-113">描述</span><span class="sxs-lookup"><span data-stu-id="4e860-113">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4e860-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4e860-114">**name**</span></span>  | <span data-ttu-id="4e860-115">指定配置部分的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e860-115">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="4e860-116">**型別**</span><span class="sxs-lookup"><span data-stu-id="4e860-116">**type**</span></span>  | <span data-ttu-id="4e860-117">指定從設定檔讀取節的配置節處理常式類的名稱。</span><span class="sxs-lookup"><span data-stu-id="4e860-117">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="4e860-118">類型值具有語法"完全限定的截面處理常式-類名稱，簡單程式集名稱"。</span><span class="sxs-lookup"><span data-stu-id="4e860-118">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="4e860-119">簡單的程式集名稱是沒有 *.dll*檔副檔名的根檔案名。</span><span class="sxs-lookup"><span data-stu-id="4e860-119">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="4e860-120">可選屬性</span><span class="sxs-lookup"><span data-stu-id="4e860-120">Optional attributes</span></span>

<span data-ttu-id="4e860-121">以下屬性僅適用于ASP.NET應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e860-121">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="4e860-122">配置系統忽略這些屬性的其他應用程式類型。</span><span class="sxs-lookup"><span data-stu-id="4e860-122">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="4e860-123">描述</span><span class="sxs-lookup"><span data-stu-id="4e860-123">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="4e860-124">**允許定義**</span><span class="sxs-lookup"><span data-stu-id="4e860-124">**allowDefinition**</span></span> | <span data-ttu-id="4e860-125">指定該節可以使用的設定檔。</span><span class="sxs-lookup"><span data-stu-id="4e860-125">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="4e860-126">請使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="4e860-126">Use one of the following values:</span></span><br><br><span data-ttu-id="4e860-127">**所有位置**</span><span class="sxs-lookup"><span data-stu-id="4e860-127">**Everywhere**</span></span><br><span data-ttu-id="4e860-128">允許在任何設定檔中使用該節。</span><span class="sxs-lookup"><span data-stu-id="4e860-128">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="4e860-129">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4e860-129">This is the default.</span></span><br><span data-ttu-id="4e860-130">**僅限機器**</span><span class="sxs-lookup"><span data-stu-id="4e860-130">**MachineOnly**</span></span><br><span data-ttu-id="4e860-131">允許僅在機器設定檔 （*機器.config）* 中使用該部分。</span><span class="sxs-lookup"><span data-stu-id="4e860-131">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="4e860-132">**機器應用**</span><span class="sxs-lookup"><span data-stu-id="4e860-132">**MachineToApplication**</span></span><br><span data-ttu-id="4e860-133">允許在電腦設定檔或應用程式佈建檔中使用節。</span><span class="sxs-lookup"><span data-stu-id="4e860-133">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="4e860-134">**允許定位**</span><span class="sxs-lookup"><span data-stu-id="4e860-134">**allowLocation**</span></span>   | <span data-ttu-id="4e860-135">確定是否可以在**\<位置>** 元素中使用節。</span><span class="sxs-lookup"><span data-stu-id="4e860-135">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="4e860-136">請使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="4e860-136">Use one of the following values:</span></span><br><br><span data-ttu-id="4e860-137">**true**</span><span class="sxs-lookup"><span data-stu-id="4e860-137">**true**</span></span><br><span data-ttu-id="4e860-138">允許在**\<位置>** 元素中使用節。</span><span class="sxs-lookup"><span data-stu-id="4e860-138">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="4e860-139">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="4e860-139">This is the default.</span></span><br><span data-ttu-id="4e860-140">**false**</span><span class="sxs-lookup"><span data-stu-id="4e860-140">**false**</span></span><br><span data-ttu-id="4e860-141">不允許在**\<位置>** 元素中使用節。</span><span class="sxs-lookup"><span data-stu-id="4e860-141">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="4e860-142">父元素</span><span class="sxs-lookup"><span data-stu-id="4e860-142">Parent elements</span></span>

|     | <span data-ttu-id="4e860-143">描述</span><span class="sxs-lookup"><span data-stu-id="4e860-143">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4e860-144">\*\* \<配置部分>\*\* 元素</span><span class="sxs-lookup"><span data-stu-id="4e860-144">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="4e860-145">包含配置部分和命名空間聲明。</span><span class="sxs-lookup"><span data-stu-id="4e860-145">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="4e860-146">第>節組\*\*\< \*\*元素</span><span class="sxs-lookup"><span data-stu-id="4e860-146">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="4e860-147">為配置部分定義命名空間。</span><span class="sxs-lookup"><span data-stu-id="4e860-147">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="4e860-148">\*\* \<>元素的節**是**\<配置">"\*\* 或**\<"組組">** 的子項目，但不能同時提供兩者。</span><span class="sxs-lookup"><span data-stu-id="4e860-148">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="4e860-149">子元素</span><span class="sxs-lookup"><span data-stu-id="4e860-149">Child elements</span></span>

<span data-ttu-id="4e860-150">None</span><span class="sxs-lookup"><span data-stu-id="4e860-150">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4e860-151">備註</span><span class="sxs-lookup"><span data-stu-id="4e860-151">Remarks</span></span>

<span data-ttu-id="4e860-152">聲明配置部分實質上定義設定檔的新元素。</span><span class="sxs-lookup"><span data-stu-id="4e860-152">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="4e860-153">新元素包含配置節處理常式（即實現介面的類）讀取的<xref:System.Configuration.IConfigurationSectionHandler>設置。</span><span class="sxs-lookup"><span data-stu-id="4e860-153">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="4e860-154">定義的節的屬性和子項目取決於用於讀取設置的節處理常式。</span><span class="sxs-lookup"><span data-stu-id="4e860-154">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="4e860-155">在*Machine.config 檔中*聲明配置部分處理常式使您能夠在該電腦上的任何應用程式佈建檔中使用配置節，除非**allowDefinition**屬性另有指定。</span><span class="sxs-lookup"><span data-stu-id="4e860-155">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="4e860-156">範例</span><span class="sxs-lookup"><span data-stu-id="4e860-156">Example</span></span>

<span data-ttu-id="4e860-157">下面的示例演示如何定義配置部分並定義該部分的設置：</span><span class="sxs-lookup"><span data-stu-id="4e860-157">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4e860-158">組態檔</span><span class="sxs-lookup"><span data-stu-id="4e860-158">Configuration file</span></span>

<span data-ttu-id="4e860-159">此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。</span><span class="sxs-lookup"><span data-stu-id="4e860-159">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e860-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e860-160">See also</span></span>

- [<span data-ttu-id="4e860-161">.NET 框架的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="4e860-161">Configuration file schema for the .NET Framework</span></span>](index.md)
