---
title: <remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920953"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="0affe-102">\<移除 NameValueSectionHandler 和 DictionarySectionHandler > 元素</span><span class="sxs-lookup"><span data-stu-id="0affe-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="0affe-103">移除先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="0affe-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="0affe-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0affe-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="0affe-105">&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="0affe-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="0affe-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="0affe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="0affe-107">語法</span><span class="sxs-lookup"><span data-stu-id="0affe-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="0affe-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0affe-108">Attribute</span></span>

|           | <span data-ttu-id="0affe-109">描述</span><span class="sxs-lookup"><span data-stu-id="0affe-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="0affe-110">**key**</span><span class="sxs-lookup"><span data-stu-id="0affe-110">**key**</span></span>   | <span data-ttu-id="0affe-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0affe-111">Required attribute.</span></span><br><br><span data-ttu-id="0affe-112">指定要移除之設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="0affe-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="0affe-113">父項目</span><span class="sxs-lookup"><span data-stu-id="0affe-113">Parent element</span></span>

| <span data-ttu-id="0affe-114">項目</span><span class="sxs-lookup"><span data-stu-id="0affe-114">Element</span></span> | <span data-ttu-id="0affe-115">說明</span><span class="sxs-lookup"><span data-stu-id="0affe-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="0affe-116"> **sectionName>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="0affe-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="0affe-117">定義使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別之自訂設定區段的設定。</span><span class="sxs-lookup"><span data-stu-id="0affe-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0affe-118">子元素</span><span class="sxs-lookup"><span data-stu-id="0affe-118">Child elements</span></span>

<span data-ttu-id="0affe-119">None</span><span class="sxs-lookup"><span data-stu-id="0affe-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="0affe-120">備註</span><span class="sxs-lookup"><span data-stu-id="0affe-120">Remarks</span></span>

<span data-ttu-id="0affe-121">您可以使用 **\<移除>** 來移除您已定義在組態檔階層架構中較高層級的應用程式設定的項目。</span><span class="sxs-lookup"><span data-stu-id="0affe-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="0affe-122">範例</span><span class="sxs-lookup"><span data-stu-id="0affe-122">Example</span></span>

<span data-ttu-id="0affe-123">下列範例示範如何使用 **\<移除>** 應用程式組態檔中移除先前在電腦組態檔中定義的設定項目。</span><span class="sxs-lookup"><span data-stu-id="0affe-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="0affe-124">下列電腦設定檔程式碼會宣告區段 **\<mySection >** 並在其中`key1`新增`key2`兩個設定:</span><span class="sxs-lookup"><span data-stu-id="0affe-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="0affe-125">下列應用程式佈建檔案代碼會`key2`從 **\<mySection >** 移除設定:</span><span class="sxs-lookup"><span data-stu-id="0affe-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="0affe-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="0affe-126">Configuration file</span></span>

<span data-ttu-id="0affe-127">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="0affe-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0affe-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0affe-128">See also</span></span>

- [<span data-ttu-id="0affe-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="0affe-129">Configuration file schema for the .NET Framework</span></span>](index.md)
