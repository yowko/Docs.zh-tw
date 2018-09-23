---
title: '&lt;新增&gt;項目&lt;appSettings&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
ms.openlocfilehash: bcdac76528e7a8b07b56b6fd1d827c3c8072c371
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46706365"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="d9172-102">\<新增 > 項目\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="d9172-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="d9172-103">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="d9172-103">Adds a custom application setting.</span></span>

<span data-ttu-id="d9172-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d9172-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="d9172-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d9172-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="d9172-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="d9172-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="d9172-107">語法</span><span class="sxs-lookup"><span data-stu-id="d9172-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="d9172-108">屬性</span><span class="sxs-lookup"><span data-stu-id="d9172-108">Attributes</span></span>

|           | <span data-ttu-id="d9172-109">描述</span><span class="sxs-lookup"><span data-stu-id="d9172-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="d9172-110">**key**</span><span class="sxs-lookup"><span data-stu-id="d9172-110">**key**</span></span>   | <span data-ttu-id="d9172-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d9172-111">Required attribute.</span></span><br><br><span data-ttu-id="d9172-112">指定要新增之索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="d9172-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="d9172-113">**value**</span><span class="sxs-lookup"><span data-stu-id="d9172-113">**value**</span></span> | <span data-ttu-id="d9172-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="d9172-114">Required attribute.</span></span><br><br><span data-ttu-id="d9172-115">指定要新增之索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="d9172-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="d9172-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d9172-116">Parent element</span></span>

|     | <span data-ttu-id="d9172-117">描述</span><span class="sxs-lookup"><span data-stu-id="d9172-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d9172-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="d9172-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="d9172-119">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="d9172-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="d9172-120">子元素</span><span class="sxs-lookup"><span data-stu-id="d9172-120">Child elements</span></span>

<span data-ttu-id="d9172-121">無</span><span class="sxs-lookup"><span data-stu-id="d9172-121">None</span></span>

## <a name="example"></a><span data-ttu-id="d9172-122">範例</span><span class="sxs-lookup"><span data-stu-id="d9172-122">Example</span></span>

<span data-ttu-id="d9172-123">下列範例示範如何新增自訂組態設定的應用程式的名稱：</span><span class="sxs-lookup"><span data-stu-id="d9172-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="d9172-124">下列範例會使用`<add>`項目來定義 ASP.NET 應用程式中的兩個的相容性設定：</span><span class="sxs-lookup"><span data-stu-id="d9172-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="d9172-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9172-125">See also</span></span>

[<span data-ttu-id="d9172-126">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="d9172-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
