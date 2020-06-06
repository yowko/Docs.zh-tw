---
title: 啟動設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- startup settings schema
- schema startup settings
- configuration schema [.NET Framework], startup settings
ms.assetid: 03de6972-442a-4648-9f3e-efa654e3b949
ms.openlocfilehash: e5f9c9af64ff38e7c0f1f26ccab039261b052e30
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "61701511"
---
# <a name="startup-settings-schema"></a><span data-ttu-id="7bf19-102">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7bf19-102">Startup settings schema</span></span>

<span data-ttu-id="7bf19-103">啟動設定會指定應執行應用程式之 Common Language Runtime 的版本。</span><span class="sxs-lookup"><span data-stu-id="7bf19-103">Startup settings specify the version of the common language runtime that should run the application.</span></span>  
  
|<span data-ttu-id="7bf19-104">元素</span><span class="sxs-lookup"><span data-stu-id="7bf19-104">Element</span></span>|<span data-ttu-id="7bf19-105">描述</span><span class="sxs-lookup"><span data-stu-id="7bf19-105">Description</span></span>|  
|-------------|-----------------|  
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="7bf19-106">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="7bf19-106">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="7bf19-107">以執行階段版本1.1 建立的應用程式應該使用 **\<supportedRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="7bf19-107">Applications built with runtime version 1.1 should use the **\<supportedRuntime>** element.</span></span>|  
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="7bf19-108">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="7bf19-108">Specifies which versions of the common language runtime the application supports.</span></span>|  
|[\<startup>](startup-element.md)|<span data-ttu-id="7bf19-109">包含 **\<requiredRuntime>** 和 **\<supportedRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="7bf19-109">Contains the **\<requiredRuntime>** and **\<supportedRuntime>** elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7bf19-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bf19-110">See also</span></span>

- [<span data-ttu-id="7bf19-111">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="7bf19-111">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7bf19-112">如何：將應用程式設定為支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="7bf19-112">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
