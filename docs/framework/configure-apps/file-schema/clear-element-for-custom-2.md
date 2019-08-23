---
title: <clear>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: fbb689db4abc5d59729d9a4d9807a02a0983d40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927701"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="d9e01-102">\<清除> NameValueSectionHandler 和 DictionarySectionHandler 的項目</span><span class="sxs-lookup"><span data-stu-id="d9e01-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="d9e01-103">清除區段中所有先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="d9e01-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="d9e01-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d9e01-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="d9e01-105">&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="d9e01-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="d9e01-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="d9e01-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d9e01-107">語法</span><span class="sxs-lookup"><span data-stu-id="d9e01-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="d9e01-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d9e01-108">Attributes</span></span>

<span data-ttu-id="d9e01-109">無</span><span class="sxs-lookup"><span data-stu-id="d9e01-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="d9e01-110">父項目</span><span class="sxs-lookup"><span data-stu-id="d9e01-110">Parent element</span></span>

|     | <span data-ttu-id="d9e01-111">描述</span><span class="sxs-lookup"><span data-stu-id="d9e01-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="d9e01-112"> **sectionName>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="d9e01-112">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="d9e01-113">定義使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別之自訂設定區段的設定。</span><span class="sxs-lookup"><span data-stu-id="d9e01-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d9e01-114">子元素</span><span class="sxs-lookup"><span data-stu-id="d9e01-114">Child elements</span></span>

<span data-ttu-id="d9e01-115">無</span><span class="sxs-lookup"><span data-stu-id="d9e01-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d9e01-116">備註</span><span class="sxs-lookup"><span data-stu-id="d9e01-116">Remarks</span></span>

<span data-ttu-id="d9e01-117">您可以使用 **\<清除>** 来移除您已定義在組態檔階層架構中較高層級的應用程式中的所有設定項目。</span><span class="sxs-lookup"><span data-stu-id="d9e01-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="d9e01-118">範例</span><span class="sxs-lookup"><span data-stu-id="d9e01-118">Example</span></span>

<span data-ttu-id="d9e01-119">此範例中定義的機器組態檔案和應用程式組態檔，並示範如何使用 **\<清除>** 清除區段中預先定義的應用程式組態檔中的項目電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="d9e01-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="d9e01-120">下列電腦設定檔程式碼會宣告 **\<mySection >** 區段:</span><span class="sxs-lookup"><span data-stu-id="d9e01-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="d9e01-121">下列應用程式佈建檔案代碼會從 **\<mySection >** 移除所有設定。</span><span class="sxs-lookup"><span data-stu-id="d9e01-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="d9e01-122">應用程式無法在電腦設定檔的 **\<mySection >** 區段中, 取得在中宣告的任何設定。</span><span class="sxs-lookup"><span data-stu-id="d9e01-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="d9e01-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="d9e01-123">Configuration file</span></span>

<span data-ttu-id="d9e01-124">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="d9e01-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9e01-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9e01-125">See also</span></span>

- [<span data-ttu-id="d9e01-126">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="d9e01-126">Configuration file schema for the .NET Framework</span></span>](index.md)
