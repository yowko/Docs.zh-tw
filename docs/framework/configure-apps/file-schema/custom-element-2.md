---
title: NameValueSectionHandler 和 DictionarySectionHandler 的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215483"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="c25af-102">NameValueSectionHandler 和 DictionarySectionHandler 的自訂元素</span><span class="sxs-lookup"><span data-stu-id="c25af-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="c25af-103">定義使用和類別之自訂設定區段的設定 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="c25af-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;**\<sectionName>**

## <a name="attributes"></a><span data-ttu-id="c25af-104">屬性</span><span class="sxs-lookup"><span data-stu-id="c25af-104">Attributes</span></span>

<span data-ttu-id="c25af-105">無</span><span class="sxs-lookup"><span data-stu-id="c25af-105">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="c25af-106">父元素</span><span class="sxs-lookup"><span data-stu-id="c25af-106">Parent element</span></span>

|     | <span data-ttu-id="c25af-107">描述</span><span class="sxs-lookup"><span data-stu-id="c25af-107">Description</span></span> |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | <span data-ttu-id="c25af-108">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c25af-108">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c25af-109">子元素</span><span class="sxs-lookup"><span data-stu-id="c25af-109">Child elements</span></span>

|     | <span data-ttu-id="c25af-110">描述</span><span class="sxs-lookup"><span data-stu-id="c25af-110">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="c25af-111">[**\<add>**](add-element-for-custom-2.md)針對 <xref:System.Configuration.NameValueSectionHandler> 和<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="c25af-111">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="c25af-112">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="c25af-112">Adds custom application settings.</span></span> |
| <span data-ttu-id="c25af-113">[**\<remove>**](remove-element-for-custom-2.md)針對 <xref:System.Configuration.NameValueSectionHandler> 和<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="c25af-113">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="c25af-114">移除先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="c25af-114">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="c25af-115">[**\<clear>**](clear-element-for-custom-2.md)針對 <xref:System.Configuration.NameValueSectionHandler> 和<xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="c25af-115">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="c25af-116">清除區段中所有先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="c25af-116">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c25af-117">備註</span><span class="sxs-lookup"><span data-stu-id="c25af-117">Remarks</span></span>

<span data-ttu-id="c25af-118">**\<sectionName>** 元素是由專案中的標記所定義的自訂元素 **\<section>** **\<configSections>** 。</span><span class="sxs-lookup"><span data-stu-id="c25af-118">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="c25af-119">下表顯示每個設定區段處理常式的 ConfigurationSettings GetConfig 方法所傳回的物件類型：</span><span class="sxs-lookup"><span data-stu-id="c25af-119">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="c25af-120">設定區段處理常式</span><span class="sxs-lookup"><span data-stu-id="c25af-120">Configuration section handler</span></span>                        | <span data-ttu-id="c25af-121">傳回類型</span><span class="sxs-lookup"><span data-stu-id="c25af-121">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="c25af-122">範例</span><span class="sxs-lookup"><span data-stu-id="c25af-122">Example</span></span>

<span data-ttu-id="c25af-123">下列範例顯示如何宣告使用 <xref:System.Configuration.DictionarySectionHandler> 和類別的區段 <xref:System.Configuration.NameValueSectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="c25af-123">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="c25af-124">第一個自訂元素是 **\<dictionarySample>** ，其中包含元件中的類別所讀取的設定 <xref:System.Configuration.DictionarySectionHandler> `System.dll` 。</span><span class="sxs-lookup"><span data-stu-id="c25af-124">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="c25af-125">第二個自訂元素是 **\<mySection>** ，其中包含元件中的類別所讀取的設定 <xref:System.Configuration.NameValueSectionHandler> `System.dll` 。</span><span class="sxs-lookup"><span data-stu-id="c25af-125">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c25af-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="c25af-126">Configuration file</span></span>

<span data-ttu-id="c25af-127">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="c25af-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c25af-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c25af-128">See also</span></span>

- [<span data-ttu-id="c25af-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="c25af-129">Configuration file schema for the .NET Framework</span></span>](index.md)
