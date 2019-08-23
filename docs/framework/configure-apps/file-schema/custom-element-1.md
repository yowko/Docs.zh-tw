---
title: SingleTagSectionHandler 的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927493"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="5e457-102">SingleTagSectionHandler 的自訂元素</span><span class="sxs-lookup"><span data-stu-id="5e457-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="5e457-103">定義自訂設定區段中, 由\<區段 > 元素所定義, 並<xref:System.Configuration.SingleTagSectionHandler>使用類別的設定。</span><span class="sxs-lookup"><span data-stu-id="5e457-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="5e457-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5e457-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="5e457-105">&nbsp;&nbsp; *\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="5e457-105">&nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="5e457-106">語法</span><span class="sxs-lookup"><span data-stu-id="5e457-106">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a><span data-ttu-id="5e457-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5e457-107">Attributes</span></span>

<span data-ttu-id="5e457-108">屬性和屬性值是使用者定義的。</span><span class="sxs-lookup"><span data-stu-id="5e457-108">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="5e457-109">父項目</span><span class="sxs-lookup"><span data-stu-id="5e457-109">Parent element</span></span>

|     | <span data-ttu-id="5e457-110">說明</span><span class="sxs-lookup"><span data-stu-id="5e457-110">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5e457-111"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="5e457-111">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="5e457-112">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5e457-112">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5e457-113">子元素</span><span class="sxs-lookup"><span data-stu-id="5e457-113">Child elements</span></span>

<span data-ttu-id="5e457-114">無</span><span class="sxs-lookup"><span data-stu-id="5e457-114">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5e457-115">備註</span><span class="sxs-lookup"><span data-stu-id="5e457-115">Remarks</span></span>

<span data-ttu-id="5e457-116">**\<SectionName>** 項目是所定義的自訂項目 [ **\<section>** ](section-element.md) 標記 [ **\<configSections>** ](configsections-element-for-configuration.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="5e457-116">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="5e457-117">當您呼叫<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>時, <xref:System.Collections.IDictionary>設定系統會傳回物件。</span><span class="sxs-lookup"><span data-stu-id="5e457-117">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="5e457-118">範例</span><span class="sxs-lookup"><span data-stu-id="5e457-118">Example</span></span>

<span data-ttu-id="5e457-119">下列範例會宣告名<xref:System.Configuration.SingleTagSectionHandler>  **\<為 sampleSection >** 的自訂元素, 其中包含類別所讀取的設定:</span><span class="sxs-lookup"><span data-stu-id="5e457-119">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="5e457-120">組態檔</span><span class="sxs-lookup"><span data-stu-id="5e457-120">Configuration file</span></span>

<span data-ttu-id="5e457-121">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="5e457-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e457-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e457-122">See also</span></span>

- [<span data-ttu-id="5e457-123">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="5e457-123">Configuration file schema for the .NET Framework</span></span>](index.md)
