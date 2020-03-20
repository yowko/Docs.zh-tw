---
title: <configuration> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155345"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="58a69-102">\<配置>元素，用於\<配置></span><span class="sxs-lookup"><span data-stu-id="58a69-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="58a69-103">包含配置部分和命名空間聲明。</span><span class="sxs-lookup"><span data-stu-id="58a69-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="58a69-104">&nbsp; [\*\* \<配置>\*\*](configuration-element.md)&nbsp;**配置>\<**</span><span class="sxs-lookup"><span data-stu-id="58a69-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="58a69-105">屬性</span><span class="sxs-lookup"><span data-stu-id="58a69-105">Attributes</span></span>

<span data-ttu-id="58a69-106">None</span><span class="sxs-lookup"><span data-stu-id="58a69-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="58a69-107">父元素</span><span class="sxs-lookup"><span data-stu-id="58a69-107">Parent element</span></span>

|     | <span data-ttu-id="58a69-108">描述</span><span class="sxs-lookup"><span data-stu-id="58a69-108">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="58a69-109">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="58a69-109">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="58a69-110">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="58a69-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="58a69-111">子元素</span><span class="sxs-lookup"><span data-stu-id="58a69-111">Child elements</span></span>

|     | <span data-ttu-id="58a69-112">描述</span><span class="sxs-lookup"><span data-stu-id="58a69-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="58a69-113">**\<第>節**</span><span class="sxs-lookup"><span data-stu-id="58a69-113">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="58a69-114">包含配置部分聲明。</span><span class="sxs-lookup"><span data-stu-id="58a69-114">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="58a69-115">**\<部分組>**</span><span class="sxs-lookup"><span data-stu-id="58a69-115">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="58a69-116">為配置部分定義命名空間。</span><span class="sxs-lookup"><span data-stu-id="58a69-116">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="58a69-117">**\<刪除>**</span><span class="sxs-lookup"><span data-stu-id="58a69-117">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="58a69-118">刪除預定義的節或節組。</span><span class="sxs-lookup"><span data-stu-id="58a69-118">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="58a69-119">**\<明確>**</span><span class="sxs-lookup"><span data-stu-id="58a69-119">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="58a69-120">清除以前定義的所有節和節組。</span><span class="sxs-lookup"><span data-stu-id="58a69-120">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="58a69-121">備註</span><span class="sxs-lookup"><span data-stu-id="58a69-121">Remarks</span></span>

<span data-ttu-id="58a69-122">如果此元素位於設定檔中，則它必須是**\<配置>** 元素的第一個子項目。</span><span class="sxs-lookup"><span data-stu-id="58a69-122">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="58a69-123">範例</span><span class="sxs-lookup"><span data-stu-id="58a69-123">Example</span></span>

<span data-ttu-id="58a69-124">下面的示例演示如何定義配置部分並定義該部分的設置：</span><span class="sxs-lookup"><span data-stu-id="58a69-124">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="58a69-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="58a69-125">Configuration file</span></span>

<span data-ttu-id="58a69-126">此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。</span><span class="sxs-lookup"><span data-stu-id="58a69-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="58a69-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58a69-127">See also</span></span>

- [<span data-ttu-id="58a69-128">.NET 框架的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="58a69-128">Configuration file schema for the .NET Framework</span></span>](index.md)
