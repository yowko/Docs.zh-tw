---
title: 使用 macOS Catalina 公證
description: 安裝 .NET Core 運行時、SDK 和使用 .NET Core 構建的應用程式時，如何處理 macOS 的公證和證書問題。
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146745"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina 公證及其對 .NET 核心下載和專案的影響

從 macOS Catalina（版本 10.15）開始，所有在 2019 年 6 月 1 日之後構建且使用開發人員 ID 分發的軟體都必須經過公證。 此要求適用于 .NET 核心運行時、.NET 核心 SDK 和使用 .NET Core 創建的軟體。 本文介紹了使用 .NET Core 和 macOS 公證可能面臨的常見方案。

## <a name="installing-net-core"></a>安裝 .NET Core

自 2020 年 2 月 18 日起，對 .NET Core（運行時和 SDK）版本 3.1、3.0 和 2.1 的安裝程式進行了公證。 未對以前發佈的版本進行公證。 您可以手動安裝未經公證版本的 .NET Core，首先下載安裝程式，然後使用 命令`sudo installer`。 有關詳細資訊，請參閱為[macOS 下載和手動安裝](sdk.md?pivots=os-macos#download-and-manually-install)。

從以下版本開始，對 .NET Core 安裝程式進行了公證：

- .NET Core 執行階段
  - 2.1.16
  - 3.0.3
  - 3.1.2

- .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>預設情況下禁用應用主機

預設情況下，在專案編譯、發佈或運行時，.NET Core SDK 3.0 及以上的非公證版本將生成本機 Mach-O 可執行檔（稱為**appHost）。** 此可執行檔是運行應用的便捷方式。 否則，你的應用必須通過運行`dotnet <filename.dll>`啟動。 啟用應用Host後，將在`dotnet run`應用Host 的上下文中調用該命令。 有關詳細資訊，請參閱[應用Host 的上下文](#context-of-the-apphost)。

從 .NET Core SDK 3.0 及以上公證版本開始，預設情況下不會生成 appHost 可執行檔。 您可以使用專案檔案中的[`UseAppHost`](../project-sdk/msbuild-props.md#useapphost)布林設置打開 appHost 生成。 您還可以在命令列上切換應用Host，`-p:UseAppHost`以進行運行的特定`dotnet`命令：

- 專案檔

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- 命令列參數

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

發佈應用[自包含](../deploying/index.md#publish-self-contained)時，始終會創建應用Host。

有關該`UseAppHost`設置的詳細資訊，請參閱[Microsoft.NET.Sdk 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。

### <a name="context-of-the-apphost"></a>應用主機的上下文

在專案中啟用 appHost 並使用`dotnet run`該命令運行應用時，將在 appHost 的上下文中而不是預設主機（預設主機是`dotnet`命令）中調用應用。 如果在專案中禁用了 appHost，該命令將在`dotnet run`預設主機的上下文中運行應用。 即使禁用了 appHost，將應用發佈為自包含將生成一個 AppHost 可執行檔，並且使用者使用該可執行檔來運行你的應用。 使用`dotnet <filename.dll>`預設主機（共用運行時）調用應用運行應用。

調用使用 appHost 的應用時，應用訪問的證書分區與經公證的預設主機不同。 如果應用必須訪問通過預設主機安裝的證書，請使用 命令`dotnet run`從其專案檔案運行應用，或使用 該`dotnet <filename.dll>`命令直接啟動應用。

有關此方案的詳細資訊，ASP.NET[核心和 macOS 和證書](#aspnet-core-and-macos-and-certificates)部分提供。

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET核心和 macOS 和證書

.NET Core 提供使用<xref:System.Security.Cryptography.X509Certificates>類管理 macOS 鑰匙串中的證書的能力。 在決定要考慮哪個分區時，對 macOS 鑰匙串的訪問使用應用程式標識作為主鍵。 例如，未簽名的應用程式在未簽名的分區中存儲機密，但簽名的應用程式僅將其機密存儲在分區中，他們才能訪問。 調用應用的執行源決定要使用的分區。

.NET Core 提供三個執行源[：appHost、](#apphost-is-disabled-by-default)預設主機`dotnet`（命令）和自訂主機。 每個執行模型可能具有不同的標識（簽名身份或未簽名身份），並且有權訪問鑰匙串中的不同分區。 一種模式導入的證書可能無法從另一種模式訪問。 例如，.NET Core 的公證版本具有已簽名的預設主機。 證書根據其標識導入到安全分區中。 這些證書無法從生成的應用Host訪問，因為應用Host是無符號的。

另一個示例，預設情況下，ASP.NET核心通過預設主機導入預設 SSL 憑證。 ASP.NET使用 appHost 的酷睿應用程式將無法訪問此證書，並且當 .NET Core 檢測到證書不可訪問時，將收到錯誤。 錯誤訊息提供有關如何解決此問題的說明。

如果需要證書共用，macOS 會為`security`實用程式提供配置選項。

有關如何解決ASP.NET核心證書問題的詳細資訊，請參閱[ASP.NET核心中強制實施 HTTPS。](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems)

## <a name="default-entitlements"></a>預設權利

.NET Core 的預設主機（`dotnet`命令）具有一組預設許可權。 這些權利是 .NET Core 正常運行所必需的。 您的應用程式可能需要其他授權，在這種情況下，您需要生成和使用[appHost，](#apphost-is-disabled-by-default)然後在本地添加必要的授權。

.NET Core 的預設許可權集：

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>公證 .NET 核心應用

如果希望應用程式在 macOS Catalina（版本 10.15）或更高版本上運行，則需要對應用進行公證。 與應用程式一起提交的用於公證的應用Host 應至少與 .NET Core 相同的[預設許可權](#default-entitlements)一起使用。

## <a name="next-steps"></a>後續步驟

- [.NET 核心依賴項和要求](dependencies.md)。
- [安裝 .NET 核心 SDK](sdk.md)。
- [安裝 .NET 核心運行時](runtime.md)
