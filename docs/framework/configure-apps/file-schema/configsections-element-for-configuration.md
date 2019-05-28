---
title: <configuration> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: dc2bb949c7db4f70c20c3c0b687cacafed8696df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674791"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="2a3d1-102">\<configSections > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="2a3d1-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="2a3d1-103">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="2a3d1-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2a3d1-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="2a3d1-105">&nbsp;&nbsp; **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="2a3d1-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="2a3d1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="2a3d1-106">Attributes</span></span>

<span data-ttu-id="2a3d1-107">None</span><span class="sxs-lookup"><span data-stu-id="2a3d1-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="2a3d1-108">父項目</span><span class="sxs-lookup"><span data-stu-id="2a3d1-108">Parent element</span></span>

|     | <span data-ttu-id="2a3d1-109">描述</span><span class="sxs-lookup"><span data-stu-id="2a3d1-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2a3d1-110"> *\*\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2a3d1-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="2a3d1-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2a3d1-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2a3d1-112">Child elements</span></span>

|     | <span data-ttu-id="2a3d1-113">描述</span><span class="sxs-lookup"><span data-stu-id="2a3d1-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2a3d1-114"> *\*\<section>** </span><span class="sxs-lookup"><span data-stu-id="2a3d1-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="2a3d1-115">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="2a3d1-116"> *\*\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="2a3d1-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="2a3d1-117">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="2a3d1-118"> *\*\<remove>** </span><span class="sxs-lookup"><span data-stu-id="2a3d1-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="2a3d1-119">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="2a3d1-120"> *\*\<clear>** </span><span class="sxs-lookup"><span data-stu-id="2a3d1-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="2a3d1-121">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2a3d1-122">備註</span><span class="sxs-lookup"><span data-stu-id="2a3d1-122">Remarks</span></span>

<span data-ttu-id="2a3d1-123">如果此項目是在組態檔中，它必須是第一個子項目 **\<組態>** 項目。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="2a3d1-124">範例</span><span class="sxs-lookup"><span data-stu-id="2a3d1-124">Example</span></span>

<span data-ttu-id="2a3d1-125">下列範例示範如何定義組態區段，並定義該區段的設定：</span><span class="sxs-lookup"><span data-stu-id="2a3d1-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="2a3d1-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="2a3d1-126">Configuration file</span></span>

<span data-ttu-id="2a3d1-127">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="2a3d1-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a3d1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a3d1-128">See also</span></span>

- [<span data-ttu-id="2a3d1-129">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2a3d1-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
