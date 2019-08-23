---
title: <configuration> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927663"
---
# <a name="configsections-element-for-configuration"></a><span data-ttu-id="2beec-102">\<configuration > 的\<configSections > 元素</span><span class="sxs-lookup"><span data-stu-id="2beec-102">\<configSections> element for \<configuration></span></span>

<span data-ttu-id="2beec-103">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="2beec-103">Contains configuration section and namespace declarations.</span></span>

<span data-ttu-id="2beec-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2beec-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="2beec-105">&nbsp;&nbsp; **\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="2beec-105">&nbsp;&nbsp;**\<configSections>**</span></span>

## <a name="attributes"></a><span data-ttu-id="2beec-106">屬性</span><span class="sxs-lookup"><span data-stu-id="2beec-106">Attributes</span></span>

<span data-ttu-id="2beec-107">無</span><span class="sxs-lookup"><span data-stu-id="2beec-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="2beec-108">父項目</span><span class="sxs-lookup"><span data-stu-id="2beec-108">Parent element</span></span>

|     | <span data-ttu-id="2beec-109">說明</span><span class="sxs-lookup"><span data-stu-id="2beec-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2beec-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="2beec-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="2beec-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2beec-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="2beec-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2beec-112">Child elements</span></span>

|     | <span data-ttu-id="2beec-113">描述</span><span class="sxs-lookup"><span data-stu-id="2beec-113">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2beec-114"> **\<區段 >** </span><span class="sxs-lookup"><span data-stu-id="2beec-114">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="2beec-115">包含設定區段宣告。</span><span class="sxs-lookup"><span data-stu-id="2beec-115">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="2beec-116"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="2beec-116">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="2beec-117">定義設定區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2beec-117">Defines a namespace for configuration sections.</span></span> |
| [<span data-ttu-id="2beec-118"> **\<remove>** </span><span class="sxs-lookup"><span data-stu-id="2beec-118">**\<remove>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="2beec-119">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="2beec-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="2beec-120"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="2beec-120">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="2beec-121">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="2beec-121">Clears all previously defined sections and section groups.</span></span> |

## <a name="remarks"></a><span data-ttu-id="2beec-122">備註</span><span class="sxs-lookup"><span data-stu-id="2beec-122">Remarks</span></span>

<span data-ttu-id="2beec-123">如果此項目是在組態檔中，它必須是第一個子項目 **\<組態>** 項目。</span><span class="sxs-lookup"><span data-stu-id="2beec-123">If this element is in a configuration file, it must be the first child element of the **\<configuration>** element.</span></span>

## <a name="example"></a><span data-ttu-id="2beec-124">範例</span><span class="sxs-lookup"><span data-stu-id="2beec-124">Example</span></span>

<span data-ttu-id="2beec-125">下列範例顯示如何定義設定區段, 並定義該區段的設定:</span><span class="sxs-lookup"><span data-stu-id="2beec-125">The following example shows how to define a configuration section and define settings for that section:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="2beec-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="2beec-126">Configuration file</span></span>

<span data-ttu-id="2beec-127">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="2beec-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="2beec-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2beec-128">See also</span></span>

- [<span data-ttu-id="2beec-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="2beec-129">Configuration file schema for the .NET Framework</span></span>](index.md)
