---
title: <appSettings> 的 <add> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865c693bf8f23bf050064ac097b72aa6fa3b371e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088751"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="d79ff-102">\<新增 \<appSettings 的 > 元素 ></span><span class="sxs-lookup"><span data-stu-id="d79ff-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="d79ff-103">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="d79ff-103">Adds a custom application setting.</span></span>

<span data-ttu-id="d79ff-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d79ff-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d79ff-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="d79ff-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="d79ff-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="d79ff-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d79ff-107">語法</span><span class="sxs-lookup"><span data-stu-id="d79ff-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="d79ff-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d79ff-108">Attributes</span></span>

|           | <span data-ttu-id="d79ff-109">描述</span><span class="sxs-lookup"><span data-stu-id="d79ff-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d79ff-110">**key**</span><span class="sxs-lookup"><span data-stu-id="d79ff-110">**key**</span></span>   | <span data-ttu-id="d79ff-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d79ff-111">Required attribute.</span></span><br><br><span data-ttu-id="d79ff-112">指定要加入之索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="d79ff-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="d79ff-113">**值**</span><span class="sxs-lookup"><span data-stu-id="d79ff-113">**value**</span></span> | <span data-ttu-id="d79ff-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d79ff-114">Required attribute.</span></span><br><br><span data-ttu-id="d79ff-115">指定要加入之索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="d79ff-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d79ff-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d79ff-116">Parent element</span></span>

|     | <span data-ttu-id="d79ff-117">描述</span><span class="sxs-lookup"><span data-stu-id="d79ff-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d79ff-118"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="d79ff-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="d79ff-119">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="d79ff-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d79ff-120">子元素</span><span class="sxs-lookup"><span data-stu-id="d79ff-120">Child elements</span></span>

<span data-ttu-id="d79ff-121">None</span><span class="sxs-lookup"><span data-stu-id="d79ff-121">None</span></span>

## <a name="example"></a><span data-ttu-id="d79ff-122">範例</span><span class="sxs-lookup"><span data-stu-id="d79ff-122">Example</span></span>

<span data-ttu-id="d79ff-123">下列範例顯示如何新增應用程式名稱的自訂設定：</span><span class="sxs-lookup"><span data-stu-id="d79ff-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="d79ff-124">下列範例會使用 `<add>` 元素，在 ASP.NET 應用程式中定義兩個相容性設定：</span><span class="sxs-lookup"><span data-stu-id="d79ff-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="d79ff-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="d79ff-125">See also</span></span>

- [<span data-ttu-id="d79ff-126">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="d79ff-126">Configuration file schema for the .NET Framework</span></span>](../index.md)
