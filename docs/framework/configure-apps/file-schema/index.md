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
ms.openlocfilehash: 6ebb6487136bff567c57143e3000a20270c1f87e
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674902"
---
# <a name="configuration-file-schema-for-the-net-framework"></a>.NET Framework 的組態檔結構描述

組態檔是標準的 XML 檔，可以用來變更應用程式的設定和設定應用程式的原則。 .NET Framework 組態結構描述所包含的項目可在組態檔中用來控制應用程式的行為。 本節的目錄反映出啟動、執行階段、網路和其他類型組態設定的結構描述階層架構。

如需組態檔之類型、格式和位置的資訊，請參閱 [設定應用程式](~/docs/framework/configure-apps/index.md)一文。 如果想要直接編輯組態檔，請熟悉 XML。

> [!IMPORTANT]
> 組態檔中的 XML 標記和屬性區分大小寫。

## <a name="in-this-section"></a>本節內容

[**\<configuration>** 項目](~/docs/framework/configure-apps/file-schema/configuration-element.md) - 描述 `<configuration>` 項目，這個項目是所有組態檔的最上層項目。

[**\<assemblyBinding>** 項目](~/docs/framework/configure-apps/file-schema/assemblybinding-element-for-configuration.md) - 指定位於組態層級的組件繫結原則。

[**\<linkedConfiguration>** 項目](~/docs/framework/configure-apps/file-schema/linkedconfiguration-element.md) - 指定要包含的組態檔。

[啟動設定結構描述](~/docs/framework/configure-apps/file-schema/startup/index.md) - 描述指定要使用的 Common Language Runtime 版本的項目。

[執行階段設定結構描述](~/docs/framework/configure-apps/file-schema/runtime/index.md) - 描述設定組件繫結和執行階段行為的項目。

[網路設定結構描述](~/docs/framework/configure-apps/file-schema/network/index.md) - 描述指定 .NET Framework 連線到網際網路之方式的項目。

[密碼編譯設定結構描述](~/docs/framework/configure-apps/file-schema/cryptography/index.md) - 描述將易記的演算法名稱對應至實作密碼編譯演算法之類別的項目。

[組態區段結構描述](~/docs/framework/configure-apps/file-schema/configuration-sections-schema.md) - 描述用來建立和使用自訂設定之組態區段的項目。

[追蹤和偵錯設定結構描述](~/docs/framework/configure-apps/file-schema/trace-debug/index.md) - 描述指定追蹤參數和接聽項的項目。

[編譯器和語言提供者設定結構描述](~/docs/framework/configure-apps/file-schema/compiler/index.md) - 描述在指定可用的語言提供者之編譯器組態的項目。

[應用程式設定結構描述](~/docs/framework/configure-apps/file-schema/application-settings-schema.md) - 描述可讓 Windows Forms 或 ASP.NET 應用程式儲存及擷取應用程式範圍和使用者範圍設定的項目。

[應用程式設定結構描述](~/docs/framework/configure-apps/file-schema/appsettings/index.md) - 包含自訂應用程式設定，例如檔案路徑、XML Web 服務 URL，或應用程式的任何其他自訂組態資訊。

[Web 設定結構描述](~/docs/framework/configure-apps/file-schema/web/index.md) - Web 設定結構描述中的所有項目，包括用來設定 ASP.NET 如何配合主機應用程式 (例如 IIS) 運作的項目。 用於 *Aspnet.config* 檔案。

[Windows Forms 組態結構描述](winforms/index.md) - Windows Forms 應用程式組態區段中的所有項目，包括多重監視器和高 DPI 支援等自訂項目。

[WCF 組態結構描述](~/docs/framework/configure-apps/file-schema/wcf/index.md) - 可讓您設定 WCF 服務與用戶端應用程式的所有項目。

[WCF 指示詞語法](~/docs/framework/configure-apps/file-schema/wcf-directive/index.md) - 描述定義 .svc 編譯器使用之網頁專用屬性的 `@ServiceHost` 指示詞。

[WIF 組態結構描述](windows-identity-foundation/index.md) - Windows Identity Foundation (WIF) 組態結構描述的所有項目。

## <a name="related-sections"></a>相關章節

[遠端設定結構描述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/z415cf9a(v=vs.100)) - 描述設定實作遠端處理之用戶端和伺服器應用程式的項目。

[ASP.NET 設定結構描述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/b5ysx397(v=vs.100)) - 描述控制 ASP.NET Web 應用程式之行為的項目。

[Web 服務設定結構描述](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cctwteet(v=vs.100)) - 描述控制 ASP.NET Web 服務和其用戶端之行為的項目。

[設定 .NET Framework 應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/kza1yk3a(v=vs.100)) - 描述如何在 .NET Framework 中設定安全性、組件繫結和遠端處理。
