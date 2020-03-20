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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154526"
---
# <a name="remove-element-for-configsections"></a><span data-ttu-id="69a05-102">\<刪除>元素以\<進行配置></span><span class="sxs-lookup"><span data-stu-id="69a05-102">\<remove> element for \<configSections></span></span>

<span data-ttu-id="69a05-103">刪除預定義的節或節組。</span><span class="sxs-lookup"><span data-stu-id="69a05-103">Removes a predefined section or section group.</span></span>

<span data-ttu-id="69a05-104">[**\<配置>**](configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="69a05-104">[**\<configuration>**](configuration-element.md)</span></span>\
<span data-ttu-id="69a05-105">&nbsp;&nbsp;[**\<配置部分>**](configsections-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="69a05-105">&nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md)</span></span>\
<span data-ttu-id="69a05-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<刪除>**</span><span class="sxs-lookup"><span data-stu-id="69a05-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="69a05-107">語法</span><span class="sxs-lookup"><span data-stu-id="69a05-107">Syntax</span></span>

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a><span data-ttu-id="69a05-108">屬性</span><span class="sxs-lookup"><span data-stu-id="69a05-108">Attribute</span></span>

|           | <span data-ttu-id="69a05-109">描述</span><span class="sxs-lookup"><span data-stu-id="69a05-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="69a05-110">**名稱**</span><span class="sxs-lookup"><span data-stu-id="69a05-110">**name**</span></span>  | <span data-ttu-id="69a05-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="69a05-111">Required attribute.</span></span><br><br><span data-ttu-id="69a05-112">指定要刪除的節或節組的名稱。</span><span class="sxs-lookup"><span data-stu-id="69a05-112">Specifies the name of the section or section group to remove.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="69a05-113">父元素</span><span class="sxs-lookup"><span data-stu-id="69a05-113">Parent element</span></span>

|     | <span data-ttu-id="69a05-114">描述</span><span class="sxs-lookup"><span data-stu-id="69a05-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="69a05-115">\*\* \<配置部分>\*\* 元素</span><span class="sxs-lookup"><span data-stu-id="69a05-115">**\<configSections>** Element</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="69a05-116">包含配置部分和命名空間聲明。</span><span class="sxs-lookup"><span data-stu-id="69a05-116">Contains configuration section and namespace declarations.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="69a05-117">子元素</span><span class="sxs-lookup"><span data-stu-id="69a05-117">Child elements</span></span>

<span data-ttu-id="69a05-118">None</span><span class="sxs-lookup"><span data-stu-id="69a05-118">None</span></span>

## <a name="remarks"></a><span data-ttu-id="69a05-119">備註</span><span class="sxs-lookup"><span data-stu-id="69a05-119">Remarks</span></span>

<span data-ttu-id="69a05-120">可以使用**\<刪除>** 元素從應用程式中從設定檔層次結構中較高級別定義的節和節組中刪除。</span><span class="sxs-lookup"><span data-stu-id="69a05-120">You can use the **\<remove>** element to remove sections and section groups from your application that were defined at a higher level in the configuration file hierarchy.</span></span>

## <a name="example"></a><span data-ttu-id="69a05-121">範例</span><span class="sxs-lookup"><span data-stu-id="69a05-121">Example</span></span>

<span data-ttu-id="69a05-122">下面的示例演示如何使用應用程式佈建檔中的**\<刪除>** 元素來刪除以前在電腦設定檔中定義的部分。</span><span class="sxs-lookup"><span data-stu-id="69a05-122">The following example shows how to use the **\<remove>** element in an application configuration file to remove a section previously defined in the machine configuration file.</span></span>

<span data-ttu-id="69a05-123">以下電腦設定檔代碼聲明節**\<示例節>**：</span><span class="sxs-lookup"><span data-stu-id="69a05-123">The following machine configuration file code declares the section **\<sampleSection>**:</span></span>

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

<span data-ttu-id="69a05-124">以下應用程式佈建檔代碼將刪除**\<示例節>** 部分。</span><span class="sxs-lookup"><span data-stu-id="69a05-124">The following application configuration file code removes the **\<sampleSection>** section.</span></span> <span data-ttu-id="69a05-125">刪除後，應用程式無法檢索**\<示例節>** 中的設置。</span><span class="sxs-lookup"><span data-stu-id="69a05-125">After removal, the application cannot retrieve the settings in **\<sampleSection>**.</span></span>

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a><span data-ttu-id="69a05-126">組態檔</span><span class="sxs-lookup"><span data-stu-id="69a05-126">Configuration file</span></span>

<span data-ttu-id="69a05-127">此元素可用於應用程式佈建檔、電腦設定檔 *（Machine.config*） 和*Web.config*檔，這些檔不在應用程式目錄級別。</span><span class="sxs-lookup"><span data-stu-id="69a05-127">This element can be used in the application configuration file, machine configuration file (*Machine.config*), and *Web.config* files that are not at the application directory level.</span></span>

## <a name="see-also"></a><span data-ttu-id="69a05-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69a05-128">See also</span></span>

- [<span data-ttu-id="69a05-129">.NET 框架的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="69a05-129">Configuration file schema for the .NET Framework</span></span>](index.md)
