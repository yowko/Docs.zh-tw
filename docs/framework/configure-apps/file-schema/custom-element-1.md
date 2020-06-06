---
title: SingleTagSectionHandler 的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635392"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="791d9-102">SingleTagSectionHandler 的自訂元素</span><span class="sxs-lookup"><span data-stu-id="791d9-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="791d9-103">定義自訂設定區段中，由 \<section> 元素定義並使用類別的設定 <xref:System.Configuration.SingleTagSectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="791d9-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="791d9-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span><span class="sxs-lookup"><span data-stu-id="791d9-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="791d9-105">語法</span><span class="sxs-lookup"><span data-stu-id="791d9-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="791d9-106">屬性</span><span class="sxs-lookup"><span data-stu-id="791d9-106">Attributes</span></span>

<span data-ttu-id="791d9-107">屬性和屬性值是使用者定義的。</span><span class="sxs-lookup"><span data-stu-id="791d9-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="791d9-108">父元素</span><span class="sxs-lookup"><span data-stu-id="791d9-108">Parent element</span></span>

|     | <span data-ttu-id="791d9-109">描述</span><span class="sxs-lookup"><span data-stu-id="791d9-109">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="791d9-110">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="791d9-110">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="791d9-111">子元素</span><span class="sxs-lookup"><span data-stu-id="791d9-111">Child elements</span></span>

<span data-ttu-id="791d9-112">None</span><span class="sxs-lookup"><span data-stu-id="791d9-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="791d9-113">備註</span><span class="sxs-lookup"><span data-stu-id="791d9-113">Remarks</span></span>

<span data-ttu-id="791d9-114">**\<sectionName>** 元素是由專案中的標記所定義的自訂元素 [**\<section>**](section-element.md) [**\<configSections>**](configsections-element-for-configuration.md) 。</span><span class="sxs-lookup"><span data-stu-id="791d9-114">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="791d9-115"><xref:System.Collections.IDictionary>當您呼叫時，設定系統會傳回物件 <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="791d9-115">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="791d9-116">範例</span><span class="sxs-lookup"><span data-stu-id="791d9-116">Example</span></span>

<span data-ttu-id="791d9-117">下列範例會宣告名為的自訂元素 **\<sampleSection>** ，其中包含類別所讀取的設定 <xref:System.Configuration.SingleTagSectionHandler> ：</span><span class="sxs-lookup"><span data-stu-id="791d9-117">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="791d9-118">組態檔</span><span class="sxs-lookup"><span data-stu-id="791d9-118">Configuration file</span></span>

<span data-ttu-id="791d9-119">此專案可用於應用程式佈建檔 *、電腦設定檔（machine.config*），以及不在應用程式目錄層級的*web.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="791d9-119">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="791d9-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="791d9-120">See also</span></span>

- [<span data-ttu-id="791d9-121">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="791d9-121">Configuration file schema for the .NET Framework</span></span>](index.md)
