---
title: '&lt;移除&gt;元素&lt;c&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 6555981edeb6f7f088fb12c710d0146cf58d5be1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="cb148-102">\<移除 > 項目\<c ></span><span class="sxs-lookup"><span data-stu-id="cb148-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="cb148-103">預先定義的區段或區段群組中移除。</span><span class="sxs-lookup"><span data-stu-id="cb148-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="cb148-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="cb148-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="cb148-105">&nbsp;&nbsp;[**\<c >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="cb148-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="cb148-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="cb148-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="cb148-107">語法</span><span class="sxs-lookup"><span data-stu-id="cb148-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="cb148-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cb148-108">Attribute</span></span>

|           | <span data-ttu-id="cb148-109">描述</span><span class="sxs-lookup"><span data-stu-id="cb148-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="cb148-110">**name**</span><span class="sxs-lookup"><span data-stu-id="cb148-110">**name**</span></span>  | <span data-ttu-id="cb148-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="cb148-111">Required attribute.</span></span><br><br><span data-ttu-id="cb148-112">指定區段或要移除的區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="cb148-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="cb148-113">父項目</span><span class="sxs-lookup"><span data-stu-id="cb148-113">Parent element</span></span>

|     | <span data-ttu-id="cb148-114">描述</span><span class="sxs-lookup"><span data-stu-id="cb148-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="cb148-115">**\<c >** 項目</span><span class="sxs-lookup"><span data-stu-id="cb148-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="cb148-116">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="cb148-116">Contains configuration section and namespace declarations.</span></span> |

# <a name="child-elements"></a><span data-ttu-id="cb148-117">子元素</span><span class="sxs-lookup"><span data-stu-id="cb148-117">Child elements</span></span>

<span data-ttu-id="cb148-118">無</span><span class="sxs-lookup"><span data-stu-id="cb148-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="cb148-119">備註</span><span class="sxs-lookup"><span data-stu-id="cb148-119">Remarks</span></span>

<span data-ttu-id="cb148-120">您可以使用**\<移除 >** 項目區段或區段群組中移除您已在組態檔階層架構中較高層級定義的應用程式。</span><span class="sxs-lookup"><span data-stu-id="cb148-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="cb148-121">範例</span><span class="sxs-lookup"><span data-stu-id="cb148-121">Example</span></span>

<span data-ttu-id="cb148-122">下列範例示範如何使用**\<移除 >** 應用程式組態檔移除電腦組態檔中預先定義的區段中的項目。</span><span class="sxs-lookup"><span data-stu-id="cb148-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="cb148-123">下列的機器組態檔案程式碼會宣告區段 **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="cb148-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="cb148-124">下列應用程式組態檔程式碼會移除 **\<sampleSection >** > 一節。</span><span class="sxs-lookup"><span data-stu-id="cb148-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="cb148-125">移除後，應用程式無法擷取中的設定 **\<sampleSection >**。</span><span class="sxs-lookup"><span data-stu-id="cb148-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="cb148-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="cb148-126">Configuration file</span></span>

<span data-ttu-id="cb148-127">此項目可以用於應用程式組態檔中，電腦組態檔 (*Machine.config*)，和*Web.config*不在應用程式目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="cb148-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb148-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb148-128">See also</span></span>

[<span data-ttu-id="cb148-129">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="cb148-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
