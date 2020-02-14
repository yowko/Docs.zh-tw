---
title: NameValueSectionHandler 和 DictionarySectionHandler 的 <add> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
ms.openlocfilehash: 57722f3518fad12cb8e6e35d68f40bb8465bdd86
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215444"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="945be-102">\<為 NameValueSectionHandler 和 DictionarySectionHandler 新增 > 元素</span><span class="sxs-lookup"><span data-stu-id="945be-102">\<add> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="945be-103">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="945be-103">Adds custom application settings.</span></span> <span data-ttu-id="945be-104">每個 **\<新增 >** 標記都包含一個索引鍵/值組。</span><span class="sxs-lookup"><span data-stu-id="945be-104">Each **\<add>** tag contains a key/value pair.</span></span>

<span data-ttu-id="945be-105">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="945be-105">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="945be-106">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="945be-106">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="945be-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="945be-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="945be-108">語法</span><span class="sxs-lookup"><span data-stu-id="945be-108">Syntax</span></span>

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a><span data-ttu-id="945be-109">屬性</span><span class="sxs-lookup"><span data-stu-id="945be-109">Attributes</span></span>

| <span data-ttu-id="945be-110">屬性</span><span class="sxs-lookup"><span data-stu-id="945be-110">Attribute</span></span> | <span data-ttu-id="945be-111">描述</span><span class="sxs-lookup"><span data-stu-id="945be-111">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="945be-112">**key**</span><span class="sxs-lookup"><span data-stu-id="945be-112">**key**</span></span>   | <span data-ttu-id="945be-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="945be-113">Required attribute.</span></span><br><br><span data-ttu-id="945be-114">指定設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="945be-114">Specifies the name of the setting.</span></span> |
| <span data-ttu-id="945be-115">**value**</span><span class="sxs-lookup"><span data-stu-id="945be-115">**value**</span></span> | <span data-ttu-id="945be-116">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="945be-116">Required attribute.</span></span><br><br><span data-ttu-id="945be-117">指定設定的值。</span><span class="sxs-lookup"><span data-stu-id="945be-117">Specifies the value of the setting.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="945be-118">父元素</span><span class="sxs-lookup"><span data-stu-id="945be-118">Parent element</span></span>

| <span data-ttu-id="945be-119">元素</span><span class="sxs-lookup"><span data-stu-id="945be-119">Element</span></span> | <span data-ttu-id="945be-120">描述</span><span class="sxs-lookup"><span data-stu-id="945be-120">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="945be-121"> **\<sectionName >** 元素</span><span class="sxs-lookup"><span data-stu-id="945be-121">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="945be-122">定義使用 <xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 類別之自訂設定區段的設定。</span><span class="sxs-lookup"><span data-stu-id="945be-122">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="945be-123">子元素</span><span class="sxs-lookup"><span data-stu-id="945be-123">Child elements</span></span>

<span data-ttu-id="945be-124">無</span><span class="sxs-lookup"><span data-stu-id="945be-124">None</span></span>

## <a name="example"></a><span data-ttu-id="945be-125">範例</span><span class="sxs-lookup"><span data-stu-id="945be-125">Example</span></span>

<span data-ttu-id="945be-126">下列範例示範如何定義自訂設定區段，並使用 **\<新增 >** 元素，將設定放入區段中：</span><span class="sxs-lookup"><span data-stu-id="945be-126">The following example shows how to define a custom configuration section and use the **\<add>** element to put settings into the section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="945be-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="945be-127">Configuration file</span></span>

<span data-ttu-id="945be-128">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="945be-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="945be-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="945be-129">See also</span></span>

- [<span data-ttu-id="945be-130">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="945be-130">Configuration file schema for the .NET Framework</span></span>](index.md)
