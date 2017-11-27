---
title: "&lt;c&gt;元素&lt;組態&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7bcf425f345a3153a83cc60e76d87b3c32d83dbe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="0c87a-102">\<c > 項目\<設定 ></span><span class="sxs-lookup"><span data-stu-id="0c87a-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="0c87a-103">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="0c87a-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="0c87a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="0c87a-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="0c87a-105">&nbsp;&nbsp;**\<c >**</span><span class="sxs-lookup"><span data-stu-id="0c87a-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="0c87a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="0c87a-106">Attributes</span></span>

<span data-ttu-id="0c87a-107">無</span><span class="sxs-lookup"><span data-stu-id="0c87a-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="0c87a-108">父項目</span><span class="sxs-lookup"><span data-stu-id="0c87a-108">Parent element</span></span>

|     | <span data-ttu-id="0c87a-109">說明</span><span class="sxs-lookup"><span data-stu-id="0c87a-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0c87a-110">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="0c87a-110">**\<configuration>**</span></span>](~/docs/framework/configure-apps/file-schema/configuration-element.md) | <span data-ttu-id="0c87a-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0c87a-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="0c87a-112">子元素</span><span class="sxs-lookup"><span data-stu-id="0c87a-112">Child elements</span></span>

|     | <span data-ttu-id="0c87a-113">說明</span><span class="sxs-lookup"><span data-stu-id="0c87a-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="0c87a-114">**\<區段 >**</span><span class="sxs-lookup"><span data-stu-id="0c87a-114">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="0c87a-115">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="0c87a-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="0c87a-116">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="0c87a-116">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="0c87a-117">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="0c87a-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="0c87a-118">**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="0c87a-118">**\<remove>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="0c87a-119">預先定義的區段或區段群組中移除。</span><span class="sxs-lookup"><span data-stu-id="0c87a-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="0c87a-120">**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="0c87a-120">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="0c87a-121">清除所有先前定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="0c87a-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="0c87a-122">備註</span><span class="sxs-lookup"><span data-stu-id="0c87a-122">Remarks</span></span>

<span data-ttu-id="0c87a-123">如果此項目是在組態檔中，它必須是第一個子元素的**\<組態 >**項目。</span><span class="sxs-lookup"><span data-stu-id="0c87a-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="0c87a-124">範例</span><span class="sxs-lookup"><span data-stu-id="0c87a-124">Example</span></span>

<span data-ttu-id="0c87a-125">下列範例會示範如何定義組態區段，並定義區段的設定：</span><span class="sxs-lookup"><span data-stu-id="0c87a-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="0c87a-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="0c87a-126">Configuration file</span></span>

<span data-ttu-id="0c87a-127">此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="0c87a-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c87a-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c87a-128">See also</span></span>

[<span data-ttu-id="0c87a-129">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0c87a-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
