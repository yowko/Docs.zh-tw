---
title: <appSettings> 的 <add> 項目
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214799"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="a6d23-102">\<appSettings> 的 \<add> 項目</span><span class="sxs-lookup"><span data-stu-id="a6d23-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="a6d23-103">新增自訂應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="a6d23-103">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="a6d23-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6d23-104">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="a6d23-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a6d23-105">Attributes</span></span>

|           | <span data-ttu-id="a6d23-106">描述</span><span class="sxs-lookup"><span data-stu-id="a6d23-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="a6d23-107">**key**</span><span class="sxs-lookup"><span data-stu-id="a6d23-107">**key**</span></span>   | <span data-ttu-id="a6d23-108">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a6d23-108">Required attribute.</span></span><br><br><span data-ttu-id="a6d23-109">指定要加入之索引鍵的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6d23-109">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="a6d23-110">**value**</span><span class="sxs-lookup"><span data-stu-id="a6d23-110">**value**</span></span> | <span data-ttu-id="a6d23-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a6d23-111">Required attribute.</span></span><br><br><span data-ttu-id="a6d23-112">指定要加入之索引鍵的值。</span><span class="sxs-lookup"><span data-stu-id="a6d23-112">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="a6d23-113">父元素</span><span class="sxs-lookup"><span data-stu-id="a6d23-113">Parent element</span></span>

|     | <span data-ttu-id="a6d23-114">描述</span><span class="sxs-lookup"><span data-stu-id="a6d23-114">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="a6d23-115">包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。</span><span class="sxs-lookup"><span data-stu-id="a6d23-115">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="a6d23-116">子元素</span><span class="sxs-lookup"><span data-stu-id="a6d23-116">Child elements</span></span>

<span data-ttu-id="a6d23-117">None</span><span class="sxs-lookup"><span data-stu-id="a6d23-117">None</span></span>

## <a name="example"></a><span data-ttu-id="a6d23-118">範例</span><span class="sxs-lookup"><span data-stu-id="a6d23-118">Example</span></span>

<span data-ttu-id="a6d23-119">下列範例顯示如何新增應用程式名稱的自訂設定：</span><span class="sxs-lookup"><span data-stu-id="a6d23-119">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="a6d23-120">下列範例會使用 `<add>` 元素，在 ASP.NET 應用程式中定義兩個相容性設定：</span><span class="sxs-lookup"><span data-stu-id="a6d23-120">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="a6d23-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d23-121">See also</span></span>

- [<span data-ttu-id="a6d23-122">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="a6d23-122">Configuration file schema for the .NET Framework</span></span>](../index.md)
