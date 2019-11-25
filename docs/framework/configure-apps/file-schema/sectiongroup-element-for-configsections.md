---
title: <configSections> 的 <sectionGroup> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 746a997e162b0fd370a249b8d039be623b57d77f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089011"
---
# <a name="sectiongroup-element-for-configsections"></a><span data-ttu-id="9adcd-102">\<configSections 的 \<sectionGroup > 元素 ></span><span class="sxs-lookup"><span data-stu-id="9adcd-102">\<sectionGroup> element for \<configSections></span></span>

<span data-ttu-id="9adcd-103">定義設定區段的命名空間。</span><span class="sxs-lookup"><span data-stu-id="9adcd-103">Defines a namespace for configuration sections.</span></span>

<span data-ttu-id="9adcd-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9adcd-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="9adcd-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="9adcd-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="9adcd-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="9adcd-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="9adcd-107">語法</span><span class="sxs-lookup"><span data-stu-id="9adcd-107">Syntax</span></span>

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a><span data-ttu-id="9adcd-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9adcd-108">Attribute</span></span>

|           | <span data-ttu-id="9adcd-109">描述</span><span class="sxs-lookup"><span data-stu-id="9adcd-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="9adcd-110">**name**</span><span class="sxs-lookup"><span data-stu-id="9adcd-110">**name**</span></span>  | <span data-ttu-id="9adcd-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="9adcd-111">Required attribute.</span></span><br><br><span data-ttu-id="9adcd-112">指定您要定義之區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="9adcd-112">Specifies the name of the section group you are defining.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="9adcd-113">父項目</span><span class="sxs-lookup"><span data-stu-id="9adcd-113">Parent element</span></span>

|     | <span data-ttu-id="9adcd-114">描述</span><span class="sxs-lookup"><span data-stu-id="9adcd-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9adcd-115"> **\<configSections >** 元素</span><span class="sxs-lookup"><span data-stu-id="9adcd-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="9adcd-116">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="9adcd-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="9adcd-117">子元素</span><span class="sxs-lookup"><span data-stu-id="9adcd-117">Child elements</span></span>

|     | <span data-ttu-id="9adcd-118">描述</span><span class="sxs-lookup"><span data-stu-id="9adcd-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="9adcd-119"> **\<區段 >** </span><span class="sxs-lookup"><span data-stu-id="9adcd-119">**\<section>**</span></span>](section-element.md) | <span data-ttu-id="9adcd-120">包含設定區段宣告。</span><span class="sxs-lookup"><span data-stu-id="9adcd-120">Contains a configuration section declaration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="9adcd-121">備註</span><span class="sxs-lookup"><span data-stu-id="9adcd-121">Remarks</span></span>

<span data-ttu-id="9adcd-122">宣告區段群組會建立設定區段的容器標記，並確保與其他人所定義的設定區段沒有任何命名衝突。</span><span class="sxs-lookup"><span data-stu-id="9adcd-122">Declaring a section group creates a container tag for configuration sections and ensures that there are no naming conflicts with configuration sections defined by someone else.</span></span> <span data-ttu-id="9adcd-123">您可以將 **\<的 sectionGroup >** 元素放在彼此內。</span><span class="sxs-lookup"><span data-stu-id="9adcd-123">You can nest **\<sectionGroup>** elements within each other.</span></span>

## <a name="example"></a><span data-ttu-id="9adcd-124">範例</span><span class="sxs-lookup"><span data-stu-id="9adcd-124">Example</span></span>

<span data-ttu-id="9adcd-125">下列範例示範如何宣告區段群組，並在區段群組中宣告區段：</span><span class="sxs-lookup"><span data-stu-id="9adcd-125">The following example shows how to declare a section group and declare sections within a section group:</span></span>

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

## <a name="configuration-file"></a><span data-ttu-id="9adcd-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="9adcd-126">Configuration file</span></span>

<span data-ttu-id="9adcd-127">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="9adcd-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="9adcd-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="9adcd-128">See also</span></span>

- [<span data-ttu-id="9adcd-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="9adcd-129">Configuration file schema for the .NET Framework</span></span>](index.md)
