---
title: <appSettings> 的 <remove> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: cf9a34e47b70aaff12b29b9c5cf944d5bb15fee9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705385"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="59d6b-102">\<移除 > 項目\<appSettings ></span><span class="sxs-lookup"><span data-stu-id="59d6b-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="59d6b-103">移除自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="59d6b-103">Removes custom application settings.</span></span>

<span data-ttu-id="59d6b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="59d6b-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="59d6b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="59d6b-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="59d6b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span><span class="sxs-lookup"><span data-stu-id="59d6b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="59d6b-107">語法</span><span class="sxs-lookup"><span data-stu-id="59d6b-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="59d6b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="59d6b-108">Attribute</span></span>

|         | <span data-ttu-id="59d6b-109">描述</span><span class="sxs-lookup"><span data-stu-id="59d6b-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="59d6b-110">**key**</span><span class="sxs-lookup"><span data-stu-id="59d6b-110">**key**</span></span> | <span data-ttu-id="59d6b-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="59d6b-111">Required attribute.</span></span><br><br><span data-ttu-id="59d6b-112">指定要移除的索引鍵名稱。</span><span class="sxs-lookup"><span data-stu-id="59d6b-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="59d6b-113">父項目</span><span class="sxs-lookup"><span data-stu-id="59d6b-113">Parent element</span></span>

|     | <span data-ttu-id="59d6b-114">描述</span><span class="sxs-lookup"><span data-stu-id="59d6b-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="59d6b-115">**\<appSettings>**</span><span class="sxs-lookup"><span data-stu-id="59d6b-115">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="59d6b-116">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="59d6b-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="59d6b-117">子元素</span><span class="sxs-lookup"><span data-stu-id="59d6b-117">Child elements</span></span>

<span data-ttu-id="59d6b-118">None</span><span class="sxs-lookup"><span data-stu-id="59d6b-118">None</span></span>

## <a name="example"></a><span data-ttu-id="59d6b-119">範例</span><span class="sxs-lookup"><span data-stu-id="59d6b-119">Example</span></span>

<span data-ttu-id="59d6b-120">下列範例示範如何移除自訂組態設定`ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="59d6b-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="59d6b-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59d6b-121">See also</span></span>

- [<span data-ttu-id="59d6b-122">適用於.NET Framework 的組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="59d6b-122">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
