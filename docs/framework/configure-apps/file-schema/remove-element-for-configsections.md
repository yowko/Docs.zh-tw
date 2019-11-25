---
title: <configSections> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: efc7208aa51cbf6abdb2fe151d48071c0aa95b5c
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089043"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="64cb3-102">\<移除 \<configSections 的 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="64cb3-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="64cb3-103">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="64cb3-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="64cb3-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="64cb3-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="64cb3-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="64cb3-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="64cb3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="64cb3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="64cb3-107">語法</span><span class="sxs-lookup"><span data-stu-id="64cb3-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="64cb3-108">屬性</span><span class="sxs-lookup"><span data-stu-id="64cb3-108">Attribute</span></span>

|           | <span data-ttu-id="64cb3-109">描述</span><span class="sxs-lookup"><span data-stu-id="64cb3-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="64cb3-110">**name**</span><span class="sxs-lookup"><span data-stu-id="64cb3-110">**name**</span></span>  | <span data-ttu-id="64cb3-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="64cb3-111">Required attribute.</span></span><br><br><span data-ttu-id="64cb3-112">指定要移除之區段或區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="64cb3-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="64cb3-113">父項目</span><span class="sxs-lookup"><span data-stu-id="64cb3-113">Parent element</span></span>

|     | <span data-ttu-id="64cb3-114">描述</span><span class="sxs-lookup"><span data-stu-id="64cb3-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="64cb3-115"> **\<configSections >** 元素</span><span class="sxs-lookup"><span data-stu-id="64cb3-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="64cb3-116">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="64cb3-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="64cb3-117">子元素</span><span class="sxs-lookup"><span data-stu-id="64cb3-117">Child elements</span></span>

<span data-ttu-id="64cb3-118">None</span><span class="sxs-lookup"><span data-stu-id="64cb3-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="64cb3-119">備註</span><span class="sxs-lookup"><span data-stu-id="64cb3-119">Remarks</span></span>

<span data-ttu-id="64cb3-120">您可以使用 **\<移除 >** 元素，從您的應用程式移除在設定檔階層中較高層級定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="64cb3-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="64cb3-121">範例</span><span class="sxs-lookup"><span data-stu-id="64cb3-121">Example</span></span>

<span data-ttu-id="64cb3-122">下列範例示範如何使用應用程式佈建檔中的 **\<移除 >** 元素，以移除先前在電腦設定檔中定義的區段。</span><span class="sxs-lookup"><span data-stu-id="64cb3-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="64cb3-123">下列電腦設定檔程式碼會宣告 **\<sampleSection >** 的區段：</span><span class="sxs-lookup"><span data-stu-id="64cb3-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

```xml
<!-- Machine.config file -->
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

<span data-ttu-id="64cb3-124">下列應用程式佈建檔案代碼會移除 **\<sampleSection >** 區段。</span><span class="sxs-lookup"><span data-stu-id="64cb3-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="64cb3-125">移除之後，應用程式就無法在 **\<sampleSection >** 中抓取設定。</span><span class="sxs-lookup"><span data-stu-id="64cb3-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="64cb3-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="64cb3-126">Configuration file</span></span>

<span data-ttu-id="64cb3-127">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="64cb3-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="64cb3-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="64cb3-128">See also</span></span>

- [<span data-ttu-id="64cb3-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="64cb3-129">Configuration file schema for the .NET Framework</span></span>](index.md)
