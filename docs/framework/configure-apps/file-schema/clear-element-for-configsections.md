---
title: <configSections> 的 <clear> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155423"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="cce17-102">\<configSections> 的 \<clear> 項目</span><span class="sxs-lookup"><span data-stu-id="cce17-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="cce17-103">清除所有先前定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="cce17-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="cce17-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="cce17-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cce17-105">語法</span><span class="sxs-lookup"><span data-stu-id="cce17-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="cce17-106">屬性</span><span class="sxs-lookup"><span data-stu-id="cce17-106">Attribute</span></span>

|           | <span data-ttu-id="cce17-107">描述</span><span class="sxs-lookup"><span data-stu-id="cce17-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cce17-108">**name**</span><span class="sxs-lookup"><span data-stu-id="cce17-108">**name**</span></span>  | <span data-ttu-id="cce17-109">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cce17-109">Required attribute.</span></span><br><br><span data-ttu-id="cce17-110">指定要移除之區段或區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="cce17-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="cce17-111">父元素</span><span class="sxs-lookup"><span data-stu-id="cce17-111">Parent element</span></span>

|     | <span data-ttu-id="cce17-112">描述</span><span class="sxs-lookup"><span data-stu-id="cce17-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cce17-113">**\<configSections>** 元素</span><span class="sxs-lookup"><span data-stu-id="cce17-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="cce17-114">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="cce17-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="cce17-115">子元素</span><span class="sxs-lookup"><span data-stu-id="cce17-115">Child elements</span></span>

<span data-ttu-id="cce17-116">None</span><span class="sxs-lookup"><span data-stu-id="cce17-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="cce17-117">備註</span><span class="sxs-lookup"><span data-stu-id="cce17-117">Remarks</span></span>

<span data-ttu-id="cce17-118">**\<clear>** 元素會從您的應用程式移除先前在目前設定檔或設定檔階層中較高層級定義的所有區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="cce17-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="cce17-119">範例</span><span class="sxs-lookup"><span data-stu-id="cce17-119">Example</span></span>

<span data-ttu-id="cce17-120">這個範例會定義電腦設定檔和應用程式佈建檔，並示範如何使用 **\<clear>** 應用程式佈建檔中的專案，清除電腦設定檔中先前定義的區段。</span><span class="sxs-lookup"><span data-stu-id="cce17-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="cce17-121">下列電腦設定檔程式碼會宣告兩個區段，分別 **\<sampleSection>** **\<anotherSampleSection>** 是在應用程式佈建檔之前讀取：</span><span class="sxs-lookup"><span data-stu-id="cce17-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="cce17-122">下列應用程式佈建檔程式碼會清除所有先前宣告的區段。</span><span class="sxs-lookup"><span data-stu-id="cce17-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="cce17-123">應用程式無法在電腦設定檔中宣告的任一區段中使用或抓取設定。</span><span class="sxs-lookup"><span data-stu-id="cce17-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="cce17-124">不過，它可以使用的設定， **\<anotherSection>** 因為它是在 **\<clear>** 元素之後。</span><span class="sxs-lookup"><span data-stu-id="cce17-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="cce17-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="cce17-125">Configuration file</span></span>

<span data-ttu-id="cce17-126">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="cce17-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cce17-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cce17-127">See also</span></span>

- [<span data-ttu-id="cce17-128">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="cce17-128">Configuration file schema for the .NET Framework</span></span>](index.md)
