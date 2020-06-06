---
title: <clear>NameValueSectionHandler 和 DictionarySectionHandler 的元素
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214748"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="4fec1-102">\<clear>NameValueSectionHandler 和 DictionarySectionHandler 的元素</span><span class="sxs-lookup"><span data-stu-id="4fec1-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="4fec1-103">清除區段中所有先前定義的設定。</span><span class="sxs-lookup"><span data-stu-id="4fec1-103">Clears all previously defined settings in a section.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<sectionName>**](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="4fec1-104">語法</span><span class="sxs-lookup"><span data-stu-id="4fec1-104">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="4fec1-105">屬性</span><span class="sxs-lookup"><span data-stu-id="4fec1-105">Attributes</span></span>

<span data-ttu-id="4fec1-106">無</span><span class="sxs-lookup"><span data-stu-id="4fec1-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="4fec1-107">父元素</span><span class="sxs-lookup"><span data-stu-id="4fec1-107">Parent element</span></span>

|     | <span data-ttu-id="4fec1-108">描述</span><span class="sxs-lookup"><span data-stu-id="4fec1-108">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="4fec1-109">**\<sectionName>** 元素</span><span class="sxs-lookup"><span data-stu-id="4fec1-109">**\<sectionName>** Element</span></span>](custom-element-2.md) | <span data-ttu-id="4fec1-110">定義使用和類別之自訂設定區段的設定 <xref:System.Configuration.NameValueSectionHandler> <xref:System.Configuration.DictionarySectionHandler> 。</span><span class="sxs-lookup"><span data-stu-id="4fec1-110">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4fec1-111">子元素</span><span class="sxs-lookup"><span data-stu-id="4fec1-111">Child elements</span></span>

<span data-ttu-id="4fec1-112">None</span><span class="sxs-lookup"><span data-stu-id="4fec1-112">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4fec1-113">備註</span><span class="sxs-lookup"><span data-stu-id="4fec1-113">Remarks</span></span>

<span data-ttu-id="4fec1-114">您可以使用 **\<clear>** 元素，從您的應用程式中移除在設定檔階層中較高層級定義的所有設定。</span><span class="sxs-lookup"><span data-stu-id="4fec1-114">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="4fec1-115">範例</span><span class="sxs-lookup"><span data-stu-id="4fec1-115">Example</span></span>

<span data-ttu-id="4fec1-116">這個範例會定義電腦設定檔和應用程式佈建檔，並示範如何使用 **\<clear>** 應用程式佈建檔中的專案，清除電腦設定檔中先前定義的區段。</span><span class="sxs-lookup"><span data-stu-id="4fec1-116">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="4fec1-117">下列電腦設定檔程式碼會宣告區段 **\<mySection>** ：</span><span class="sxs-lookup"><span data-stu-id="4fec1-117">The following machine configuration file code declares the section **\<mySection>**:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

<span data-ttu-id="4fec1-118">下列應用程式佈建檔案代碼會從移除所有設定 **\<mySection>** 。</span><span class="sxs-lookup"><span data-stu-id="4fec1-118">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="4fec1-119">應用程式無法在電腦設定檔的區段中，取得在中宣告的任何設定 **\<mySection>** 。</span><span class="sxs-lookup"><span data-stu-id="4fec1-119">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="4fec1-120">組態檔</span><span class="sxs-lookup"><span data-stu-id="4fec1-120">Configuration file</span></span>

<span data-ttu-id="4fec1-121">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="4fec1-121">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4fec1-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4fec1-122">See also</span></span>

- [<span data-ttu-id="4fec1-123">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="4fec1-123">Configuration file schema for the .NET Framework</span></span>](index.md)
