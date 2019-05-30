---
title: <appSettings> 的 <clear> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d4d96143dbd1db440de2247a7dc2f0c66f20403
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301291"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="976b7-102">\<清除 > 項目\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="976b7-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="976b7-103">清除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="976b7-103">Clears custom application settings.</span></span>

<span data-ttu-id="976b7-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="976b7-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="976b7-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="976b7-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="976b7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="976b7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="976b7-107">語法</span><span class="sxs-lookup"><span data-stu-id="976b7-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="976b7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="976b7-108">Attributes</span></span>

<span data-ttu-id="976b7-109">None</span><span class="sxs-lookup"><span data-stu-id="976b7-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="976b7-110">父項目</span><span class="sxs-lookup"><span data-stu-id="976b7-110">Parent element</span></span>

|     | <span data-ttu-id="976b7-111">描述</span><span class="sxs-lookup"><span data-stu-id="976b7-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="976b7-112"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="976b7-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="976b7-113">包含自訂應用程式設定，例如檔案路徑、 XML Web 服務 Url 或任何其他的自訂應用程式組態資訊。</span><span class="sxs-lookup"><span data-stu-id="976b7-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="976b7-114">子元素</span><span class="sxs-lookup"><span data-stu-id="976b7-114">Child elements</span></span>

<span data-ttu-id="976b7-115">None</span><span class="sxs-lookup"><span data-stu-id="976b7-115">None</span></span>

## <a name="example"></a><span data-ttu-id="976b7-116">範例</span><span class="sxs-lookup"><span data-stu-id="976b7-116">Example</span></span>

<span data-ttu-id="976b7-117">下列範例顯示如何清除自訂組態設定：</span><span class="sxs-lookup"><span data-stu-id="976b7-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="976b7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="976b7-118">See also</span></span>

- [<span data-ttu-id="976b7-119">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="976b7-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
