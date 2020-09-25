---
title: Web 設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- ASP.NET configuration system, Web settings schema
- schema Web settings
- Web settings, schema [ASP.NET]
- configuration files [ASP.NET]
- configuration schema [.NET Framework], Web settings
ms.assetid: ae1ac356-267d-4753-8d7a-7a04eb45a9be
ms.openlocfilehash: c3ac9b42aeff3f7b26f0b36480bc75ceda39e7e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185596"
---
# <a name="web-settings-schema"></a><span data-ttu-id="2cae0-102">Web 設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2cae0-102">Web Settings Schema</span></span>

<span data-ttu-id="2cae0-103">Web 設定會指定 CPU 和執行層級 ASP.NET 設定，這些設定將套用至 ASP.NET 裝載層管理的整個處理序行為。</span><span class="sxs-lookup"><span data-stu-id="2cae0-103">Web settings specify CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span> <span data-ttu-id="2cae0-104">這些設定不同於 ASP.NET 應用程式之 Web.config 檔中所指定的應用程式定義域類型設定。</span><span class="sxs-lookup"><span data-stu-id="2cae0-104">These settings differ from application domain-type settings that are specified in the Web.config file of an ASP.NET application.</span></span>  
  
<span data-ttu-id="2cae0-105">Web 設定包含在 Aspnet.config 檔中，此檔案位於 .NET Framework 各版本的安裝資料夾中。</span><span class="sxs-lookup"><span data-stu-id="2cae0-105">Web settings are contained in Aspnet.config files, which are located in the installation folders for versions of the .NET Framework.</span></span> <span data-ttu-id="2cae0-106">例如，.NET Framework 2.0 的 Aspnet.config 檔案位於下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="2cae0-106">For example, the Aspnet.config file for .NET Framework 2.0 is in the following folder:</span></span>  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
<span data-ttu-id="2cae0-107">Web 設定會在於任何其他組態檔中使用，例如 machine.config 檔、根目錄 Web.config 或應用程式層級 Web.config 檔。</span><span class="sxs-lookup"><span data-stu-id="2cae0-107">Web settings are not used in any other configuration files such as the machine.config file, the root Web.config, or application-level Web.config files.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|<span data-ttu-id="2cae0-108">項目</span><span class="sxs-lookup"><span data-stu-id="2cae0-108">Element</span></span>|<span data-ttu-id="2cae0-109">描述</span><span class="sxs-lookup"><span data-stu-id="2cae0-109">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="2cae0-110">包含 ASP.NET 裝載層使用的資訊。</span><span class="sxs-lookup"><span data-stu-id="2cae0-110">Contains information that the ASP.NET hosting layer uses.</span></span>|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|<span data-ttu-id="2cae0-111">指定 CPU 和執行層級 ASP.NET 設定，這些設定將套用至 ASP.NET 裝載層管理的整個處理序行為。</span><span class="sxs-lookup"><span data-stu-id="2cae0-111">Specifies CPU and execution-level ASP.NET settings that apply to process-wide behavior managed by the ASP.NET hosting layer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2cae0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cae0-112">See also</span></span>

- [<span data-ttu-id="2cae0-113">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="2cae0-113">Configuration File Schema</span></span>](../index.md)
