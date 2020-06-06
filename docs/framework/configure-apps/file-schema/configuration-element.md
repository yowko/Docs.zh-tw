---
title: <configuration> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
ms.openlocfilehash: 0e09ec49024b769c516fd97085904781f64b4486
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "69921241"
---
# <a name="configuration-element"></a><span data-ttu-id="24388-102">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="24388-102">\<configuration> element</span></span>

<span data-ttu-id="24388-103">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="24388-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

**\<configuration>**

## <a name="syntax"></a><span data-ttu-id="24388-104">語法</span><span class="sxs-lookup"><span data-stu-id="24388-104">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="24388-105">屬性</span><span class="sxs-lookup"><span data-stu-id="24388-105">Attributes</span></span>

<span data-ttu-id="24388-106">無</span><span class="sxs-lookup"><span data-stu-id="24388-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="24388-107">父元素</span><span class="sxs-lookup"><span data-stu-id="24388-107">Parent element</span></span>

<span data-ttu-id="24388-108">無</span><span class="sxs-lookup"><span data-stu-id="24388-108">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="24388-109">子元素</span><span class="sxs-lookup"><span data-stu-id="24388-109">Child elements</span></span>

|     | <span data-ttu-id="24388-110">描述</span><span class="sxs-lookup"><span data-stu-id="24388-110">Description</span></span> |
| --- | ----------- |
| [**\<assemblyBinding>**](assemblybinding-element-for-configuration.md) | <span data-ttu-id="24388-111">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="24388-111">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="24388-112">**\<startup>** 設定架構</span><span class="sxs-lookup"><span data-stu-id="24388-112">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="24388-113">啟動設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-113">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="24388-114">**\<runtime>** 設定架構</span><span class="sxs-lookup"><span data-stu-id="24388-114">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="24388-115">執行時間設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-115">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="24388-116">[**\<system.runtime.remoting>** 設定架構](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="24388-116">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="24388-117">遠端設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-117">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="24388-118">**\<system.Net>** 設定架構</span><span class="sxs-lookup"><span data-stu-id="24388-118">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="24388-119">網路設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-119">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="24388-120">**\<cryptographySettings>** 設定架構</span><span class="sxs-lookup"><span data-stu-id="24388-120">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="24388-121">加密設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-121">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="24388-122">**\<configuration>** 區段架構</span><span class="sxs-lookup"><span data-stu-id="24388-122">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="24388-123">Configuration 區段設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-123">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="24388-124">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="24388-124">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="24388-125">追蹤和 debug 設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-125">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="24388-126">[ASP.NET 設定架構](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="24388-126">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="24388-127">ASP.NET 設定架構中的所有元素，包括用於設定 ASP.NET 網站和應用程式的元素。</span><span class="sxs-lookup"><span data-stu-id="24388-127">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="24388-128">用於 web.config*檔案中。*</span><span class="sxs-lookup"><span data-stu-id="24388-128">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="24388-129">[**\<webServices>** 設定架構](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="24388-129">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="24388-130">Web 服務設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="24388-130">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="24388-131">Web 設定結構描述</span><span class="sxs-lookup"><span data-stu-id="24388-131">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="24388-132">Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。</span><span class="sxs-lookup"><span data-stu-id="24388-132">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="24388-133">用於*aspnet .config*檔案。</span><span class="sxs-lookup"><span data-stu-id="24388-133">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="24388-134">備註</span><span class="sxs-lookup"><span data-stu-id="24388-134">Remarks</span></span>

<span data-ttu-id="24388-135">每個設定檔都必須剛好包含一個 **\<configuration>** 元素。</span><span class="sxs-lookup"><span data-stu-id="24388-135">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="24388-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24388-136">See also</span></span>

- [<span data-ttu-id="24388-137">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="24388-137">Configuration file schema for the .NET Framework</span></span>](index.md)
