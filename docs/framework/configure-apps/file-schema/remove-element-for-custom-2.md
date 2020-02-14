---
title: NameValueSectionHandler 和 DictionarySectionHandler 的 <remove> 元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214761"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="cbeb9-102">\<移除 NameValueSectionHandler 和 DictionarySectionHandler 的 > 元素</span><span class="sxs-lookup"><span data-stu-id="cbeb9-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="cbeb9-103">移除先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="cbeb9-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="cbeb9-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cbeb9-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="cbeb9-105">&nbsp;&nbsp;[ **\<sectionName >** ](custom-element-2.md)</span><span class="sxs-lookup"><span data-stu-id="cbeb9-105">&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)</span></span>\
<span data-ttu-id="cbeb9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="cbeb9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cbeb9-107">語法</span><span class="sxs-lookup"><span data-stu-id="cbeb9-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="cbeb9-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cbeb9-108">Attribute</span></span>

|           | <span data-ttu-id="cbeb9-109">描述</span><span class="sxs-lookup"><span data-stu-id="cbeb9-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cbeb9-110">**key**</span><span class="sxs-lookup"><span data-stu-id="cbeb9-110">**key**</span></span>   | <span data-ttu-id="cbeb9-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cbeb9-111">Required attribute.</span></span><br><br><span data-ttu-id="cbeb9-112">指定要移除之設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbeb9-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="cbeb9-113">父元素</span><span class="sxs-lookup"><span data-stu-id="cbeb9-113">Parent element</span></span>

| <span data-ttu-id="cbeb9-114">元素</span><span class="sxs-lookup"><span data-stu-id="cbeb9-114">Element</span></span> | <span data-ttu-id="cbeb9-115">描述</span><span class="sxs-lookup"><span data-stu-id="cbeb9-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="cbeb9-116"> **\<sectionName >** 元素</span><span class="sxs-lookup"><span data-stu-id="cbeb9-116">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="cbeb9-117">定義使用 <xref:System.Configuration.NameValueSectionHandler> 和 <xref:System.Configuration.DictionarySectionHandler> 類別之自訂設定區段的設定。</span><span class="sxs-lookup"><span data-stu-id="cbeb9-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cbeb9-118">子元素</span><span class="sxs-lookup"><span data-stu-id="cbeb9-118">Child elements</span></span>

<span data-ttu-id="cbeb9-119">None</span><span class="sxs-lookup"><span data-stu-id="cbeb9-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="cbeb9-120">備註</span><span class="sxs-lookup"><span data-stu-id="cbeb9-120">Remarks</span></span>

<span data-ttu-id="cbeb9-121">您可以使用 **\<移除 >** 元素，從您的應用程式中移除在設定檔階層中較高層級定義的設定。</span><span class="sxs-lookup"><span data-stu-id="cbeb9-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="cbeb9-122">範例</span><span class="sxs-lookup"><span data-stu-id="cbeb9-122">Example</span></span>

<span data-ttu-id="cbeb9-123">下列範例示範如何使用應用程式佈建檔中的 **\<移除 >** 元素，以移除先前在電腦設定檔中定義的設定。</span><span class="sxs-lookup"><span data-stu-id="cbeb9-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="cbeb9-124">下列電腦設定檔程式碼會宣告 **\<mySection >** 區段，並在其中加入兩個設定，`key1` 和 `key2`：</span><span class="sxs-lookup"><span data-stu-id="cbeb9-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="cbeb9-125">下列應用程式佈建檔案代碼會從 **\<mySection >** 移除 `key2` 設定：</span><span class="sxs-lookup"><span data-stu-id="cbeb9-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="cbeb9-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="cbeb9-126">Configuration file</span></span>

<span data-ttu-id="cbeb9-127">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="cbeb9-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cbeb9-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbeb9-128">See also</span></span>

- [<span data-ttu-id="cbeb9-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="cbeb9-129">Configuration file schema for the .NET Framework</span></span>](index.md)
