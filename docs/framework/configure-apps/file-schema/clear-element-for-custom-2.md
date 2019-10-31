---
title: NameValueSectionHandler 和 DictionarySectionHandler 的 <clear> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e27bb7e21baf2eb4990d0107db4aae1b5f9a7d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119067"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="58c3d-102">\<清除 NameValueSectionHandler 和 DictionarySectionHandler 的 > 元素</span><span class="sxs-lookup"><span data-stu-id="58c3d-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="58c3d-103">清除區段中所有先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="58c3d-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="58c3d-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="58c3d-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="58c3d-105">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="58c3d-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="58c3d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="58c3d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="58c3d-107">語法</span><span class="sxs-lookup"><span data-stu-id="58c3d-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="58c3d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="58c3d-108">Attributes</span></span>

<span data-ttu-id="58c3d-109">None</span><span class="sxs-lookup"><span data-stu-id="58c3d-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="58c3d-110">父項目</span><span class="sxs-lookup"><span data-stu-id="58c3d-110">Parent element</span></span>

|     | <span data-ttu-id="58c3d-111">描述</span><span class="sxs-lookup"><span data-stu-id="58c3d-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="58c3d-112"> **\<sectionName >** 元素</span><span class="sxs-lookup"><span data-stu-id="58c3d-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="58c3d-113">定義使用 <xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 類別之自訂設定區段的設定。</span><span class="sxs-lookup"><span data-stu-id="58c3d-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="58c3d-114">子元素</span><span class="sxs-lookup"><span data-stu-id="58c3d-114">Child elements</span></span>

<span data-ttu-id="58c3d-115">None</span><span class="sxs-lookup"><span data-stu-id="58c3d-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="58c3d-116">備註</span><span class="sxs-lookup"><span data-stu-id="58c3d-116">Remarks</span></span>

<span data-ttu-id="58c3d-117">您可以使用 **\<clear >** 元素，從您的應用程式中移除在設定檔階層中較高層級定義的所有設定。</span><span class="sxs-lookup"><span data-stu-id="58c3d-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="58c3d-118">範例</span><span class="sxs-lookup"><span data-stu-id="58c3d-118">Example</span></span>

<span data-ttu-id="58c3d-119">這個範例會定義電腦設定檔和應用程式佈建檔，並示範如何使用應用程式佈建檔中的 **\<clear >** 元素，清除電腦設定檔中先前定義的區段。</span><span class="sxs-lookup"><span data-stu-id="58c3d-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="58c3d-120">下列電腦設定檔程式碼會宣告 **\<mySection >** 的區段：</span><span class="sxs-lookup"><span data-stu-id="58c3d-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="58c3d-121">下列應用程式佈建檔案代碼會移除 **\<mySection >** 的所有設定。</span><span class="sxs-lookup"><span data-stu-id="58c3d-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="58c3d-122">應用程式無法在電腦設定檔的 **\<mySection >** 區段中，取得在中宣告的任何設定。</span><span class="sxs-lookup"><span data-stu-id="58c3d-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="58c3d-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="58c3d-123">Configuration file</span></span>

<span data-ttu-id="58c3d-124">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="58c3d-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="58c3d-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="58c3d-125">See also</span></span>

- [<span data-ttu-id="58c3d-126">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="58c3d-126">Configuration file schema for the .NET Framework</span></span>](index.md)
