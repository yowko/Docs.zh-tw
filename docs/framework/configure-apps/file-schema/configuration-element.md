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
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921241"
---
# <a name="configuration-element"></a><span data-ttu-id="ef07c-102">\<configuration > 元素</span><span class="sxs-lookup"><span data-stu-id="ef07c-102">\<configuration> element</span></span>

<span data-ttu-id="ef07c-103">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ef07c-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="ef07c-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="ef07c-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ef07c-105">語法</span><span class="sxs-lookup"><span data-stu-id="ef07c-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="ef07c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="ef07c-106">Attributes</span></span>

<span data-ttu-id="ef07c-107">無</span><span class="sxs-lookup"><span data-stu-id="ef07c-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="ef07c-108">父項目</span><span class="sxs-lookup"><span data-stu-id="ef07c-108">Parent element</span></span>

<span data-ttu-id="ef07c-109">無</span><span class="sxs-lookup"><span data-stu-id="ef07c-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="ef07c-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ef07c-110">Child elements</span></span>

|     | <span data-ttu-id="ef07c-111">描述</span><span class="sxs-lookup"><span data-stu-id="ef07c-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="ef07c-112"> **\<assemblyBinding>** </span><span class="sxs-lookup"><span data-stu-id="ef07c-112">**\<assemblyBinding>**</span></span>](assemblybinding-element-for-configuration.md) | <span data-ttu-id="ef07c-113">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="ef07c-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="ef07c-114">啟動 > 設定架構 **\<** </span><span class="sxs-lookup"><span data-stu-id="ef07c-114">**\<startup>** Settings Schema</span></span>](./startup/index.md) | <span data-ttu-id="ef07c-115">啟動設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="ef07c-116">執行時間 > 設定架構 **\<** </span><span class="sxs-lookup"><span data-stu-id="ef07c-116">**\<runtime>** Settings Schema</span></span>](./runtime/index.md) | <span data-ttu-id="ef07c-117">執行時間設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-117">All elements in the runtime settings schema.</span></span> |
| <span data-ttu-id="ef07c-118">[system.web > 設定架構 **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef07c-118">[**\<system.runtime.remoting>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))</span></span> | <span data-ttu-id="ef07c-119">遠端設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="ef07c-120">系統 .net > 設定架構 **\<** </span><span class="sxs-lookup"><span data-stu-id="ef07c-120">**\<system.Net>** Settings Schema</span></span>](./network/index.md) | <span data-ttu-id="ef07c-121">網路設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="ef07c-122">cryptographySettings > 設定架構 **\<** </span><span class="sxs-lookup"><span data-stu-id="ef07c-122">**\<cryptographySettings>** Settings Schema</span></span>](./cryptography/index.md) | <span data-ttu-id="ef07c-123">加密設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="ef07c-124">configuration > 區段架構 **\<** </span><span class="sxs-lookup"><span data-stu-id="ef07c-124">**\<configuration>** Sections Schema</span></span>](configuration-sections-schema.md) | <span data-ttu-id="ef07c-125">Configuration 區段設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="ef07c-126">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ef07c-126">Trace and Debug Settings Schema</span></span>](./trace-debug/index.md) | <span data-ttu-id="ef07c-127">追蹤和 debug 設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="ef07c-128">[ASP.NET 設定架構](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef07c-128">[ASP.NET Configuration Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))</span></span> | <span data-ttu-id="ef07c-129">ASP.NET 設定架構中的所有元素, 包括用於設定 ASP.NET 網站和應用程式的元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="ef07c-130">用於 web.config檔案中。</span><span class="sxs-lookup"><span data-stu-id="ef07c-130">Used in *Web.config* files.</span></span> |
| <span data-ttu-id="ef07c-131">[webServices > 設定架構 **\<** ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ef07c-131">[**\<webServices>** Settings Schema](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))</span></span> | <span data-ttu-id="ef07c-132">Web 服務設定架構中的所有元素。</span><span class="sxs-lookup"><span data-stu-id="ef07c-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="ef07c-133">Web 設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ef07c-133">Web Settings Schema</span></span>](./web/index.md) | <span data-ttu-id="ef07c-134">Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。</span><span class="sxs-lookup"><span data-stu-id="ef07c-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="ef07c-135">用於*aspnet .config*檔案。</span><span class="sxs-lookup"><span data-stu-id="ef07c-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="ef07c-136">備註</span><span class="sxs-lookup"><span data-stu-id="ef07c-136">Remarks</span></span>

<span data-ttu-id="ef07c-137">每個組態檔必須剛好包含一個 **\<組態>** 項目。</span><span class="sxs-lookup"><span data-stu-id="ef07c-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef07c-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef07c-138">See also</span></span>

- [<span data-ttu-id="ef07c-139">.NET Framework 的設定檔架構</span><span class="sxs-lookup"><span data-stu-id="ef07c-139">Configuration file schema for the .NET Framework</span></span>](index.md)
