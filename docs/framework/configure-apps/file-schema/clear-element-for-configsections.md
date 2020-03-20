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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155423"
---
# <a name="clear-element-for-configsections"></a><span data-ttu-id="d33c0-102">\<用於\<配置>的透明>元素</span><span class="sxs-lookup"><span data-stu-id="d33c0-102">\<clear> element for \<configSections></span></span>

<span data-ttu-id="d33c0-103">清除以前定義的所有節和節組。</span><span class="sxs-lookup"><span data-stu-id="d33c0-103">Clears all previously defined sections and section groups.</span></span>

<span data-ttu-id="d33c0-104">&nbsp; [\*\* \<配置>\*\*](configuration-element.md)&nbsp;&nbsp;**配置>\<清晰的>** [\*\* \< \*\*](configsections-element-for-configuration.md) &nbsp; &nbsp; &nbsp;</span><span class="sxs-lookup"><span data-stu-id="d33c0-104">[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d33c0-105">語法</span><span class="sxs-lookup"><span data-stu-id="d33c0-105">Syntax</span></span>

```xml
<clear/>
```

## <a name="attribute"></a><span data-ttu-id="d33c0-106">屬性</span><span class="sxs-lookup"><span data-stu-id="d33c0-106">Attribute</span></span>

|           | <span data-ttu-id="d33c0-107">描述</span><span class="sxs-lookup"><span data-stu-id="d33c0-107">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d33c0-108">**名稱**</span><span class="sxs-lookup"><span data-stu-id="d33c0-108">**name**</span></span>  | <span data-ttu-id="d33c0-109">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d33c0-109">Required attribute.</span></span><br><br><span data-ttu-id="d33c0-110">指定要刪除的節或節組的名稱。</span><span class="sxs-lookup"><span data-stu-id="d33c0-110">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d33c0-111">父元素</span><span class="sxs-lookup"><span data-stu-id="d33c0-111">Parent element</span></span>

|     | <span data-ttu-id="d33c0-112">描述</span><span class="sxs-lookup"><span data-stu-id="d33c0-112">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d33c0-113">\*\* \<配置部分>\*\* 元素</span><span class="sxs-lookup"><span data-stu-id="d33c0-113">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="d33c0-114">包含配置部分和命名空間聲明。</span><span class="sxs-lookup"><span data-stu-id="d33c0-114">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d33c0-115">子元素</span><span class="sxs-lookup"><span data-stu-id="d33c0-115">Child elements</span></span>

<span data-ttu-id="d33c0-116">None</span><span class="sxs-lookup"><span data-stu-id="d33c0-116">None</span></span>

## <a name="remarks"></a><span data-ttu-id="d33c0-117">備註</span><span class="sxs-lookup"><span data-stu-id="d33c0-117">Remarks</span></span>

<span data-ttu-id="d33c0-118">\*\* \<清除>\*\* 元素從應用程式中刪除當前設定檔前面或設定檔層次結構中較高級別定義的所有節和節組。</span><span class="sxs-lookup"><span data-stu-id="d33c0-118">The **\<clear>** element removes all sections and section groups from your application that were defined earlier in the current configuration file or at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="d33c0-119">範例</span><span class="sxs-lookup"><span data-stu-id="d33c0-119">Example</span></span>

<span data-ttu-id="d33c0-120">本示例定義電腦設定檔和應用程式佈建檔，並演示如何在應用程式佈建檔中使用**\<清除>** 元素來清除以前在電腦設定檔中定義的部分。</span><span class="sxs-lookup"><span data-stu-id="d33c0-120">This example defines a machine configuration file and an application configuration file and shows how to use the **\<clear>** element in an application configuration file to clear sections previously defined in the machine configuration file.</span></span>

<span data-ttu-id="d33c0-121">以下電腦設定檔代碼聲明兩個部分，**\<示例節>\*\*\*\*\<和另一個Sample節>**，在應用程式佈建檔之前讀取：</span><span class="sxs-lookup"><span data-stu-id="d33c0-121">The following machine configuration file code declares two sections, **\<sampleSection>** and **\<anotherSampleSection>**, which are read before the application configuration file:</span></span>

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

<span data-ttu-id="d33c0-122">以下應用程式佈建檔代碼清除以前聲明的所有部分。</span><span class="sxs-lookup"><span data-stu-id="d33c0-122">The following application configuration file code clears all previously declared sections.</span></span> <span data-ttu-id="d33c0-123">應用程式無法使用或檢索在電腦設定檔中聲明的任一部分中的設置。</span><span class="sxs-lookup"><span data-stu-id="d33c0-123">The application cannot use or retrieve settings in either of the sections that were declared in the machine configuration file.</span></span> <span data-ttu-id="d33c0-124">但是，它可以使用**\<另一節>** 設置，因為它在**\<明確>** 元素之後出現。</span><span class="sxs-lookup"><span data-stu-id="d33c0-124">However, it can use settings from **\<anotherSection>** because it comes after the **\<clear>** element.</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="d33c0-125">組態檔</span><span class="sxs-lookup"><span data-stu-id="d33c0-125">Configuration file</span></span>

<span data-ttu-id="d33c0-126">此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。</span><span class="sxs-lookup"><span data-stu-id="d33c0-126">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="d33c0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d33c0-127">See also</span></span>

- [<span data-ttu-id="d33c0-128">.NET 框架的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="d33c0-128">Configuration file schema for the .NET Framework</span></span>](index.md)
