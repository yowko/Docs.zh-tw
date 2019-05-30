---
title: <configSections> 的 <sectionGroup> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 750708483f9680745eef4531d86fa7ecaa329f51
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301186"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="7a651-102">\<sectionGroup > 項目\<configSections ></span><span class="sxs-lookup"><span data-stu-id="7a651-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="7a651-103">定義組態區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="7a651-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="7a651-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7a651-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="7a651-105">&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="7a651-105">&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="7a651-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="7a651-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7a651-107">語法</span><span class="sxs-lookup"><span data-stu-id="7a651-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="7a651-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7a651-108">Attribute</span></span>

|           | <span data-ttu-id="7a651-109">描述</span><span class="sxs-lookup"><span data-stu-id="7a651-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="7a651-110">**name**</span><span class="sxs-lookup"><span data-stu-id="7a651-110">**name**</span></span>  | <span data-ttu-id="7a651-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="7a651-111">Required attribute.</span></span><br><br><span data-ttu-id="7a651-112">指定您要定義之區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a651-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="7a651-113">父項目</span><span class="sxs-lookup"><span data-stu-id="7a651-113">Parent element</span></span>

|     | <span data-ttu-id="7a651-114">描述</span><span class="sxs-lookup"><span data-stu-id="7a651-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7a651-115"> *\*\<configSections >** 項目</span><span class="sxs-lookup"><span data-stu-id="7a651-115">**\<configSections>** Element</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="7a651-116">包含組態區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="7a651-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7a651-117">子元素</span><span class="sxs-lookup"><span data-stu-id="7a651-117">Child elements</span></span>

|     | <span data-ttu-id="7a651-118">描述</span><span class="sxs-lookup"><span data-stu-id="7a651-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7a651-119"> *\*\<section>** </span><span class="sxs-lookup"><span data-stu-id="7a651-119">**\<section>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="7a651-120">包含組態區段宣告。</span><span class="sxs-lookup"><span data-stu-id="7a651-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="7a651-121">備註</span><span class="sxs-lookup"><span data-stu-id="7a651-121">Remarks</span></span>

<span data-ttu-id="7a651-122">宣告區段群組時，會建立容器標記的組態區段，並確保沒有與其他人所定義的組態區段的命名衝突。</span><span class="sxs-lookup"><span data-stu-id="7a651-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="7a651-123">您可以巢狀 **\<sectionGroup >** 彼此的項目。</span><span class="sxs-lookup"><span data-stu-id="7a651-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="7a651-124">範例</span><span class="sxs-lookup"><span data-stu-id="7a651-124">Example</span></span>

<span data-ttu-id="7a651-125">下列範例示範如何宣告區段群組和區段群組內宣告區段：</span><span class="sxs-lookup"><span data-stu-id="7a651-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="7a651-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="7a651-126">Configuration file</span></span>

<span data-ttu-id="7a651-127">這個項目可用的應用程式組態檔中，電腦組態檔 (*Machine.config*)，以及*Web.config*不在應用程式的目錄層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="7a651-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a651-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a651-128">See also</span></span>

- [<span data-ttu-id="7a651-129">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="7a651-129">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
