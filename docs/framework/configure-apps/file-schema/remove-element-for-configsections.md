---
title: <remove> 的 <configSections> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 99d67bd621390789993caa4862e5ce379135eb92
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215382"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="c1ed4-102">\<移除 \<configSections 的 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="c1ed4-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="c1ed4-103">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="c1ed4-104">[ **\<configuration>** ](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1ed4-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="c1ed4-105">&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="c1ed4-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="c1ed4-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<移除 >**</span><span class="sxs-lookup"><span data-stu-id="c1ed4-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c1ed4-107">語法</span><span class="sxs-lookup"><span data-stu-id="c1ed4-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="c1ed4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="c1ed4-108">Attribute</span></span>

|           | <span data-ttu-id="c1ed4-109">描述</span><span class="sxs-lookup"><span data-stu-id="c1ed4-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="c1ed4-110">**name**</span><span class="sxs-lookup"><span data-stu-id="c1ed4-110">**name**</span></span>  | <span data-ttu-id="c1ed4-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-111">Required attribute.</span></span><br><br><span data-ttu-id="c1ed4-112">指定要移除之區段或區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="c1ed4-113">父元素</span><span class="sxs-lookup"><span data-stu-id="c1ed4-113">Parent element</span></span>

|     | <span data-ttu-id="c1ed4-114">描述</span><span class="sxs-lookup"><span data-stu-id="c1ed4-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="c1ed4-115"> **\<configSections >** 元素</span><span class="sxs-lookup"><span data-stu-id="c1ed4-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="c1ed4-116">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="c1ed4-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c1ed4-117">Child elements</span></span>

<span data-ttu-id="c1ed4-118">無</span><span class="sxs-lookup"><span data-stu-id="c1ed4-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="c1ed4-119">備註</span><span class="sxs-lookup"><span data-stu-id="c1ed4-119">Remarks</span></span>

<span data-ttu-id="c1ed4-120">您可以使用 **\<移除 >** 元素，從您的應用程式移除在設定檔階層中較高層級定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="c1ed4-121">範例</span><span class="sxs-lookup"><span data-stu-id="c1ed4-121">Example</span></span>

<span data-ttu-id="c1ed4-122">下列範例示範如何使用應用程式佈建檔中的 **\<移除 >** 元素，以移除先前在電腦設定檔中定義的區段。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="c1ed4-123">下列電腦設定檔程式碼會宣告 **\<sampleSection >** 的區段：</span><span class="sxs-lookup"><span data-stu-id="c1ed4-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="c1ed4-124">下列應用程式佈建檔案代碼會移除 **\<sampleSection >** 區段。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="c1ed4-125">移除之後，應用程式就無法在 **\<sampleSection >** 中抓取設定。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="c1ed4-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="c1ed4-126">Configuration file</span></span>

<span data-ttu-id="c1ed4-127">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="c1ed4-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1ed4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1ed4-128">See also</span></span>

- [<span data-ttu-id="c1ed4-129">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="c1ed4-129">Configuration file schema for the .NET Framework</span></span>](index.md)
