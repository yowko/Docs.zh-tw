---
title: <remove> NameValueSectionHandler 和 DictionarySectionHandler 的項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 062aa3921d29cffd33db2d96096ef25c2b819030
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300703"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="498f8-102">\<移除 > NameValueSectionHandler 和 DictionarySectionHandler 的項目</span><span class="sxs-lookup"><span data-stu-id="498f8-102">\<remove> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="498f8-103">移除先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="498f8-103">Removes a previously defined setting.</span></span>

<span data-ttu-id="498f8-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="498f8-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="498f8-105">&nbsp;&nbsp;[ **\<sectionName>** ](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="498f8-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="498f8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="498f8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="498f8-107">語法</span><span class="sxs-lookup"><span data-stu-id="498f8-107">Syntax</span></span>

```xml
<add remove="key" />
```

## <a name="attribute"></a><span data-ttu-id="498f8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="498f8-108">Attribute</span></span>

|           | <span data-ttu-id="498f8-109">描述</span><span class="sxs-lookup"><span data-stu-id="498f8-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="498f8-110">**key**</span><span class="sxs-lookup"><span data-stu-id="498f8-110">**key**</span></span>   | <span data-ttu-id="498f8-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="498f8-111">Required attribute.</span></span><br><br><span data-ttu-id="498f8-112">指定要移除之設定的名稱。</span><span class="sxs-lookup"><span data-stu-id="498f8-112">Specifies the name of the setting to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="498f8-113">父項目</span><span class="sxs-lookup"><span data-stu-id="498f8-113">Parent element</span></span>

| <span data-ttu-id="498f8-114">項目</span><span class="sxs-lookup"><span data-stu-id="498f8-114">Element</span></span> | <span data-ttu-id="498f8-115">描述</span><span class="sxs-lookup"><span data-stu-id="498f8-115">Description</span></span> |
| ------- | ------------|
| [<span data-ttu-id="498f8-116"> *\*\<sectionName >** 項目</span><span class="sxs-lookup"><span data-stu-id="498f8-116">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="498f8-117">定義設定使用的自訂組態區段<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="498f8-117">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="498f8-118">子元素</span><span class="sxs-lookup"><span data-stu-id="498f8-118">Child elements</span></span>

<span data-ttu-id="498f8-119">None</span><span class="sxs-lookup"><span data-stu-id="498f8-119">None</span></span>

## <a name="remarks"></a><span data-ttu-id="498f8-120">備註</span><span class="sxs-lookup"><span data-stu-id="498f8-120">Remarks</span></span>

<span data-ttu-id="498f8-121">您可以使用 **\<移除>** 來移除您已定義在組態檔階層架構中較高層級的應用程式設定的項目。</span><span class="sxs-lookup"><span data-stu-id="498f8-121">You can use the **\<remove>** element to remove settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="498f8-122">範例</span><span class="sxs-lookup"><span data-stu-id="498f8-122">Example</span></span>

<span data-ttu-id="498f8-123">下列範例示範如何使用 **\<移除>** 應用程式組態檔中移除先前在電腦組態檔中定義的設定項目。</span><span class="sxs-lookup"><span data-stu-id="498f8-123">The following example shows how to use the **\<remove>** element in an application configuration file to remove settings previously defined in the machine configuration file.</span></span>

<span data-ttu-id="498f8-124">下列的機器組態檔案程式碼會宣告一節 **\<mySection >** ，並將兩種設定`key1`和`key2`，給它：</span><span class="sxs-lookup"><span data-stu-id="498f8-124">The following machine configuration file code declares the section **\<mySection>** and adds two settings, `key1` and `key2`, to it:</span></span>

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

<span data-ttu-id="498f8-125">下列應用程式組態檔程式碼中移除`key2`上設定 **\<mySection >** :</span><span class="sxs-lookup"><span data-stu-id="498f8-125">The following application configuration file code removes the `key2` setting from **\<mySection>**:</span></span>

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="498f8-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="498f8-126">Configuration file</span></span>

<span data-ttu-id="498f8-127">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="498f8-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="498f8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="498f8-128">See also</span></span>

- [<span data-ttu-id="498f8-129">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="498f8-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
