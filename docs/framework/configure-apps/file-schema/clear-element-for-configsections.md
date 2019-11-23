---
title: <clear> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a45572d0dcb2737558e11f5c38ac2ccc338c754a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119089"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="17a86-102">\<清除 \<configSections 的 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="17a86-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="17a86-103">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="17a86-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="17a86-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="17a86-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="17a86-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="17a86-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="17a86-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="17a86-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="17a86-107">語法</span><span class="sxs-lookup"><span data-stu-id="17a86-107">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="17a86-108">屬性</span><span class="sxs-lookup"><span data-stu-id="17a86-108">Attribute</span></span>

|           | <span data-ttu-id="17a86-109">描述</span><span class="sxs-lookup"><span data-stu-id="17a86-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="17a86-110">**name**</span><span class="sxs-lookup"><span data-stu-id="17a86-110">**name**</span></span>  | <span data-ttu-id="17a86-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="17a86-111">Required attribute.</span></span><br><br><span data-ttu-id="17a86-112">指定要移除之區段或區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="17a86-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="17a86-113">父項目</span><span class="sxs-lookup"><span data-stu-id="17a86-113">Parent element</span></span>

|     | <span data-ttu-id="17a86-114">描述</span><span class="sxs-lookup"><span data-stu-id="17a86-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="17a86-115"> **\<configSections >** 元素</span><span class="sxs-lookup"><span data-stu-id="17a86-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="17a86-116">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="17a86-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="17a86-117">子元素</span><span class="sxs-lookup"><span data-stu-id="17a86-117">Child elements</span></span>

<span data-ttu-id="17a86-118">無</span><span class="sxs-lookup"><span data-stu-id="17a86-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="17a86-119">備註</span><span class="sxs-lookup"><span data-stu-id="17a86-119">Remarks</span></span>

<span data-ttu-id="17a86-120">**\<清除>** 項目會從您先前已定義在目前的組態檔中或在組態檔階層架構中較高層級的應用程式移除所有區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="17a86-120">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="17a86-121">範例</span><span class="sxs-lookup"><span data-stu-id="17a86-121">Example</span></span>

<span data-ttu-id="17a86-122">這個範例會定義電腦設定檔和應用程式佈建檔，並示範如何使用應用程式佈建檔中的 **\<clear >** 元素，清除電腦設定檔中先前定義的區段。</span><span class="sxs-lookup"><span data-stu-id="17a86-122">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="17a86-123">下列電腦設定檔程式碼會宣告兩個區段， **\<sampleSection >** 和 **\<anotherSampleSection >** ，在應用程式佈建檔之前讀取：</span><span class="sxs-lookup"><span data-stu-id="17a86-123">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

<span data-ttu-id="17a86-124">下列應用程式佈建檔程式碼會清除所有先前宣告的區段。</span><span class="sxs-lookup"><span data-stu-id="17a86-124">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="17a86-125">應用程式無法在電腦設定檔中宣告的任一區段中使用或抓取設定。</span><span class="sxs-lookup"><span data-stu-id="17a86-125">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="17a86-126">不過，它可以使用來自 **\<anotherSection >** 的設定，因為它是在 **\<clear >** 元素之後。</span><span class="sxs-lookup"><span data-stu-id="17a86-126">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="17a86-127">組態檔</span><span class="sxs-lookup"><span data-stu-id="17a86-127">Configuration file</span></span>

<span data-ttu-id="17a86-128">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="17a86-128">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="17a86-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17a86-129">See also</span></span>

- [<span data-ttu-id="17a86-130">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="17a86-130">Configuration file schema for the .NET Framework</span></span>](index.md)
