---
title: <add> NameValueSectionHandler 和 DictionarySectionHandler 的項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 9b421b4bab32c1aae7a6ba7d69b9f4aea2ab99a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705489"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="f23fc-102"> \<新增> NameValueSectionHandler 和 DictionarySectionHandler 的項目</span><span class="sxs-lookup"><span data-stu-id="f23fc-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="f23fc-103">加入自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="f23fc-103">Adds custom application settings.</span></span> <span data-ttu-id="f23fc-104">每個 **\<新增>** 標記包含索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="f23fc-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="f23fc-105">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f23fc-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="f23fc-106">&nbsp;&nbsp;[ **\<sectionName>** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="f23fc-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="f23fc-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="f23fc-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f23fc-108">語法</span><span class="sxs-lookup"><span data-stu-id="f23fc-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="f23fc-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f23fc-109">Attributes</span></span>

| <span data-ttu-id="f23fc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f23fc-110">Attribute</span></span> | <span data-ttu-id="f23fc-111">描述</span><span class="sxs-lookup"><span data-stu-id="f23fc-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="f23fc-112">**key**</span><span class="sxs-lookup"><span data-stu-id="f23fc-112">**key**</span></span>   | <span data-ttu-id="f23fc-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f23fc-113">Required attribute.</span></span><br><br><span data-ttu-id="f23fc-114">指定之設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="f23fc-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="f23fc-115">**value**</span><span class="sxs-lookup"><span data-stu-id="f23fc-115">**value**</span></span> | <span data-ttu-id="f23fc-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f23fc-116">Required attribute.</span></span><br><br><span data-ttu-id="f23fc-117">指定設定的值。</span><span class="sxs-lookup"><span data-stu-id="f23fc-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="f23fc-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f23fc-118">Parent element</span></span>

| <span data-ttu-id="f23fc-119">項目</span><span class="sxs-lookup"><span data-stu-id="f23fc-119">Element</span></span> | <span data-ttu-id="f23fc-120">描述</span><span class="sxs-lookup"><span data-stu-id="f23fc-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="f23fc-121"> *\*\<sectionName >** 項目</span><span class="sxs-lookup"><span data-stu-id="f23fc-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="f23fc-122">定義設定使用的自訂組態區段<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="f23fc-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="f23fc-123">子元素</span><span class="sxs-lookup"><span data-stu-id="f23fc-123">Child elements</span></span>

<span data-ttu-id="f23fc-124">None</span><span class="sxs-lookup"><span data-stu-id="f23fc-124">None</span></span>

## <a name="example"></a><span data-ttu-id="f23fc-125">範例</span><span class="sxs-lookup"><span data-stu-id="f23fc-125">Example</span></span>

<span data-ttu-id="f23fc-126">下列範例示範如何定義自訂組態區段，然後使用 **\<新增>** 放一節中的設定項目：</span><span class="sxs-lookup"><span data-stu-id="f23fc-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="f23fc-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="f23fc-127">Configuration file</span></span>

<span data-ttu-id="f23fc-128">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="f23fc-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="f23fc-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f23fc-129">See also</span></span>

- [<span data-ttu-id="f23fc-130">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f23fc-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
