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
ms.openlocfilehash: 5d5da531bff3a0e9e198ba9b5ab6cf2b52bf36b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921306"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="960e8-102">\<清除 appSettings 的\<> 元素 ></span><span class="sxs-lookup"><span data-stu-id="960e8-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="960e8-103">清除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="960e8-103">Clears custom application settings.</span></span>

<span data-ttu-id="960e8-104">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="960e8-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="960e8-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="960e8-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="960e8-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="960e8-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="960e8-107">語法</span><span class="sxs-lookup"><span data-stu-id="960e8-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="960e8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="960e8-108">Attributes</span></span>

<span data-ttu-id="960e8-109">無</span><span class="sxs-lookup"><span data-stu-id="960e8-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="960e8-110">父項目</span><span class="sxs-lookup"><span data-stu-id="960e8-110">Parent element</span></span>

|     | <span data-ttu-id="960e8-111">描述</span><span class="sxs-lookup"><span data-stu-id="960e8-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="960e8-112"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="960e8-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="960e8-113">包含自訂應用程式設定, 例如檔案路徑、XML Web Service Url, 或任何其他自訂應用程式設定資訊。</span><span class="sxs-lookup"><span data-stu-id="960e8-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="960e8-114">子元素</span><span class="sxs-lookup"><span data-stu-id="960e8-114">Child elements</span></span>

<span data-ttu-id="960e8-115">無</span><span class="sxs-lookup"><span data-stu-id="960e8-115">None</span></span>

## <a name="example"></a><span data-ttu-id="960e8-116">範例</span><span class="sxs-lookup"><span data-stu-id="960e8-116">Example</span></span>

<span data-ttu-id="960e8-117">下列範例顯示如何清除自訂設定:</span><span class="sxs-lookup"><span data-stu-id="960e8-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="960e8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="960e8-118">See also</span></span>

- [<span data-ttu-id="960e8-119">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="960e8-119">Configuration file schema for the .NET Framework</span></span>](../index.md)
