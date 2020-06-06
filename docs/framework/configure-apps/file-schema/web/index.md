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
ms.openlocfilehash: 030841330ff37cddb0c9e3e466a55a4be098e784
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088782"
---
# <a name="web-settings-schema"></a>Web 設定結構描述
Web 設定會指定 CPU 和執行層級 ASP.NET 設定，這些設定將套用至 ASP.NET 裝載層管理的整個處理序行為。 這些設定不同於 ASP.NET 應用程式之 Web.config 檔中所指定的應用程式定義域類型設定。  
  
Web 設定包含在 Aspnet.config 檔中，此檔案位於 .NET Framework 各版本的安裝資料夾中。 例如，.NET Framework 2.0 的 Aspnet .config 檔案位於下列資料夾中：  
  
`C:\Windows\Microsoft.NET\Framework\v2.0.50727\`  
  
Web 設定會在於任何其他組態檔中使用，例如 machine.config 檔、根目錄 Web.config 或應用程式層級 Web.config 檔。  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<applicationPool>**](applicationpool-element-web-settings.md)

|元素|描述|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|包含 ASP.NET 裝載層使用的資訊。|  
|[\<applicationPool>](applicationpool-element-web-settings.md)|指定 CPU 和執行層級 ASP.NET 設定，這些設定將套用至 ASP.NET 裝載層管理的整個處理序行為。|  
  
## <a name="see-also"></a>另請參閱

- [設定檔架構](../index.md)
