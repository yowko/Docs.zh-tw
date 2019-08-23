---
title: <add>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921343"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="79dc7-102">\<新增> NameValueSectionHandler 和 DictionarySectionHandler 的項目</span><span class="sxs-lookup"><span data-stu-id="79dc7-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="79dc7-103">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="79dc7-103">Adds custom application settings.</span></span> <span data-ttu-id="79dc7-104">每個 **\<新增>** 標記包含索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="79dc7-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="79dc7-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="79dc7-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="79dc7-106">&nbsp;&nbsp;[ **\<sectionName>** ](custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="79dc7-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md) </span></span>  
<span data-ttu-id="79dc7-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="79dc7-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="79dc7-108">語法</span><span class="sxs-lookup"><span data-stu-id="79dc7-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="79dc7-109">屬性</span><span class="sxs-lookup"><span data-stu-id="79dc7-109">Attributes</span></span>

| <span data-ttu-id="79dc7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="79dc7-110">Attribute</span></span> | <span data-ttu-id="79dc7-111">描述</span><span class="sxs-lookup"><span data-stu-id="79dc7-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="79dc7-112">**key**</span><span class="sxs-lookup"><span data-stu-id="79dc7-112">**key**</span></span>   | <span data-ttu-id="79dc7-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="79dc7-113">Required attribute.</span></span><br><br><span data-ttu-id="79dc7-114">指定設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="79dc7-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="79dc7-115">**value**</span><span class="sxs-lookup"><span data-stu-id="79dc7-115">**value**</span></span> | <span data-ttu-id="79dc7-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="79dc7-116">Required attribute.</span></span><br><br><span data-ttu-id="79dc7-117">指定設定的值。</span><span class="sxs-lookup"><span data-stu-id="79dc7-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="79dc7-118">父項目</span><span class="sxs-lookup"><span data-stu-id="79dc7-118">Parent element</span></span>

| <span data-ttu-id="79dc7-119">項目</span><span class="sxs-lookup"><span data-stu-id="79dc7-119">Element</span></span> | <span data-ttu-id="79dc7-120">描述</span><span class="sxs-lookup"><span data-stu-id="79dc7-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="79dc7-121"> **sectionName>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="79dc7-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="79dc7-122">定義使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別之自訂設定區段的設定。</span><span class="sxs-lookup"><span data-stu-id="79dc7-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="79dc7-123">子元素</span><span class="sxs-lookup"><span data-stu-id="79dc7-123">Child elements</span></span>

<span data-ttu-id="79dc7-124">無</span><span class="sxs-lookup"><span data-stu-id="79dc7-124">None</span></span>

## <a name="example"></a><span data-ttu-id="79dc7-125">範例</span><span class="sxs-lookup"><span data-stu-id="79dc7-125">Example</span></span>

<span data-ttu-id="79dc7-126">下列範例示範如何定義自訂組態區段，然後使用 **\<新增>** 放一節中的設定項目：</span><span class="sxs-lookup"><span data-stu-id="79dc7-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="79dc7-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="79dc7-127">Configuration file</span></span>

<span data-ttu-id="79dc7-128">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="79dc7-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="79dc7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79dc7-129">See also</span></span>

- [<span data-ttu-id="79dc7-130">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="79dc7-130">Configuration file schema for the .NET Framework</span></span>](index.md)
