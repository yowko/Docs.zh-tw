---
title: 使用 macOS Catalina 公證
description: 當您安裝以 .NET Core 建立的 .NET Core 執行時間、SDK 和應用程式時，如何處理 macOS 的公證和憑證問題。
author: adegeo
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: 616f163856cca48ccc6d1a14e0c6e68d56379c0c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538298"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina 公證和 .NET Core 下載和專案的影響

從 macOS Catalina () 10.15 版開始，在2019年6月1日之後建立的所有軟體都必須公證。 這項需求適用于使用 .NET Core 建立的 .NET Core 執行時間、.NET Core SDK 和軟體。 本文說明使用 .NET Core 和 macOS 公證時可能面臨的常見案例。

## <a name="installing-net-core"></a>安裝 .NET Core

.NET Core 的安裝程式 (執行時間和 SDK) 3.1、3.0 和2.1 版，自2020年2月18日起已公證。 先前發行的版本不會公證。 您可以手動安裝 .NET Core 的非公證版本，方法是先下載安裝程式，然後使用 `sudo installer` 命令。 如需詳細資訊，請參閱 [下載並手動安裝以進行 macOS](./macos.md#download-and-manually-install)。

從下列版本開始，.NET Core 安裝程式會公證：

- .NET Core 執行階段
  - 2.1.16
  - 3.0.3
  - 3.1.2

- .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>預設會停用 appHost

根據預設，.NET Core SDK 3.0 和更新版本的非公證版本會在您的專案編譯、發行或執行時，產生原生的符合-O 可執行檔 (稱為 **appHost**) 。 這個可執行檔是執行應用程式的便利方式。 否則，您的應用程式必須藉由執行來啟動 `dotnet <filename.dll>` 。 當 appHost 啟用時， `dotnet run` 會在 apphost 的內容中叫用此命令。 如需詳細資訊，請參閱 [appHost 的內容](#context-of-the-apphost)。

從 .NET Core SDK 3.0 和更新版本的公證版本開始，預設不會產生 appHost 可執行檔。 您可以使用 [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) 專案檔中的布林值設定來開啟 appHost 產生。 您也可以使用 `-p:UseAppHost` 命令列上的參數來切換 appHost，以執行您所執行的特定 `dotnet` 命令：

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

當您發行 [獨立](../deploying/index.md#publish-self-contained)應用程式時，一律會建立 appHost。

如需有關此設定的詳細資訊 `UseAppHost` ，請參閱 [適用于 Microsoft .Net 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。

### <a name="context-of-the-apphost"></a>AppHost 的內容

當您的專案中已啟用 appHost，且您使用 `dotnet run` 命令來執行應用程式時，會在 appHost 的內容中叫用應用程式，而不是預設主機 (預設主機是 `dotnet` 命令) 。 如果您的專案中已停用 appHost，此 `dotnet run` 命令會在預設主機的內容中執行您的應用程式。 即使已停用 appHost，將您的應用程式發佈為獨立的會產生 appHost 可執行檔，而使用者會使用該可執行檔來執行您的應用程式。 執行應用程式時 `dotnet <filename.dll>` ，會使用預設主控制項（共用執行時間）來叫用應用程式。

叫用使用 appHost 的應用程式時，應用程式所存取的憑證磁碟分割與公證預設主機不同。 如果您的應用程式必須存取透過預設主機安裝的憑證，請使用 `dotnet run` 命令從其專案檔執行您的應用程式，或使用 `dotnet <filename.dll>` 命令直接啟動應用程式。

如需此案例的詳細資訊，請 [ASP.NET Core 和 macOS 和憑證](#aspnet-core-and-macos-and-certificates) 一節中提供。

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core 和 macOS 和憑證

.NET Core 提供在 macOS Keychain 中使用類別來管理憑證的功能 <xref:System.Security.Cryptography.X509Certificates> 。 當您決定要考慮的分割區時，存取 macOS Keychain 會使用應用程式身分識別作為主要金鑰。 例如，未簽署的應用程式會將秘密儲存在未簽署的磁碟分割中，但已簽署的應用程式只會將其秘密儲存在磁碟分割中 叫用應用程式的執行來源會決定要使用的資料分割。

.NET Core 提供三個執行來源： [appHost](#apphost-is-disabled-by-default)、預設主機 (`dotnet` 命令) 和自訂主機。 每個執行模型可能會有不同的身分識別（帶正負號或不帶正負號），而且可以存取 Keychain 中的不同資料分割。 可能無法從另一個模式匯入憑證。 例如，.NET Core 的公證版本具有已簽署的預設主機。 憑證會根據其身分識別匯入至安全的磁碟分割。 因為 appHost 未簽署，所以無法從產生的 appHost 存取這些憑證。

另一個範例 ASP.NET Core 預設會透過預設主機匯入預設 SSL 憑證。 ASP.NET Core 使用 appHost 的應用程式將無法存取此憑證，且當 .NET Core 偵測到無法存取憑證時，將會收到錯誤。 錯誤訊息提供如何修正此問題的指示。

如果需要共用憑證，macOS 會提供公用程式的設定選項 `security` 。

如需有關如何針對 ASP.NET Core 憑證問題進行疑難排解的詳細資訊，請參閱 [ASP.NET Core 中的強制使用 HTTPS](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems)。

## <a name="default-entitlements"></a>預設權利

.NET Core 的預設主機 (`dotnet` 命令) 有一組預設權利。 需要這些權利才能正常運作 .NET Core。 您的應用程式可能需要額外的權利，在這種情況下，您必須產生並使用 [appHost](#apphost-is-disabled-by-default) ，然後在本機新增必要的權利。

.NET Core 的預設權利集：

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>驗證 .NET Core 應用程式

如果您想要在 macOS Catalina () 10.15 版或更高版本上執行您的應用程式，則需要驗證您的應用程式。 您使用應用程式進行公證提交的 appHost，應至少與 .NET Core 的相同 [預設權利](#default-entitlements) 搭配使用。

## <a name="next-steps"></a>後續步驟

- [.Net Core 相依性和需求](macos.md#dependencies)。
- [安裝 .Net Core 執行時間和 SDK](macos.md)。
