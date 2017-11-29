---
title: "&lt;新增&gt;元素&lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2b00af6f7d735d5db8fd746205ba225253cad133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="750ef-102">\<新增 > 項目\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="750ef-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="750ef-103">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="750ef-103">Adds a custom application setting.</span></span>

<span data-ttu-id="750ef-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="750ef-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="750ef-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="750ef-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="750ef-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="750ef-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="750ef-107">語法</span><span class="sxs-lookup"><span data-stu-id="750ef-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="750ef-108">屬性</span><span class="sxs-lookup"><span data-stu-id="750ef-108">Attributes</span></span>

|           | <span data-ttu-id="750ef-109">說明</span><span class="sxs-lookup"><span data-stu-id="750ef-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="750ef-110">**key**</span><span class="sxs-lookup"><span data-stu-id="750ef-110">**key**</span></span>   | <span data-ttu-id="750ef-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="750ef-111">Required attribute.</span></span><br><br><span data-ttu-id="750ef-112">指定要新增之索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="750ef-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="750ef-113">**value**</span><span class="sxs-lookup"><span data-stu-id="750ef-113">**value**</span></span> | <span data-ttu-id="750ef-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="750ef-114">Required attribute.</span></span><br><br><span data-ttu-id="750ef-115">指定要新增之索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="750ef-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="750ef-116">父項目</span><span class="sxs-lookup"><span data-stu-id="750ef-116">Parent element</span></span>

|     | <span data-ttu-id="750ef-117">說明</span><span class="sxs-lookup"><span data-stu-id="750ef-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="750ef-118">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="750ef-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="750ef-119">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="750ef-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="750ef-120">子元素</span><span class="sxs-lookup"><span data-stu-id="750ef-120">Child elements</span></span>

<span data-ttu-id="750ef-121">無</span><span class="sxs-lookup"><span data-stu-id="750ef-121">None</span></span>

## <a name="example"></a><span data-ttu-id="750ef-122">範例</span><span class="sxs-lookup"><span data-stu-id="750ef-122">Example</span></span>

<span data-ttu-id="750ef-123">下列範例會示範如何新增自訂組態設定的應用程式的名稱：</span><span class="sxs-lookup"><span data-stu-id="750ef-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="750ef-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="750ef-124">See also</span></span>

[<span data-ttu-id="750ef-125">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="750ef-125">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
