---
title: <appSettings> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215480"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="3fadb-102">\<appSettings> 的 \<remove> 項目</span><span class="sxs-lookup"><span data-stu-id="3fadb-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="3fadb-103">移除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="3fadb-103">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="3fadb-104">語法</span><span class="sxs-lookup"><span data-stu-id="3fadb-104">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="3fadb-105">屬性</span><span class="sxs-lookup"><span data-stu-id="3fadb-105">Attribute</span></span>

|         | <span data-ttu-id="3fadb-106">描述</span><span class="sxs-lookup"><span data-stu-id="3fadb-106">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="3fadb-107">**key**</span><span class="sxs-lookup"><span data-stu-id="3fadb-107">**key**</span></span> | <span data-ttu-id="3fadb-108">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3fadb-108">Required attribute.</span></span><br><br><span data-ttu-id="3fadb-109">指定要移除之索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="3fadb-109">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="3fadb-110">父元素</span><span class="sxs-lookup"><span data-stu-id="3fadb-110">Parent element</span></span>

|     | <span data-ttu-id="3fadb-111">描述</span><span class="sxs-lookup"><span data-stu-id="3fadb-111">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="3fadb-112">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="3fadb-112">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="3fadb-113">子元素</span><span class="sxs-lookup"><span data-stu-id="3fadb-113">Child elements</span></span>

<span data-ttu-id="3fadb-114">None</span><span class="sxs-lookup"><span data-stu-id="3fadb-114">None</span></span>

## <a name="example"></a><span data-ttu-id="3fadb-115">範例</span><span class="sxs-lookup"><span data-stu-id="3fadb-115">Example</span></span>

<span data-ttu-id="3fadb-116">下列範例顯示如何移除的自訂設定 `ApplicationName` ：</span><span class="sxs-lookup"><span data-stu-id="3fadb-116">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="3fadb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fadb-117">See also</span></span>

- [<span data-ttu-id="3fadb-118">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="3fadb-118">Configuration file schema for the .NET Framework</span></span>](../index.md)
