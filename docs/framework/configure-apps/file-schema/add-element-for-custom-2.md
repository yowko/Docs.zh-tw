---
title: <add>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215444"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="e5a3a-102">\<add>NameValueSectionHandler 和 DictionarySectionHandler 的元素</span><span class="sxs-lookup"><span data-stu-id="e5a3a-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="e5a3a-103">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-103">Adds custom application settings.</span></span> <span data-ttu-id="e5a3a-104">每個 **\<add>** 標記都包含一個索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-104">Each **\<add>** tag contains a key/value pair.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="e5a3a-105">語法</span><span class="sxs-lookup"><span data-stu-id="e5a3a-105">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="e5a3a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e5a3a-106">Attributes</span></span>

| <span data-ttu-id="e5a3a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e5a3a-107">Attribute</span></span> | <span data-ttu-id="e5a3a-108">描述</span><span class="sxs-lookup"><span data-stu-id="e5a3a-108">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="e5a3a-109">**key**</span><span class="sxs-lookup"><span data-stu-id="e5a3a-109">**key**</span></span>   | <span data-ttu-id="e5a3a-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-110">Required attribute.</span></span><br><br><span data-ttu-id="e5a3a-111">指定設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-111">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="e5a3a-112">**value**</span><span class="sxs-lookup"><span data-stu-id="e5a3a-112">**value**</span></span> | <span data-ttu-id="e5a3a-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-113">Required attribute.</span></span><br><br><span data-ttu-id="e5a3a-114">指定設定的值。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-114">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="e5a3a-115">父元素</span><span class="sxs-lookup"><span data-stu-id="e5a3a-115">Parent element</span></span>

| <span data-ttu-id="e5a3a-116">元素</span><span class="sxs-lookup"><span data-stu-id="e5a3a-116">Element</span></span> | <span data-ttu-id="e5a3a-117">描述</span><span class="sxs-lookup"><span data-stu-id="e5a3a-117">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="e5a3a-118">**\<sectionName>** 元素</span><span class="sxs-lookup"><span data-stu-id="e5a3a-118">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="e5a3a-119">定義使用和類別之自訂設定區段的設定 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-119">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e5a3a-120">子元素</span><span class="sxs-lookup"><span data-stu-id="e5a3a-120">Child elements</span></span>

<span data-ttu-id="e5a3a-121">None</span><span class="sxs-lookup"><span data-stu-id="e5a3a-121">None</span></span>

## <a name="example"></a><span data-ttu-id="e5a3a-122">範例</span><span class="sxs-lookup"><span data-stu-id="e5a3a-122">Example</span></span>

<span data-ttu-id="e5a3a-123">下列範例示範如何定義自訂的設定區段，並使用 **\<add>** 元素將設定放入區段中：</span><span class="sxs-lookup"><span data-stu-id="e5a3a-123">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="e5a3a-124">組態檔</span><span class="sxs-lookup"><span data-stu-id="e5a3a-124">Configuration file</span></span>

<span data-ttu-id="e5a3a-125">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="e5a3a-125">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5a3a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5a3a-126">See also</span></span>

- [<span data-ttu-id="e5a3a-127">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="e5a3a-127">Configuration file schema for the .NET Framework</span></span>](index.md)
