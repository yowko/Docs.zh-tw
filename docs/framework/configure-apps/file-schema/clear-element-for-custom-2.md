---
title: "&lt;清除&gt;NameValueSectionHandler DictionarySectionHandler 的項目"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57ee634c987d344d81f1ca099fe55e633bfbf659
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a><span data-ttu-id="fa95b-102">\<清除 > NameValueSectionHandler DictionarySectionHandler 的項目</span><span class="sxs-lookup"><span data-stu-id="fa95b-102">\<clear> element for NameValueSectionHandler and DictionarySectionHandler</span></span>

<span data-ttu-id="fa95b-103">清除所有先前定義的設定區段中。</span><span class="sxs-lookup"><span data-stu-id="fa95b-103">Clears all previously defined settings in a section.</span></span>

<span data-ttu-id="fa95b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="fa95b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="fa95b-105">&nbsp;&nbsp;[**\<sectionName >**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span><span class="sxs-lookup"><span data-stu-id="fa95b-105">&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md) </span></span>  
<span data-ttu-id="fa95b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<清除 >**</span><span class="sxs-lookup"><span data-stu-id="fa95b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="fa95b-107">語法</span><span class="sxs-lookup"><span data-stu-id="fa95b-107">Syntax</span></span>

```xml
<clear />
```

## <a name="attributes"></a><span data-ttu-id="fa95b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fa95b-108">Attributes</span></span>

<span data-ttu-id="fa95b-109">無</span><span class="sxs-lookup"><span data-stu-id="fa95b-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="fa95b-110">父項目</span><span class="sxs-lookup"><span data-stu-id="fa95b-110">Parent element</span></span>

|     | <span data-ttu-id="fa95b-111">描述</span><span class="sxs-lookup"><span data-stu-id="fa95b-111">Description</span></span> |
| --- | ------------|
| [<span data-ttu-id="fa95b-112">**\<sectionName >**項目</span><span class="sxs-lookup"><span data-stu-id="fa95b-112">**\<sectionName>** Element</span></span>](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | <span data-ttu-id="fa95b-113">定義自訂組態區段，使用設定<xref:System.Configuration.NameValueSectionHandler>和<xref:System.Configuration.DictionarySectionHandler>類別。</span><span class="sxs-lookup"><span data-stu-id="fa95b-113">Defines settings for custom configuration sections that use the <xref:System.Configuration.NameValueSectionHandler> and <xref:System.Configuration.DictionarySectionHandler> classes.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="fa95b-114">子元素</span><span class="sxs-lookup"><span data-stu-id="fa95b-114">Child elements</span></span>

<span data-ttu-id="fa95b-115">無</span><span class="sxs-lookup"><span data-stu-id="fa95b-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="fa95b-116">備註</span><span class="sxs-lookup"><span data-stu-id="fa95b-116">Remarks</span></span>

<span data-ttu-id="fa95b-117">您可以使用**\<清除 >**項目移除您已在組態檔階層架構中較高層級定義的應用程式中的所有設定。</span><span class="sxs-lookup"><span data-stu-id="fa95b-117">You can use the **\<clear>** element to remove all settings from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="fa95b-118">範例</span><span class="sxs-lookup"><span data-stu-id="fa95b-118">Example</span></span>

<span data-ttu-id="fa95b-119">此範例中定義的機器組態檔案和應用程式組態檔，並示範如何使用**\<清除 >**應用程式組態檔中清除先前定義的區段中的項目電腦組態檔。</span><span class="sxs-lookup"><span data-stu-id="fa95b-119">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="fa95b-120">下列的機器組態檔案程式碼會宣告區段 **\<mySection >**:</span><span class="sxs-lookup"><span data-stu-id="fa95b-120">The following machine configuration file code declares the section **\<mySection>**:</span></span>

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

<span data-ttu-id="fa95b-121">下列應用程式組態檔程式碼中移除的所有設定 **\<mySection >**。</span><span class="sxs-lookup"><span data-stu-id="fa95b-121">The following application configuration file code removes all settings from **\<mySection>**.</span></span> <span data-ttu-id="fa95b-122">應用程式無法擷取的任何設定中所宣告的中 **\<mySection >**機器組態檔區段。</span><span class="sxs-lookup"><span data-stu-id="fa95b-122">The application cannot retrieve any of the settings that were declared in the in the **\<mySection>** section of the machine configuration file.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="fa95b-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="fa95b-123">Configuration file</span></span>

<span data-ttu-id="fa95b-124">此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="fa95b-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa95b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa95b-125">See also</span></span>

[<span data-ttu-id="fa95b-126">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="fa95b-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
