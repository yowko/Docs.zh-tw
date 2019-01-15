---
title: '&lt;移除&gt;項目&lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 11a930120c375616d73faae68a6d6807c2f633cb
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307223"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="4cbfd-102">\<移除 > 項目\<configSections ></span><span class="sxs-lookup"><span data-stu-id="4cbfd-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="4cbfd-103">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="4cbfd-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="4cbfd-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="4cbfd-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="4cbfd-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="4cbfd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="4cbfd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4cbfd-107">語法</span><span class="sxs-lookup"><span data-stu-id="4cbfd-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="4cbfd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4cbfd-108">Attribute</span></span>

|           | <span data-ttu-id="4cbfd-109">描述</span><span class="sxs-lookup"><span data-stu-id="4cbfd-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="4cbfd-110">**name**</span><span class="sxs-lookup"><span data-stu-id="4cbfd-110">**name**</span></span>  | <span data-ttu-id="4cbfd-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-111">Required attribute.</span></span><br><br><span data-ttu-id="4cbfd-112">指定要移除的區段群組之區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="4cbfd-113">父項目</span><span class="sxs-lookup"><span data-stu-id="4cbfd-113">Parent element</span></span>

|     | <span data-ttu-id="4cbfd-114">描述</span><span class="sxs-lookup"><span data-stu-id="4cbfd-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4cbfd-115">**\<configSections >** 項目</span><span class="sxs-lookup"><span data-stu-id="4cbfd-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="4cbfd-116">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4cbfd-117">子元素</span><span class="sxs-lookup"><span data-stu-id="4cbfd-117">Child elements</span></span>

<span data-ttu-id="4cbfd-118">無</span><span class="sxs-lookup"><span data-stu-id="4cbfd-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="4cbfd-119">備註</span><span class="sxs-lookup"><span data-stu-id="4cbfd-119">Remarks</span></span>

<span data-ttu-id="4cbfd-120">您可以使用**\<移除 >** 區段和區段群組中移除您的應用程式組態檔階層架構中較高層級所定義的項目。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="4cbfd-121">範例</span><span class="sxs-lookup"><span data-stu-id="4cbfd-121">Example</span></span>

<span data-ttu-id="4cbfd-122">下列範例示範如何使用**\<移除 >** 應用程式組態檔，以移除先前在電腦組態檔中定義的區段中的項目。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="4cbfd-123">下列的機器組態檔案程式碼會宣告一節 **\<sampleSection >**:</span><span class="sxs-lookup"><span data-stu-id="4cbfd-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="4cbfd-124">下列應用程式組態檔程式碼中移除 **\<sampleSection >** 一節。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="4cbfd-125">移除後，應用程式無法擷取中的設定 **\<sampleSection >**。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="4cbfd-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="4cbfd-126">Configuration file</span></span>

<span data-ttu-id="4cbfd-127">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="4cbfd-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cbfd-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cbfd-128">See also</span></span>

[<span data-ttu-id="4cbfd-129">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="4cbfd-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
