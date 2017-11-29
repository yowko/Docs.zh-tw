---
title: "&lt;新增&gt;NameValueSectionHandler DictionarySectionHandler 的項目"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e9dc671f0df9034410d20fdf69862884d6b3b300
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="26d4f-102">\<新增 > NameValueSectionHandler DictionarySectionHandler 的項目</span><span class="sxs-lookup"><span data-stu-id="26d4f-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="26d4f-103">加入自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="26d4f-103">Adds custom application settings.</span></span> <span data-ttu-id="26d4f-104">每個**\<新增 >**標記包含的索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="26d4f-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="26d4f-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="26d4f-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="26d4f-106">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="26d4f-106">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="26d4f-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="26d4f-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="26d4f-108">語法</span><span class="sxs-lookup"><span data-stu-id="26d4f-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="26d4f-109">屬性</span><span class="sxs-lookup"><span data-stu-id="26d4f-109">Attributes</span></span>

| <span data-ttu-id="26d4f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="26d4f-110">Attribute</span></span> | <span data-ttu-id="26d4f-111">說明</span><span class="sxs-lookup"><span data-stu-id="26d4f-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="26d4f-112">**key**</span><span class="sxs-lookup"><span data-stu-id="26d4f-112">**key**</span></span>   | <span data-ttu-id="26d4f-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="26d4f-113">Required attribute.</span></span><br><br><span data-ttu-id="26d4f-114">指定設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="26d4f-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="26d4f-115">**value**</span><span class="sxs-lookup"><span data-stu-id="26d4f-115">**value**</span></span> | <span data-ttu-id="26d4f-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="26d4f-116">Required attribute.</span></span><br><br><span data-ttu-id="26d4f-117">指定設定的值。</span><span class="sxs-lookup"><span data-stu-id="26d4f-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="26d4f-118">父項目</span><span class="sxs-lookup"><span data-stu-id="26d4f-118">Parent element</span></span>

| <span data-ttu-id="26d4f-119">項目</span><span class="sxs-lookup"><span data-stu-id="26d4f-119">Element</span></span> | <span data-ttu-id="26d4f-120">說明</span><span class="sxs-lookup"><span data-stu-id="26d4f-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="26d4f-121">**\<sectionName >**項目</span><span class="sxs-lookup"><span data-stu-id="26d4f-121">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="26d4f-122">定義自訂組態區段，使用設定<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="26d4f-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="26d4f-123">子元素</span><span class="sxs-lookup"><span data-stu-id="26d4f-123">Child elements</span></span>

<span data-ttu-id="26d4f-124">無</span><span class="sxs-lookup"><span data-stu-id="26d4f-124">None</span></span>

## <a name="example"></a><span data-ttu-id="26d4f-125">範例</span><span class="sxs-lookup"><span data-stu-id="26d4f-125">Example</span></span>

<span data-ttu-id="26d4f-126">下列範例示範如何定義自訂組態區段，然後使用**\<新增 >**放一節中的設定項目：</span><span class="sxs-lookup"><span data-stu-id="26d4f-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="26d4f-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="26d4f-127">Configuration file</span></span>

<span data-ttu-id="26d4f-128">此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="26d4f-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="26d4f-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="26d4f-129">See also</span></span>

[<span data-ttu-id="26d4f-130">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="26d4f-130">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
