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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153722"
---
# <a name="section-element"></a><span data-ttu-id="6f34e-102">\<section> 項目</span><span class="sxs-lookup"><span data-stu-id="6f34e-102">\<section> element</span></span>

<span data-ttu-id="6f34e-103">包含設定區段宣告。</span><span class="sxs-lookup"><span data-stu-id="6f34e-103">Contains a configuration section declaration.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<section>**

## <a name="syntax"></a><span data-ttu-id="6f34e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6f34e-104">Syntax</span></span>

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication"
         allowLocation="true|false" />
```

## <a name="required-attributes"></a><span data-ttu-id="6f34e-105">必要的屬性</span><span class="sxs-lookup"><span data-stu-id="6f34e-105">Required attributes</span></span>

|           | <span data-ttu-id="6f34e-106">描述</span><span class="sxs-lookup"><span data-stu-id="6f34e-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="6f34e-107">**name**</span><span class="sxs-lookup"><span data-stu-id="6f34e-107">**name**</span></span>  | <span data-ttu-id="6f34e-108">指定設定區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="6f34e-108">Specifies the name of the configuration section.</span></span> |
| <span data-ttu-id="6f34e-109">**type**</span><span class="sxs-lookup"><span data-stu-id="6f34e-109">**type**</span></span>  | <span data-ttu-id="6f34e-110">指定在設定檔案中讀取區段的設定區段處理常式類別名稱。</span><span class="sxs-lookup"><span data-stu-id="6f34e-110">Specifies the name of the configuration section handler class that reads the section from the configuration file.</span></span> <span data-ttu-id="6f34e-111">類型值的語法為「完整區段-處理常式類別名稱，簡單元件名稱」。</span><span class="sxs-lookup"><span data-stu-id="6f34e-111">The type value has the syntax "fully-qualified-section-handler-class-name, simple-assembly-name".</span></span> <span data-ttu-id="6f34e-112">簡單元件名稱是不含 *.dll*副檔名的根檔案名。</span><span class="sxs-lookup"><span data-stu-id="6f34e-112">The simple assembly name is the root filename without the *.dll* file extension.</span></span> |

## <a name="optional-attributes"></a><span data-ttu-id="6f34e-113">選擇性屬性</span><span class="sxs-lookup"><span data-stu-id="6f34e-113">Optional attributes</span></span>

<span data-ttu-id="6f34e-114">下列屬性僅適用于 ASP.NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="6f34e-114">The following attributes are applicable only for ASP.NET applications.</span></span> <span data-ttu-id="6f34e-115">設定系統會忽略其他應用程式類型的這些屬性。</span><span class="sxs-lookup"><span data-stu-id="6f34e-115">The configuration system ignores these attributes for other application types.</span></span>

|                     | <span data-ttu-id="6f34e-116">描述</span><span class="sxs-lookup"><span data-stu-id="6f34e-116">Description</span></span> |
| ------------------- | ----------- |
| <span data-ttu-id="6f34e-117">**allowDefinition**</span><span class="sxs-lookup"><span data-stu-id="6f34e-117">**allowDefinition**</span></span> | <span data-ttu-id="6f34e-118">指定區段可以用於哪一個設定檔。</span><span class="sxs-lookup"><span data-stu-id="6f34e-118">Specifies which configuration file the section can be used in.</span></span> <span data-ttu-id="6f34e-119">請使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="6f34e-119">Use one of the following values:</span></span><br><br><span data-ttu-id="6f34e-120">**所有位置**</span><span class="sxs-lookup"><span data-stu-id="6f34e-120">**Everywhere**</span></span><br><span data-ttu-id="6f34e-121">允許在任何設定檔案中使用區段。</span><span class="sxs-lookup"><span data-stu-id="6f34e-121">Allows the section to be used in any configuration file.</span></span> <span data-ttu-id="6f34e-122">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="6f34e-122">This is the default.</span></span><br><span data-ttu-id="6f34e-123">**MachineOnly**</span><span class="sxs-lookup"><span data-stu-id="6f34e-123">**MachineOnly**</span></span><br><span data-ttu-id="6f34e-124">允許區段僅用於電腦設定檔（*machine.config*）。</span><span class="sxs-lookup"><span data-stu-id="6f34e-124">Allows the section to be used only in the machine configuration file (*Machine.config*).</span></span><br><span data-ttu-id="6f34e-125">**MachineToApplication**</span><span class="sxs-lookup"><span data-stu-id="6f34e-125">**MachineToApplication**</span></span><br><span data-ttu-id="6f34e-126">允許在電腦設定檔或應用程式佈建檔中使用區段。</span><span class="sxs-lookup"><span data-stu-id="6f34e-126">Allows the section to be used in the machine configuration file or the application configuration file.</span></span> |
| <span data-ttu-id="6f34e-127">**allowLocation**</span><span class="sxs-lookup"><span data-stu-id="6f34e-127">**allowLocation**</span></span>   | <span data-ttu-id="6f34e-128">判斷區段是否可以在元素內使用 **\<location>** 。</span><span class="sxs-lookup"><span data-stu-id="6f34e-128">Determines whether the section can be used within the **\<location>** element.</span></span> <span data-ttu-id="6f34e-129">請使用下列其中一個值：</span><span class="sxs-lookup"><span data-stu-id="6f34e-129">Use one of the following values:</span></span><br><br><span data-ttu-id="6f34e-130">**true**</span><span class="sxs-lookup"><span data-stu-id="6f34e-130">**true**</span></span><br><span data-ttu-id="6f34e-131">允許在元素內使用區段 **\<location>** 。</span><span class="sxs-lookup"><span data-stu-id="6f34e-131">Allows the section to be used within the **\<location>** element.</span></span> <span data-ttu-id="6f34e-132">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="6f34e-132">This is the default.</span></span><br><span data-ttu-id="6f34e-133">**false**</span><span class="sxs-lookup"><span data-stu-id="6f34e-133">**false**</span></span><br><span data-ttu-id="6f34e-134">不允許在元素內使用區段 **\<location>** 。</span><span class="sxs-lookup"><span data-stu-id="6f34e-134">Does not allow the section to be used within the **\<location>** element.</span></span> |

## <a name="parent-elements"></a><span data-ttu-id="6f34e-135">父元素</span><span class="sxs-lookup"><span data-stu-id="6f34e-135">Parent elements</span></span>

|     | <span data-ttu-id="6f34e-136">描述</span><span class="sxs-lookup"><span data-stu-id="6f34e-136">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6f34e-137">**\<configSections>** 元素</span><span class="sxs-lookup"><span data-stu-id="6f34e-137">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="6f34e-138">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="6f34e-138">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="6f34e-139">**\<sectionGroup>** 元素</span><span class="sxs-lookup"><span data-stu-id="6f34e-139">**\<sectionGroup>** Element</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="6f34e-140">定義設定區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="6f34e-140">Defines a namespace for configuration sections.</span></span> |

> [!NOTE]
> <span data-ttu-id="6f34e-141">**\<section>** 元素是或的子項目， **\<configSections>** **\<sectionGroup>** 但不能同時是兩者。</span><span class="sxs-lookup"><span data-stu-id="6f34e-141">A **\<section>** element is a child element of either **\<configSections>** or **\<sectionGroup>** but not both.</span></span>

## <a name="child-elements"></a><span data-ttu-id="6f34e-142">子元素</span><span class="sxs-lookup"><span data-stu-id="6f34e-142">Child elements</span></span>

<span data-ttu-id="6f34e-143">None</span><span class="sxs-lookup"><span data-stu-id="6f34e-143">None</span></span>

## <a name="remarks"></a><span data-ttu-id="6f34e-144">備註</span><span class="sxs-lookup"><span data-stu-id="6f34e-144">Remarks</span></span>

<span data-ttu-id="6f34e-145">宣告設定區段基本上會定義設定檔的新元素。</span><span class="sxs-lookup"><span data-stu-id="6f34e-145">Declaring a configuration section essentially defines a new element for the configuration file.</span></span> <span data-ttu-id="6f34e-146">新專案包含設定區段處理常式（也就是執行介面的類別）會讀取的設定 <xref:System.Configuration.IConfigurationSectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="6f34e-146">The new element contains settings that a configuration section handler (that is, a class that implements the <xref:System.Configuration.IConfigurationSectionHandler> interface) reads.</span></span> <span data-ttu-id="6f34e-147">您所定義之區段的屬性和子專案，取決於您用來讀取設定的區段處理常式。</span><span class="sxs-lookup"><span data-stu-id="6f34e-147">The attributes and child elements of a section you define depend on the section handler you use to read your settings.</span></span>

<span data-ttu-id="6f34e-148">在*machine.config*檔案中宣告設定區段處理常式，可讓您在該電腦上的任何應用程式佈建檔中使用 configuration 區段，除非**allowDefinition**屬性另行指定。</span><span class="sxs-lookup"><span data-stu-id="6f34e-148">Declaring a configuration section handler in the *Machine.config* file enables you to use the configuration section in any application configuration file on that computer, unless the **allowDefinition** attribute specifies otherwise.</span></span>

## <a name="example"></a><span data-ttu-id="6f34e-149">範例</span><span class="sxs-lookup"><span data-stu-id="6f34e-149">Example</span></span>

<span data-ttu-id="6f34e-150">下列範例顯示如何定義設定區段，並定義該區段的設定：</span><span class="sxs-lookup"><span data-stu-id="6f34e-150">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="6f34e-151">組態檔</span><span class="sxs-lookup"><span data-stu-id="6f34e-151">Configuration file</span></span>

<span data-ttu-id="6f34e-152">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="6f34e-152">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f34e-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f34e-153">See also</span></span>

- [<span data-ttu-id="6f34e-154">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="6f34e-154">Configuration file schema for the .NET Framework</span></span>](index.md)
