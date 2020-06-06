---
title: <remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
ms.openlocfilehash: d1e4f3478f6afd6a20c01c6b57a137020ee88f5f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214761"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="a2fc8-102">\<remove>NameValueSectionHandler 和 DictionarySectionHandler 的元素</span><span class="sxs-lookup"><span data-stu-id="a2fc8-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="a2fc8-103">移除先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="a2fc8-103">Removes a previously defined setting.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="a2fc8-104">語法</span><span class="sxs-lookup"><span data-stu-id="a2fc8-104">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="a2fc8-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a2fc8-105">Attribute</span></span>

|           | <span data-ttu-id="a2fc8-106">描述</span><span class="sxs-lookup"><span data-stu-id="a2fc8-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a2fc8-107">**key**</span><span class="sxs-lookup"><span data-stu-id="a2fc8-107">**key**</span></span>   | <span data-ttu-id="a2fc8-108">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a2fc8-108">Required attribute.</span></span><br><br><span data-ttu-id="a2fc8-109">指定要移除之設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="a2fc8-109">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a2fc8-110">父元素</span><span class="sxs-lookup"><span data-stu-id="a2fc8-110">Parent element</span></span>

| <span data-ttu-id="a2fc8-111">元素</span><span class="sxs-lookup"><span data-stu-id="a2fc8-111">Element</span></span> | <span data-ttu-id="a2fc8-112">描述</span><span class="sxs-lookup"><span data-stu-id="a2fc8-112">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="a2fc8-113">**\<sectionName>** 元素</span><span class="sxs-lookup"><span data-stu-id="a2fc8-113">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="a2fc8-114">定義使用和類別之自訂設定區段的設定 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="a2fc8-114">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a2fc8-115">子元素</span><span class="sxs-lookup"><span data-stu-id="a2fc8-115">Child elements</span></span>

<span data-ttu-id="a2fc8-116">None</span><span class="sxs-lookup"><span data-stu-id="a2fc8-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="a2fc8-117">備註</span><span class="sxs-lookup"><span data-stu-id="a2fc8-117">Remarks</span></span>

<span data-ttu-id="a2fc8-118">您可以使用 **\<remove>** 元素，從您的應用程式中移除在設定檔階層中較高層級定義的設定。</span><span class="sxs-lookup"><span data-stu-id="a2fc8-118">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="a2fc8-119">範例</span><span class="sxs-lookup"><span data-stu-id="a2fc8-119">Example</span></span>

<span data-ttu-id="a2fc8-120">下列範例顯示如何使用 **\<remove>** 應用程式佈建檔中的專案，來移除先前在電腦設定檔中定義的設定。</span><span class="sxs-lookup"><span data-stu-id="a2fc8-120">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="a2fc8-121">下列電腦設定檔程式碼會宣告區段， **\<mySection>** 並在其中新增兩個設定 `key1` `key2` ：</span><span class="sxs-lookup"><span data-stu-id="a2fc8-121">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="a2fc8-122">下列應用程式佈建檔案代碼會 `key2` 從移除設定 **\<mySection>** ：</span><span class="sxs-lookup"><span data-stu-id="a2fc8-122">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="a2fc8-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="a2fc8-123">Configuration file</span></span>

<span data-ttu-id="a2fc8-124">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="a2fc8-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2fc8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2fc8-125">See also</span></span>

- [<span data-ttu-id="a2fc8-126">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="a2fc8-126">Configuration file schema for the .NET Framework</span></span>](index.md)
