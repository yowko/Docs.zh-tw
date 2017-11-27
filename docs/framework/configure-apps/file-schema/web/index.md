---
title: "Web 設定結構描述"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: efdfba94bd2d2a64b3434c97f30a035f210fda9a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="web-settings-schema"></a><span data-ttu-id="ed6e8-102">Web 設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ed6e8-102">Web Settings Schema</span></span>
<span data-ttu-id="ed6e8-103">Web 設定會指定 CPU 和執行層級 ASP.NET 設定，這些設定將套用至 ASP.NET 裝載層管理的整個處理序行為。</span><span class="sxs-lookup"><span data-stu-id="ed6e8-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="ed6e8-104">這些設定不同於 ASP.NET 應用程式之 Web.config 檔中所指定的應用程式定義域類型設定。</span><span class="sxs-lookup"><span data-stu-id="ed6e8-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
 <span data-ttu-id="ed6e8-105">Web 設定包含在 Aspnet.config 檔中，此檔案位於 .NET Framework 各版本的安裝資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ed6e8-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="ed6e8-106">例如，[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] 的 Aspnet.config 檔位於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="ed6e8-106">For example, the Aspnet.config file for [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] is in the following folder:</span></span>  
  
 `C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
 <span data-ttu-id="ed6e8-107">Web 設定會在於任何其他組態檔中使用，例如 machine.config 檔、根目錄 Web.config 或應用程式層級 Web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="ed6e8-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  
  
 [<span data-ttu-id="ed6e8-108">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="ed6e8-108">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="ed6e8-109">\<system.web> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="ed6e8-109">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)  
  
 [<span data-ttu-id="ed6e8-110">\<applicationPool> 項目 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="ed6e8-110">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)  
  
|<span data-ttu-id="ed6e8-111">項目</span><span class="sxs-lookup"><span data-stu-id="ed6e8-111">Element</span></span>|<span data-ttu-id="ed6e8-112">說明</span><span class="sxs-lookup"><span data-stu-id="ed6e8-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed6e8-113">\<system.web></span><span class="sxs-lookup"><span data-stu-id="ed6e8-113">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="ed6e8-114">包含 ASP.NET 裝載層使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="ed6e8-114">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[<span data-ttu-id="ed6e8-115">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="ed6e8-115">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="ed6e8-116">指定 CPU 和執行層級 ASP.NET 設定，這些設定將套用至 ASP.NET 裝載層管理的整個處理序行為。</span><span class="sxs-lookup"><span data-stu-id="ed6e8-116">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ed6e8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed6e8-117">See Also</span></span>  
 [<span data-ttu-id="ed6e8-118">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="ed6e8-118">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
