---
title: .NET Framework 的組態檔結構描述
ms.date: 05/01/2017
helpviewer_keywords:
- .NET Framework application configuration, configuration schema
- machine configuration files
- application configuration files, schema
- app.config files, schema
- schema configuration settings
- schemas, configuration settings
- enterprisesec.config files
- well-formed XML
- enterprisesec configuration files
- security.config files
- security [.NET Framework], configuration files
- application development [.NET Framework], schema
- XML tags
- container tags
- machine.config files
- configuration schema [.NET Framework]
- configuration settings [.NET Framework], applications
- configuration file reference [.NET Framework]
ms.assetid: 69003d39-dc8a-460c-a6be-e6d93e690b38
ms.openlocfilehash: ab6f12be01899f5b7e54a7ec2d9675d502d88bc3
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555129"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework 的組態檔結構描述

組態檔是標準的 XML 檔，可以用來變更應用程式的設定和設定應用程式的原則。 .NET Framework 組態結構描述所包含的項目可在組態檔中用來控制應用程式的行為。 本節的目錄反映出啟動、執行階段、網路和其他類型組態設定的結構描述階層架構。

如需配置檔案類型、格式和位置的相關資訊，請參閱 [設定應用程式](../index.md)。 如果想要直接編輯組態檔，請熟悉 XML。

> [!IMPORTANT]
> 組態檔中的 XML 標記和屬性區分大小寫。

## <a name="in-this-section"></a>本節內容

[**\<configuration>** 元素](configuration-element.md)\
所有設定檔的最上層元素。

[**\<assemblyBinding>** 元素](assemblybinding-element-for-configuration.md)\
指定位於組態層級的組件繫結原則。

[**\<linkedConfiguration>** 元素](linkedconfiguration-element.md)\
指定要包含的組態檔。

[啟動設定架構](./startup/index.md)\
元素，指定要使用的 common language runtime 版本。

[執行時間設定架構](./runtime/index.md)\
設定元件系結和執行時間行為的元素。

[網路設定架構](./network/index.md)\
指定 .NET Framework 如何連接到網際網路的元素。

[密碼編譯設定架構](./cryptography/index.md)\
將易記的演算法名稱對應至執行密碼編譯演算法之類別的元素。

[設定區段架構](configuration-sections-schema.md)\
用來建立及使用自訂設定之設定區段的元素。

[追蹤和調試設定架構](./trace-debug/index.md)\
指定追蹤參數和接聽程式的元素。

[編譯器和語言提供者設定架構](./compiler/index.md)\
指定可用語言提供者之編譯器設定的元素。

[應用程式設定架構](application-settings-schema.md)\
可讓 Windows Forms 或 ASP.NET 應用程式儲存和取出應用程式範圍和使用者範圍設定的元素。

[應用程式設定架構](./appsettings/index.md)\
包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。

[Web 設定架構](./web/index.md)\
用來設定 ASP.NET 如何搭配主機應用程式（例如 IIS）運作的元素。 用於 *Aspnet.config* 檔案。

[Windows Forms 設定架構](winforms/index.md)\
[Windows Forms 應用程式設定] 區段中的所有元素，包括多監視器和高 DPI 支援等自訂。

[WCF 設定架構](./wcf/index.md)\
所有可讓您設定 WCF 服務和用戶端應用程式的元素。

[WCF 指示詞語法](./wcf-directive/index.md)\
描述指示詞，此指示詞會 `@ServiceHost` 定義 .svc 編譯器使用的頁面特定屬性。

[WIF 設定架構](windows-identity-foundation/index.md)\
Windows Identity Foundation (的所有元素都會 WIF) 設定架構。

## <a name="related-sections"></a>相關章節

[遠端設定架構](/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100))\
說明設定實作遠端處理之用戶端和伺服器應用程式的項目。

[ASP.NET 設定架構](/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100))\
描述控制 ASP.NET Web 應用程式之行為的項目。

[Web 服務設定架構](/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100))\
描述控制 ASP.NET Web 服務和其用戶端之行為的項目。

[設定 .NET Framework 應用程式](/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100))\
描述如何在 .NET Framework 中設定安全性、組件繫結和遠端處理。
