---
title: <appSettings> 的 <clear> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214786"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="420ff-102">\<appSettings> 的 \<clear> 項目</span><span class="sxs-lookup"><span data-stu-id="420ff-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="420ff-103">清除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="420ff-103">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="420ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="420ff-104">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="420ff-105">屬性</span><span class="sxs-lookup"><span data-stu-id="420ff-105">Attributes</span></span>

<span data-ttu-id="420ff-106">無</span><span class="sxs-lookup"><span data-stu-id="420ff-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="420ff-107">父元素</span><span class="sxs-lookup"><span data-stu-id="420ff-107">Parent element</span></span>

|     | <span data-ttu-id="420ff-108">描述</span><span class="sxs-lookup"><span data-stu-id="420ff-108">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="420ff-109">包含自訂應用程式設定，例如檔案路徑、XML Web Service Url，或任何其他自訂應用程式設定資訊。</span><span class="sxs-lookup"><span data-stu-id="420ff-109">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="420ff-110">子元素</span><span class="sxs-lookup"><span data-stu-id="420ff-110">Child elements</span></span>

<span data-ttu-id="420ff-111">None</span><span class="sxs-lookup"><span data-stu-id="420ff-111">None</span></span>

## <a name="example"></a><span data-ttu-id="420ff-112">範例</span><span class="sxs-lookup"><span data-stu-id="420ff-112">Example</span></span>

<span data-ttu-id="420ff-113">下列範例顯示如何清除自訂設定：</span><span class="sxs-lookup"><span data-stu-id="420ff-113">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="420ff-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="420ff-114">See also</span></span>

- [<span data-ttu-id="420ff-115">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="420ff-115">Configuration file schema for the .NET Framework</span></span>](../index.md)
