---
title: <clear> NameValueSectionHandler 和 DictionarySectionHandler 的項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: ad3ac93b2a7f92cd33787620fc0caa2b632aa072
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281871"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="120fc-102">\<清除 > NameValueSectionHandler 和 DictionarySectionHandler 的項目</span><span class="sxs-lookup"><span data-stu-id="120fc-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="120fc-103">清除所有先前定義的設定區段中。</span><span class="sxs-lookup"><span data-stu-id="120fc-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="120fc-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="120fc-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="120fc-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="120fc-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="120fc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="120fc-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="120fc-107">語法</span><span class="sxs-lookup"><span data-stu-id="120fc-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="120fc-108">屬性</span><span class="sxs-lookup"><span data-stu-id="120fc-108">Attributes</span></span>

<span data-ttu-id="120fc-109">無</span><span class="sxs-lookup"><span data-stu-id="120fc-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="120fc-110">父項目</span><span class="sxs-lookup"><span data-stu-id="120fc-110">Parent element</span></span>

|     | <span data-ttu-id="120fc-111">描述</span><span class="sxs-lookup"><span data-stu-id="120fc-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="120fc-112">**\<sectionName >** 項目</span><span class="sxs-lookup"><span data-stu-id="120fc-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="120fc-113">定義設定使用的自訂組態區段<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="120fc-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="120fc-114">子元素</span><span class="sxs-lookup"><span data-stu-id="120fc-114">Child elements</span></span>

<span data-ttu-id="120fc-115">無</span><span class="sxs-lookup"><span data-stu-id="120fc-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="120fc-116">備註</span><span class="sxs-lookup"><span data-stu-id="120fc-116">Remarks</span></span>

<span data-ttu-id="120fc-117">您可以使用**\<清除 >** 来移除您已定義在組態檔階層架構中較高層級的應用程式中的所有設定項目。</span><span class="sxs-lookup"><span data-stu-id="120fc-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="120fc-118">範例</span><span class="sxs-lookup"><span data-stu-id="120fc-118">Example</span></span>

<span data-ttu-id="120fc-119">此範例中定義的機器組態檔案和應用程式組態檔，並示範如何使用**\<清除 >** 清除區段中預先定義的應用程式組態檔中的項目電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="120fc-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="120fc-120">下列的機器組態檔案程式碼會宣告一節 **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="120fc-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="120fc-121">下列應用程式組態檔程式碼中移除的所有設定 **\<mySection >**。</span><span class="sxs-lookup"><span data-stu-id="120fc-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="120fc-122">應用程式無法擷取的任何設定中所宣告的中 **\<mySection >** 機器組態檔區段。</span><span class="sxs-lookup"><span data-stu-id="120fc-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="120fc-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="120fc-123">Configuration file</span></span>

<span data-ttu-id="120fc-124">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="120fc-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="120fc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="120fc-125">See also</span></span>

- [<span data-ttu-id="120fc-126">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="120fc-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
