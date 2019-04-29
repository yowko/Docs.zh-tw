---
title: <appSettings> 的 <clear> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 0b6a48d1fdab3cbccf40aaa77731a658f533eeba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705398"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="3cb01-102">\<清除 > 項目\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="3cb01-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="3cb01-103">清除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="3cb01-103">Clears custom application settings.</span></span>

<span data-ttu-id="3cb01-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3cb01-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="3cb01-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="3cb01-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="3cb01-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span><span class="sxs-lookup"><span data-stu-id="3cb01-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3cb01-107">語法</span><span class="sxs-lookup"><span data-stu-id="3cb01-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="3cb01-108">屬性</span><span class="sxs-lookup"><span data-stu-id="3cb01-108">Attributes</span></span>

<span data-ttu-id="3cb01-109">None</span><span class="sxs-lookup"><span data-stu-id="3cb01-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="3cb01-110">父項目</span><span class="sxs-lookup"><span data-stu-id="3cb01-110">Parent element</span></span>

|     | <span data-ttu-id="3cb01-111">描述</span><span class="sxs-lookup"><span data-stu-id="3cb01-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="3cb01-112">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="3cb01-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="3cb01-113">包含自訂應用程式設定，例如檔案路徑、 XML Web 服務 Url 或任何其他的自訂應用程式組態資訊。</span><span class="sxs-lookup"><span data-stu-id="3cb01-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3cb01-114">子元素</span><span class="sxs-lookup"><span data-stu-id="3cb01-114">Child elements</span></span>

<span data-ttu-id="3cb01-115">None</span><span class="sxs-lookup"><span data-stu-id="3cb01-115">None</span></span>

## <a name="example"></a><span data-ttu-id="3cb01-116">範例</span><span class="sxs-lookup"><span data-stu-id="3cb01-116">Example</span></span>

<span data-ttu-id="3cb01-117">下列範例顯示如何清除自訂組態設定：</span><span class="sxs-lookup"><span data-stu-id="3cb01-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="3cb01-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cb01-118">See also</span></span>

- [<span data-ttu-id="3cb01-119">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3cb01-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
