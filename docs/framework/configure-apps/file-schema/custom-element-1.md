---
title: 單一分頁處理程式的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635392"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="e6afd-102">單一分頁處理程式的自訂元素</span><span class="sxs-lookup"><span data-stu-id="e6afd-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="e6afd-103">在由\<節>元素定義的自訂設定部分中定義設定,並使用類<xref:System.Configuration.SingleTagSectionHandler>。</span><span class="sxs-lookup"><span data-stu-id="e6afd-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="e6afd-104">&nbsp;&nbsp;節名稱>[\*\* \<\*\*](configuration-element.md)\* \<\*</span><span class="sxs-lookup"><span data-stu-id="e6afd-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="e6afd-105">語法</span><span class="sxs-lookup"><span data-stu-id="e6afd-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="e6afd-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e6afd-106">Attributes</span></span>

<span data-ttu-id="e6afd-107">屬性和屬性值是使用者定義的。</span><span class="sxs-lookup"><span data-stu-id="e6afd-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="e6afd-108">父元素</span><span class="sxs-lookup"><span data-stu-id="e6afd-108">Parent element</span></span>

|     | <span data-ttu-id="e6afd-109">描述</span><span class="sxs-lookup"><span data-stu-id="e6afd-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e6afd-110">**\<設定>**</span><span class="sxs-lookup"><span data-stu-id="e6afd-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="e6afd-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="e6afd-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e6afd-112">子元素</span><span class="sxs-lookup"><span data-stu-id="e6afd-112">Child elements</span></span>

<span data-ttu-id="e6afd-113">None</span><span class="sxs-lookup"><span data-stu-id="e6afd-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="e6afd-114">備註</span><span class="sxs-lookup"><span data-stu-id="e6afd-114">Remarks</span></span>

<span data-ttu-id="e6afd-115">節名稱>元素是由[**\<配置節>**](configsections-element-for-configuration.md)元素中[**\<>**](section-element.md)標記定義的自定義元素。 \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="e6afd-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="e6afd-116">當您呼叫<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>時<xref:System.Collections.IDictionary>, 配置系統將傳回一個物件。</span><span class="sxs-lookup"><span data-stu-id="e6afd-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="e6afd-117">範例</span><span class="sxs-lookup"><span data-stu-id="e6afd-117">Example</span></span>

<span data-ttu-id="e6afd-118">以下範例聲明一個稱為**\<範例節>** 的自定義元素,其中包含類讀<xref:System.Configuration.SingleTagSectionHandler>取的 設定:</span><span class="sxs-lookup"><span data-stu-id="e6afd-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="e6afd-119">組態檔</span><span class="sxs-lookup"><span data-stu-id="e6afd-119">Configuration file</span></span>

<span data-ttu-id="e6afd-120">此元素可用於應用程式設定檔、計算機設定檔 *(Machine.config)* 和*Web.config*檔,這些檔案不在應用程式目錄等級。</span><span class="sxs-lookup"><span data-stu-id="e6afd-120">This element can be used in the application configuration file, the machine configuration file (*Machine.config*), and *Web.config* files that aren't at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6afd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6afd-121">See also</span></span>

- [<span data-ttu-id="e6afd-122">.NET 架構的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="e6afd-122">Configuration file schema for the .NET Framework</span></span>](index.md)
