---
title: NameValueSectionHandler 和 DictionarySectionHandler 的自訂元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921022"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="4019e-102">NameValueSectionHandler 和 DictionarySectionHandler 的自訂元素</span><span class="sxs-lookup"><span data-stu-id="4019e-102">Custom element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="4019e-103">定義使用<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別之自訂設定區段的設定。</span><span class="sxs-lookup"><span data-stu-id="4019e-103">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span>

<span data-ttu-id="4019e-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4019e-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="4019e-105">&nbsp;&nbsp; **\<sectionName>**</span><span class="sxs-lookup"><span data-stu-id="4019e-105">&nbsp;&nbsp;**\<sectionName>**</span></span>

## <a name="attributes"></a><span data-ttu-id="4019e-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4019e-106">Attributes</span></span>

<span data-ttu-id="4019e-107">無</span><span class="sxs-lookup"><span data-stu-id="4019e-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4019e-108">父項目</span><span class="sxs-lookup"><span data-stu-id="4019e-108">Parent element</span></span>

|     | <span data-ttu-id="4019e-109">描述</span><span class="sxs-lookup"><span data-stu-id="4019e-109">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4019e-110"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="4019e-110">**\<configuration>**</span></span>](configuration-element.md) | <span data-ttu-id="4019e-111">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="4019e-111">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4019e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4019e-112">Child elements</span></span>

|     | <span data-ttu-id="4019e-113">描述</span><span class="sxs-lookup"><span data-stu-id="4019e-113">Description</span></span> |
| --- | ----------- |
| <span data-ttu-id="4019e-114">新增和的 > [ **\<** ](add-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="4019e-114">[**\<add>**](add-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span>  | <span data-ttu-id="4019e-115">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="4019e-115">Adds custom application settings.</span></span> |
| <span data-ttu-id="4019e-116">移除和的 > [ **\<** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="4019e-116">[**\<remove>**](remove-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="4019e-117">移除先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="4019e-117">Removes a previously defined setting.</span></span> |
| <span data-ttu-id="4019e-118">清除和的 > [ **\<** ](clear-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler></span><span class="sxs-lookup"><span data-stu-id="4019e-118">[**\<clear>**](clear-element-for-custom-2.md) for <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler></span></span> | <span data-ttu-id="4019e-119">清除區段中所有先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="4019e-119">Clears all previously defined settings in a section.</span></span> |

## <a name="remarks"></a><span data-ttu-id="4019e-120">備註</span><span class="sxs-lookup"><span data-stu-id="4019e-120">Remarks</span></span>

<span data-ttu-id="4019e-121">**\<SectionName>** 項目是所定義的自訂項目 **\<區段>** 標記中 **\<configSections>** 項目。</span><span class="sxs-lookup"><span data-stu-id="4019e-121">The **\<sectionName>** element is a custom element defined by a **\<section>** tag in the **\<configSections>** element.</span></span>

<span data-ttu-id="4019e-122">下表顯示每個設定區段處理常式的 ConfigurationSettings GetConfig 方法所傳回的物件類型:</span><span class="sxs-lookup"><span data-stu-id="4019e-122">The following table shows the type of object the ConfigurationSettings.GetConfig method returns for each configuration section handler:</span></span>

| <span data-ttu-id="4019e-123">設定區段處理常式</span><span class="sxs-lookup"><span data-stu-id="4019e-123">Configuration section handler</span></span>                        | <span data-ttu-id="4019e-124">傳回類型</span><span class="sxs-lookup"><span data-stu-id="4019e-124">Return type</span></span>                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a><span data-ttu-id="4019e-125">範例</span><span class="sxs-lookup"><span data-stu-id="4019e-125">Example</span></span>

<span data-ttu-id="4019e-126">下列範例顯示如何宣告使用<xref:System.Configuration.DictionarySectionHandler>和<xref:System.Configuration.NameValueSectionHandler>類別的區段。</span><span class="sxs-lookup"><span data-stu-id="4019e-126">The following example shows how to declare sections that use the <xref:System.Configuration.DictionarySectionHandler> and <xref:System.Configuration.NameValueSectionHandler> classes.</span></span>

<span data-ttu-id="4019e-127">第一個自訂元素為 **\<dictionarySample >** , 其中包含`System.dll`元件中的<xref:System.Configuration.DictionarySectionHandler>類別所讀取的設定。</span><span class="sxs-lookup"><span data-stu-id="4019e-127">The first custom element is **\<dictionarySample>**, which contains settings read by the <xref:System.Configuration.DictionarySectionHandler> class in the `System.dll` assembly.</span></span> <span data-ttu-id="4019e-128">第二個自訂元素是 **\<mySection >** , 其中包含`System.dll`元件中<xref:System.Configuration.NameValueSectionHandler>的類別所讀取的設定。</span><span class="sxs-lookup"><span data-stu-id="4019e-128">The second custom element is **\<mySection>**, which contains settings read by the <xref:System.Configuration.NameValueSectionHandler> class in the `System.dll` assembly.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="4019e-129">組態檔</span><span class="sxs-lookup"><span data-stu-id="4019e-129">Configuration file</span></span>

<span data-ttu-id="4019e-130">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4019e-130">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4019e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4019e-131">See also</span></span>

- [<span data-ttu-id="4019e-132">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="4019e-132">Configuration file schema for the .NET Framework</span></span>](index.md)
