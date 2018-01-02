---
title: "&lt;清除&gt;元素&lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54479cab9abc2c1a107cd055341404c0fe1308fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="91483-102">\<清除 > 項目\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="91483-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="91483-103">清除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="91483-103">Clears custom application settings.</span></span>

<span data-ttu-id="91483-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="91483-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="91483-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="91483-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="91483-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<清除 >**</span><span class="sxs-lookup"><span data-stu-id="91483-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="91483-107">語法</span><span class="sxs-lookup"><span data-stu-id="91483-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="91483-108">屬性</span><span class="sxs-lookup"><span data-stu-id="91483-108">Attributes</span></span>

<span data-ttu-id="91483-109">無</span><span class="sxs-lookup"><span data-stu-id="91483-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="91483-110">父項目</span><span class="sxs-lookup"><span data-stu-id="91483-110">Parent element</span></span>

|     | <span data-ttu-id="91483-111">描述</span><span class="sxs-lookup"><span data-stu-id="91483-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="91483-112">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="91483-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="91483-113">包含自訂應用程式設定，例如檔案路徑、 XML Web 服務 Url 或任何其他的自訂應用程式組態資訊。</span><span class="sxs-lookup"><span data-stu-id="91483-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="91483-114">子元素</span><span class="sxs-lookup"><span data-stu-id="91483-114">Child elements</span></span>

<span data-ttu-id="91483-115">無</span><span class="sxs-lookup"><span data-stu-id="91483-115">None</span></span>

## <a name="example"></a><span data-ttu-id="91483-116">範例</span><span class="sxs-lookup"><span data-stu-id="91483-116">Example</span></span>

<span data-ttu-id="91483-117">下列範例顯示如何清除自訂組態設定：</span><span class="sxs-lookup"><span data-stu-id="91483-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="91483-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91483-118">See also</span></span>

[<span data-ttu-id="91483-119">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="91483-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
