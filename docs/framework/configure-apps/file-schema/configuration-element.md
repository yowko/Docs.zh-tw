---
title: "&lt;組態&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration
helpviewer_keywords:
- <configuration> element
- configuration element
- container tags, <configuration> element
ms.assetid: 2ec1c9dc-2e5c-4ef0-9958-81670ab88449
caps.latest.revision: "15"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2241f3e835defe308b94d0cbad96020518dfd19b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-element"></a><span data-ttu-id="b89a7-102">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="b89a7-102">\<configuration> element</span></span>

<span data-ttu-id="b89a7-103">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-103">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>

<span data-ttu-id="b89a7-104">**\<configuration>**</span><span class="sxs-lookup"><span data-stu-id="b89a7-104">**\<configuration>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b89a7-105">語法</span><span class="sxs-lookup"><span data-stu-id="b89a7-105">Syntax</span></span>

```xml
<configuration>
  <!-- Configuration settings -->
</configuration>
```

## <a name="attributes"></a><span data-ttu-id="b89a7-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b89a7-106">Attributes</span></span>

<span data-ttu-id="b89a7-107">無</span><span class="sxs-lookup"><span data-stu-id="b89a7-107">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="b89a7-108">父項目</span><span class="sxs-lookup"><span data-stu-id="b89a7-108">Parent element</span></span>

<span data-ttu-id="b89a7-109">無</span><span class="sxs-lookup"><span data-stu-id="b89a7-109">None</span></span>

## <a name="child-elements"></a><span data-ttu-id="b89a7-110">子元素</span><span class="sxs-lookup"><span data-stu-id="b89a7-110">Child elements</span></span>

|     | <span data-ttu-id="b89a7-111">說明</span><span class="sxs-lookup"><span data-stu-id="b89a7-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b89a7-112">**\<assemblyBinding >**</span><span class="sxs-lookup"><span data-stu-id="b89a7-112">**\<assemblyBinding>**</span></span>](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) | <span data-ttu-id="b89a7-113">指定位於組態層級的組件繫結原則。</span><span class="sxs-lookup"><span data-stu-id="b89a7-113">Specifies assembly binding policy at the configuration level.</span></span>|
| [<span data-ttu-id="b89a7-114">**\<啟動 >**設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-114">**\<startup>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/startup/index.md) | <span data-ttu-id="b89a7-115">啟動設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-115">All elements in the startup settings schema.</span></span> |
| [<span data-ttu-id="b89a7-116">**\<執行階段 >**設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-116">**\<runtime>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/runtime/index.md) | <span data-ttu-id="b89a7-117">執行階段設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-117">All elements in the runtime settings schema.</span></span> |
| [<span data-ttu-id="b89a7-118">**\<system.runtime.remoting >**設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-118">**\<system.runtime.remoting>** Settings Schema</span></span>](http://msdn.microsoft.com/dc2d1e62-9af7-4ca1-99fd-98b93bb4db9e) | <span data-ttu-id="b89a7-119">在 遠端設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-119">All elements in the remoting settings schema.</span></span> |
| [<span data-ttu-id="b89a7-120">**\<system.Net >**設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-120">**\<system.Net>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/network/index.md) | <span data-ttu-id="b89a7-121">網路設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-121">All elements in the network settings schema.</span></span> |
| [<span data-ttu-id="b89a7-122">**\<cryptographySettings >**設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-122">**\<cryptographySettings>** Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/cryptography/index.md) | <span data-ttu-id="b89a7-123">密碼編譯設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-123">All elements in the crypto settings schema.</span></span> |
| [<span data-ttu-id="b89a7-124">**\<設定 >**區段結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-124">**\<configuration>** Sections Schema</span></span>](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) | <span data-ttu-id="b89a7-125">組態區段設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-125">All elements in the configuration section settings schema.</span></span> |
| [<span data-ttu-id="b89a7-126">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-126">Trace and Debug Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) | <span data-ttu-id="b89a7-127">追蹤和偵錯設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-127">All elements in the trace and debug settings schema.</span></span> |
| <span data-ttu-id="b89a7-128">[ASP.NET 組態設定結構描述](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span><span class="sxs-lookup"><span data-stu-id="b89a7-128">[ASP.NET Configuration Settings Schema](https://msdn.microsoft.com/library/b5ysx397(v=vs.100).aspx)</span></span> | <span data-ttu-id="b89a7-129">ASP.NET 設定結構描述，包括用來設定 ASP.NET 網站和應用程式的項目中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-129">All elements in the ASP.NET configuration schema, which includes elements for configuring ASP.NET Web sites and applications.</span></span> <span data-ttu-id="b89a7-130">用於*Web.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="b89a7-130">Used in *Web.config* files.</span></span> |
| [<span data-ttu-id="b89a7-131">**\<web 服務 >**設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-131">**\<webServices>** Settings Schema</span></span>](http://msdn.microsoft.com/f84d6d55-1add-4eb7-ae46-33df5833ea2e) | <span data-ttu-id="b89a7-132">Web 服務設定結構描述中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-132">All elements in the Web services settings schema.</span></span> |
| [<span data-ttu-id="b89a7-133">Web 設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-133">Web Settings Schema</span></span>](~/docs/framework/configure-apps/file-schema/web/index.md) | <span data-ttu-id="b89a7-134">Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-134">All elements in the Web settings schema, which includes elements for configuring how ASP.NET works with a host application such as IIS.</span></span> <span data-ttu-id="b89a7-135">用於*aspnet.config*檔案。</span><span class="sxs-lookup"><span data-stu-id="b89a7-135">Used in *aspnet.config* files.</span></span> |

## <a name="remarks"></a><span data-ttu-id="b89a7-136">備註</span><span class="sxs-lookup"><span data-stu-id="b89a7-136">Remarks</span></span>

<span data-ttu-id="b89a7-137">每個組態檔必須剛好包含一個**\<組態 >**項目。</span><span class="sxs-lookup"><span data-stu-id="b89a7-137">Each configuration file must contain exactly one **\<configuration>** element.</span></span>

## <a name="see-also"></a><span data-ttu-id="b89a7-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="b89a7-138">See also</span></span>

[<span data-ttu-id="b89a7-139">適用於.NET Framework 組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="b89a7-139">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)
