---
title: 單一標籤節處理常式的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 0d765a9789ad566428b1fbda6c0863b10b98c363
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345069"
---
# <a name="custom-element-for-singletagsectionhandler"></a><span data-ttu-id="5e615-102">單一標籤節處理常式的自訂元素</span><span class="sxs-lookup"><span data-stu-id="5e615-102">Custom element for SingleTagSectionHandler</span></span>

<span data-ttu-id="5e615-103">在由\<節>元素定義的自訂配置部分中定義設置，並使用類<xref:System.Configuration.SingleTagSectionHandler>。</span><span class="sxs-lookup"><span data-stu-id="5e615-103">Defines settings in a custom configuration section that is defined by a \<section> element and uses the <xref:System.Configuration.SingleTagSectionHandler> class.</span></span>

<span data-ttu-id="5e615-104">&nbsp; [\*\* \<配置>\*\*](configuration-element.md)&nbsp;*節名稱>\<*</span><span class="sxs-lookup"><span data-stu-id="5e615-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*</span></span>

## <a name="syntax"></a><span data-ttu-id="5e615-105">語法</span><span class="sxs-lookup"><span data-stu-id="5e615-105">Syntax</span></span>

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a><span data-ttu-id="5e615-106">屬性</span><span class="sxs-lookup"><span data-stu-id="5e615-106">Attributes</span></span>

<span data-ttu-id="5e615-107">屬性和屬性值是使用者定義的。</span><span class="sxs-lookup"><span data-stu-id="5e615-107">Attributes and attribute values are user defined.</span></span>

## <a name="parent-element"></a><span data-ttu-id="5e615-108">父元素</span><span class="sxs-lookup"><span data-stu-id="5e615-108">Parent element</span></span>

|     | <span data-ttu-id="5e615-109">描述</span><span class="sxs-lookup"><span data-stu-id="5e615-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="5e615-110">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="5e615-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="5e615-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5e615-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="5e615-112">子元素</span><span class="sxs-lookup"><span data-stu-id="5e615-112">Child elements</span></span>

<span data-ttu-id="5e615-113">None</span><span class="sxs-lookup"><span data-stu-id="5e615-113">None</span></span>

## <a name="remarks"></a><span data-ttu-id="5e615-114">備註</span><span class="sxs-lookup"><span data-stu-id="5e615-114">Remarks</span></span>

<span data-ttu-id="5e615-115">\*\* \<節名稱>\*\* 元素是由[**\<配置節>**](configsections-element-for-configuration.md)元素中[**\<>**](section-element.md)標記定義的自訂元素。</span><span class="sxs-lookup"><span data-stu-id="5e615-115">The **\<sectionName>** element is a custom element defined by a [**\<section>**](section-element.md) tag in the [**\<configSections>**](configsections-element-for-configuration.md) element.</span></span> <span data-ttu-id="5e615-116">當您調用<xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>時，<xref:System.Collections.IDictionary>配置系統將返回一個物件。</span><span class="sxs-lookup"><span data-stu-id="5e615-116">The configuration system returns a <xref:System.Collections.IDictionary> object when you call <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.</span></span>

## <a name="example"></a><span data-ttu-id="5e615-117">範例</span><span class="sxs-lookup"><span data-stu-id="5e615-117">Example</span></span>

<span data-ttu-id="5e615-118">以下示例聲明一個稱為**\<示例節>** 的自訂元素，其中包含類讀取的<xref:System.Configuration.SingleTagSectionHandler>設置：</span><span class="sxs-lookup"><span data-stu-id="5e615-118">The following example declares a custom element called **\<sampleSection>** that contains settings read by the <xref:System.Configuration.SingleTagSectionHandler> class:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="5e615-119">組態檔</span><span class="sxs-lookup"><span data-stu-id="5e615-119">Configuration file</span></span>

<span data-ttu-id="5e615-120">此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。</span><span class="sxs-lookup"><span data-stu-id="5e615-120">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e615-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e615-121">See also</span></span>

- [<span data-ttu-id="5e615-122">.NET 框架的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="5e615-122">Configuration file schema for the .NET Framework</span></span>](index.md)
