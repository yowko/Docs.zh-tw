---
title: <configSections> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154526"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="30803-102">\<configSections> 的 \<remove> 項目</span><span class="sxs-lookup"><span data-stu-id="30803-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="30803-103">移除預先定義的區段或區段群組。</span><span class="sxs-lookup"><span data-stu-id="30803-103">Removes a predefined section or section group.</span></span>

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="30803-104">語法</span><span class="sxs-lookup"><span data-stu-id="30803-104">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="30803-105">屬性</span><span class="sxs-lookup"><span data-stu-id="30803-105">Attribute</span></span>

|           | <span data-ttu-id="30803-106">描述</span><span class="sxs-lookup"><span data-stu-id="30803-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="30803-107">**name**</span><span class="sxs-lookup"><span data-stu-id="30803-107">**name**</span></span>  | <span data-ttu-id="30803-108">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="30803-108">Required attribute.</span></span><br><br><span data-ttu-id="30803-109">指定要移除之區段或區段群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="30803-109">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="30803-110">父元素</span><span class="sxs-lookup"><span data-stu-id="30803-110">Parent element</span></span>

|     | <span data-ttu-id="30803-111">描述</span><span class="sxs-lookup"><span data-stu-id="30803-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="30803-112">**\<configSections>** 元素</span><span class="sxs-lookup"><span data-stu-id="30803-112">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="30803-113">包含設定區段和命名空間宣告。</span><span class="sxs-lookup"><span data-stu-id="30803-113">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="30803-114">子元素</span><span class="sxs-lookup"><span data-stu-id="30803-114">Child elements</span></span>

<span data-ttu-id="30803-115">None</span><span class="sxs-lookup"><span data-stu-id="30803-115">None</span></span>

## <a name="remarks"></a><span data-ttu-id="30803-116">備註</span><span class="sxs-lookup"><span data-stu-id="30803-116">Remarks</span></span>

<span data-ttu-id="30803-117">您可以使用 **\<remove>** 元素，從您的應用程式移除在設定檔階層中較高層級定義的區段和區段群組。</span><span class="sxs-lookup"><span data-stu-id="30803-117">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="30803-118">範例</span><span class="sxs-lookup"><span data-stu-id="30803-118">Example</span></span>

<span data-ttu-id="30803-119">下列範例顯示如何使用 **\<remove>** 應用程式佈建檔中的專案，來移除先前在電腦設定檔中定義的區段。</span><span class="sxs-lookup"><span data-stu-id="30803-119">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="30803-120">下列電腦設定檔程式碼會宣告區段 **\<sampleSection>** ：</span><span class="sxs-lookup"><span data-stu-id="30803-120">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="30803-121">下列應用程式佈建檔案代碼會移除 **\<sampleSection>** 區段。</span><span class="sxs-lookup"><span data-stu-id="30803-121">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="30803-122">移除之後，應用程式就無法抓取中的設定 **\<sampleSection>** 。</span><span class="sxs-lookup"><span data-stu-id="30803-122">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="30803-123">組態檔</span><span class="sxs-lookup"><span data-stu-id="30803-123">Configuration file</span></span>

<span data-ttu-id="30803-124">此元素可用於應用程式佈建檔案 *、電腦設定檔案（machine.config*），以及不在應用程式目錄層級*的 web.config 檔案*。</span><span class="sxs-lookup"><span data-stu-id="30803-124">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="30803-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30803-125">See also</span></span>

- [<span data-ttu-id="30803-126">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="30803-126">Configuration file schema for the .NET Framework</span></span>](index.md)
