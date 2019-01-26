---
title: 啟動設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083414"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="083d4-102">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="083d4-102">Startup settings schema</span></span>

<span data-ttu-id="083d4-103">啟動設定會指定應執行應用程式之 Common Language Runtime 的版本。</span><span class="sxs-lookup"><span data-stu-id="083d4-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="083d4-104">元素</span><span class="sxs-lookup"><span data-stu-id="083d4-104">Element</span></span>|<span data-ttu-id="083d4-105">描述</span><span class="sxs-lookup"><span data-stu-id="083d4-105">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="083d4-106">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="083d4-106">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="083d4-107">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="083d4-107">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="083d4-108">使用執行階段版本 1.1 建置的應用程式應該使用 **\<supportedRuntime>** 項目。</span><span class="sxs-lookup"><span data-stu-id="083d4-108">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="083d4-109">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="083d4-109">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="083d4-110">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="083d4-110">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[<span data-ttu-id="083d4-111">\<startup></span><span class="sxs-lookup"><span data-stu-id="083d4-111">\<startup></span></span>](startup-element.md)|<span data-ttu-id="083d4-112">包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 項目。</span><span class="sxs-lookup"><span data-stu-id="083d4-112">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="083d4-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="083d4-113">See also</span></span>

- [<span data-ttu-id="083d4-114">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="083d4-114">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="083d4-115">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="083d4-115">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
