---
title: <configSections> 的 <clear> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: e79def513637937262d00b0edb1b0f7676fd120b
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300796"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="ed855-102">\<清除>項目\<configSections ></span><span class="sxs-lookup"><span data-stu-id="ed855-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="ed855-103">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="ed855-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="ed855-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="ed855-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="ed855-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="ed855-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="ed855-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="ed855-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ed855-107">語法</span><span class="sxs-lookup"><span data-stu-id="ed855-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="ed855-108">屬性</span><span class="sxs-lookup"><span data-stu-id="ed855-108">Attribute</span></span>

|           | <span data-ttu-id="ed855-109">描述</span><span class="sxs-lookup"><span data-stu-id="ed855-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="ed855-110">**name**</span><span class="sxs-lookup"><span data-stu-id="ed855-110">**name**</span></span>  | <span data-ttu-id="ed855-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="ed855-111">Required attribute.</span></span><br><br><span data-ttu-id="ed855-112">指定要移除的區段群組之區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="ed855-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="ed855-113">父項目</span><span class="sxs-lookup"><span data-stu-id="ed855-113">Parent element</span></span>

|     | <span data-ttu-id="ed855-114">描述</span><span class="sxs-lookup"><span data-stu-id="ed855-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ed855-115"> *\*\<configSections >** 項目</span><span class="sxs-lookup"><span data-stu-id="ed855-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="ed855-116">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="ed855-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="ed855-117">子元素</span><span class="sxs-lookup"><span data-stu-id="ed855-117">Child elements</span></span>

<span data-ttu-id="ed855-118">None</span><span class="sxs-lookup"><span data-stu-id="ed855-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="ed855-119">備註</span><span class="sxs-lookup"><span data-stu-id="ed855-119">Remarks</span></span>

<span data-ttu-id="ed855-120">**\<清除>** 項目會從您先前已定義在目前的組態檔中或在組態檔階層架構中較高層級的應用程式移除所有區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="ed855-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="ed855-121">範例</span><span class="sxs-lookup"><span data-stu-id="ed855-121">Example</span></span>

<span data-ttu-id="ed855-122">此範例中定義的機器組態檔案和應用程式組態檔，並示範如何使用 **\<清除>** 清除區段中預先定義的應用程式組態檔中的項目電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="ed855-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="ed855-123">下列的機器組態檔案程式碼會宣告兩個區段 **\<sampleSection >** 並 **\<anotherSampleSection >** ，應用程式之前所讀取的來源組態檔：</span><span class="sxs-lookup"><span data-stu-id="ed855-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="ed855-124">下列應用程式組態檔程式碼會清除所有先前宣告的區段。</span><span class="sxs-lookup"><span data-stu-id="ed855-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="ed855-125">應用程式無法使用，或擷取在電腦組態檔中所宣告的各區段的設定。</span><span class="sxs-lookup"><span data-stu-id="ed855-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="ed855-126">不過，它可以在這裡使用的設定 **\<anotherSection>** 因為它的來源之後 **\<清除>** 項目。</span><span class="sxs-lookup"><span data-stu-id="ed855-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="ed855-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="ed855-127">Configuration file</span></span>

<span data-ttu-id="ed855-128">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="ed855-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="ed855-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed855-129">See also</span></span>

- [<span data-ttu-id="ed855-130">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ed855-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
