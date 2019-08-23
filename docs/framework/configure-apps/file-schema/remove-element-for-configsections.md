---
title: <configSections> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 4ff9bb537a31e28dbd4b878c1bc04c96262f85ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927463"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="55d73-102">\<移除 configSections > 的\<> 元素</span><span class="sxs-lookup"><span data-stu-id="55d73-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="55d73-103">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="55d73-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="55d73-104">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="55d73-104">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="55d73-105">&nbsp;&nbsp;[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="55d73-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="55d73-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**</span><span class="sxs-lookup"><span data-stu-id="55d73-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="55d73-107">語法</span><span class="sxs-lookup"><span data-stu-id="55d73-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="55d73-108">屬性</span><span class="sxs-lookup"><span data-stu-id="55d73-108">Attribute</span></span>

|           | <span data-ttu-id="55d73-109">說明</span><span class="sxs-lookup"><span data-stu-id="55d73-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="55d73-110">**name**</span><span class="sxs-lookup"><span data-stu-id="55d73-110">**name**</span></span>  | <span data-ttu-id="55d73-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="55d73-111">Required attribute.</span></span><br><br><span data-ttu-id="55d73-112">指定要移除之區段或區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="55d73-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="55d73-113">父項目</span><span class="sxs-lookup"><span data-stu-id="55d73-113">Parent element</span></span>

|     | <span data-ttu-id="55d73-114">描述</span><span class="sxs-lookup"><span data-stu-id="55d73-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="55d73-115"> **configSections>\<** 元素</span><span class="sxs-lookup"><span data-stu-id="55d73-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="55d73-116">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="55d73-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="55d73-117">子元素</span><span class="sxs-lookup"><span data-stu-id="55d73-117">Child elements</span></span>

<span data-ttu-id="55d73-118">None</span><span class="sxs-lookup"><span data-stu-id="55d73-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="55d73-119">備註</span><span class="sxs-lookup"><span data-stu-id="55d73-119">Remarks</span></span>

<span data-ttu-id="55d73-120">您可以使用 **\<移除>** 區段和區段群組中移除您的應用程式組態檔階層架構中較高層級所定義的項目。</span><span class="sxs-lookup"><span data-stu-id="55d73-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="55d73-121">範例</span><span class="sxs-lookup"><span data-stu-id="55d73-121">Example</span></span>

<span data-ttu-id="55d73-122">下列範例示範如何使用 **\<移除>** 應用程式組態檔，以移除先前在電腦組態檔中定義的區段中的項目。</span><span class="sxs-lookup"><span data-stu-id="55d73-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="55d73-123">下列電腦設定檔程式碼會宣告 **\<sampleSection >** 區段:</span><span class="sxs-lookup"><span data-stu-id="55d73-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="55d73-124">下列應用程式佈建檔程式碼會移除 **\<sampleSection >** 區段。</span><span class="sxs-lookup"><span data-stu-id="55d73-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="55d73-125">移除之後, 應用程式就無法抓取 **\<sampleSection >** 中的設定。</span><span class="sxs-lookup"><span data-stu-id="55d73-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="55d73-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="55d73-126">Configuration file</span></span>

<span data-ttu-id="55d73-127">此元素可用於應用程式佈建檔案、電腦設定檔案 (machine.config), 以及不在應用程式目錄層級的 web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="55d73-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="55d73-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55d73-128">See also</span></span>

- [<span data-ttu-id="55d73-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="55d73-129">Configuration file schema for the .NET Framework</span></span>](index.md)
