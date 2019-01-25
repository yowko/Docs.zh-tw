---
title: 啟動設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 12f91a1c74e85cbce0c8f641f202a181beb7412c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728904"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="ddb25-102">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ddb25-102">Startup settings schema</span></span>

<span data-ttu-id="ddb25-103">啟動設定會指定應執行應用程式之 Common Language Runtime 的版本。</span><span class="sxs-lookup"><span data-stu-id="ddb25-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="ddb25-104">元素</span><span class="sxs-lookup"><span data-stu-id="ddb25-104">Element</span></span>|<span data-ttu-id="ddb25-105">描述</span><span class="sxs-lookup"><span data-stu-id="ddb25-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddb25-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="ddb25-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="ddb25-107">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="ddb25-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ddb25-108">使用執行階段版本 1.1 建置的應用程式應該使用 **\<supportedRuntime>** 項目。</span><span class="sxs-lookup"><span data-stu-id="ddb25-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="ddb25-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="ddb25-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="ddb25-110">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="ddb25-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="ddb25-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="ddb25-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="ddb25-112">包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 項目。</span><span class="sxs-lookup"><span data-stu-id="ddb25-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddb25-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddb25-113">See also</span></span>

- [<span data-ttu-id="ddb25-114">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ddb25-114">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ddb25-115">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="ddb25-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
