---
title: '&lt;c&gt;元素&lt;組態&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 33406a67389cdf857fa5030e20d8a4dec7662741
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32752074"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="64f96-102">\<c > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="64f96-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="64f96-103">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="64f96-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="64f96-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="64f96-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="64f96-105">&nbsp;&nbsp;**\<c >**</span><span class="sxs-lookup"><span data-stu-id="64f96-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="64f96-106">屬性</span><span class="sxs-lookup"><span data-stu-id="64f96-106">Attributes</span></span>

<span data-ttu-id="64f96-107">無</span><span class="sxs-lookup"><span data-stu-id="64f96-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="64f96-108">父項目</span><span class="sxs-lookup"><span data-stu-id="64f96-108">Parent element</span></span>

|     | <span data-ttu-id="64f96-109">描述</span><span class="sxs-lookup"><span data-stu-id="64f96-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="64f96-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="64f96-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="64f96-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="64f96-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="64f96-112">子元素</span><span class="sxs-lookup"><span data-stu-id="64f96-112">Child elements</span></span>

|     | <span data-ttu-id="64f96-113">描述</span><span class="sxs-lookup"><span data-stu-id="64f96-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="64f96-114">**\<區段 >**</span><span class="sxs-lookup"><span data-stu-id="64f96-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="64f96-115">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="64f96-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="64f96-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="64f96-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="64f96-117">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="64f96-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="64f96-118">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="64f96-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="64f96-119">預先定義的區段或區段群組中移除。</span><span class="sxs-lookup"><span data-stu-id="64f96-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="64f96-120">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="64f96-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="64f96-121">清除所有先前定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="64f96-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="64f96-122">備註</span><span class="sxs-lookup"><span data-stu-id="64f96-122">Remarks</span></span>

<span data-ttu-id="64f96-123">如果此項目是在組態檔中，它必須是第一個子元素的**\<組態 >** 項目。</span><span class="sxs-lookup"><span data-stu-id="64f96-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="64f96-124">範例</span><span class="sxs-lookup"><span data-stu-id="64f96-124">Example</span></span>

<span data-ttu-id="64f96-125">下列範例會示範如何定義組態區段，並定義區段的設定：</span><span class="sxs-lookup"><span data-stu-id="64f96-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="64f96-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="64f96-126">Configuration file</span></span>

<span data-ttu-id="64f96-127">此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="64f96-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="64f96-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64f96-128">See also</span></span>

[<span data-ttu-id="64f96-129">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="64f96-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
