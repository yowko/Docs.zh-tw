---
title: 使用 macOS Catalina Notarization
description: 當您安裝使用 .NET Core 建立的 .NET Core 執行時間、SDK 和應用程式時，如何處理 macOS 的 notarization 和憑證問題。
author: adegeo
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: 905a8b8a4a17836823b1c6574828acb08110d224
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415954"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a>macOS Catalina Notarization 和對 .NET Core 下載和專案的影響

從 macOS Catalina （版本10.15）開始，在2019年6月1日之後建立的所有軟體，以及以開發人員識別碼發佈之後，都必須是公證。 這項需求適用于 .NET core 執行時間、.NET Core SDK 和使用 .NET Core 所建立的軟體。 本文說明您在 .NET Core 和 macOS notarization 中可能會面臨的常見案例。

## <a name="installing-net-core"></a>安裝 .NET Core

從2020年2月18日起，已公證 .NET Core （執行時間和 SDK）版本3.1、3.0 和2.1 的安裝程式。 先前發行的版本不會公證。 您可以手動安裝非公證版本的 .NET Core，方法是先下載安裝程式，然後再使用 `sudo installer` 命令。 如需詳細資訊，請參閱[下載並手動安裝 macOS](sdk.md?pivots=os-macos#download-and-manually-install)。

從下列版本開始，會公證 .NET Core 安裝程式：

- .NET Core 執行階段
  - 2.1.16
  - 3.0.3
  - 3.1.2

- .NET Core SDK
  - 2.1.512
  - 3.0.103
  - 3.1.102

## <a name="apphost-is-disabled-by-default"></a>appHost 預設為停用

根據預設，當您的專案編譯、發行或執行時，不公證的 .NET Core SDK 3.0 和更新版本會產生原生符合-O 可執行檔（稱為**appHost**）。 這個可執行檔是執行應用程式的便利方式。 否則，您的應用程式必須藉由執行來啟動 `dotnet <filename.dll>` 。 當 appHost 啟用時， `dotnet run` 會在 apphost 的內容中叫用命令。 如需詳細資訊，請參閱[appHost 的內容](#context-of-the-apphost)。

從 .NET Core SDK 3.0 和更新版本的公證版開始，appHost 可執行檔預設不會產生。 您可以使用 [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) 專案檔中的布林值設定來開啟 appHost 產生。 您也可以在 `-p:UseAppHost` 命令列上，使用參數在您執行的特定命令上切換 appHost `dotnet` ：

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

當您發佈[獨立](../deploying/index.md#publish-self-contained)應用程式時，一律會建立 appHost。

如需設定的詳細資訊 `UseAppHost` ，請參閱[適用于 Microsoft .Net 的 MSBuild 屬性](../project-sdk/msbuild-props.md#useapphost)。

### <a name="context-of-the-apphost"></a>AppHost 的內容

當您的專案中已啟用 appHost，而且您使用 `dotnet run` 命令來執行應用程式時，會在 appHost 的內容中叫用應用程式，而不是在預設主機上叫用（預設主機是 `dotnet` 命令）。 如果您的專案中已停用 appHost，此 `dotnet run` 命令會在預設主機的內容中執行您的應用程式。 即使已停用 appHost，以獨立式形式發佈應用程式也會產生 appHost 可執行檔，而使用者會使用該可執行檔來執行您的應用程式。 執行應用程式時 `dotnet <filename.dll>` ，會使用預設主機（共用執行時間）叫用應用程式。

叫用使用 appHost 的應用程式時，應用程式所存取的憑證分割區與公證預設主機不同。 如果您的應用程式必須存取透過預設主機安裝的憑證，請使用 `dotnet run` 命令從其專案檔執行您的應用程式，或使用 `dotnet <filename.dll>` 命令直接啟動應用程式。

如需此案例的詳細資訊，請[ASP.NET Core 和 macOS 和憑證](#aspnet-core-and-macos-and-certificates)一節中提供。

## <a name="aspnet-core-and-macos-and-certificates"></a>ASP.NET Core 和 macOS 和憑證

.NET Core 提供使用類別來管理 macOS Keychain 中憑證的功能 <xref:System.Security.Cryptography.X509Certificates> 。 在決定要考慮哪一個分割區時，存取 macOS Keychain 會使用應用程式身分識別做為主要金鑰。 例如，未簽署的應用程式會在不帶正負號的磁碟分割中儲存秘密，但已簽署的應用程式只會將其秘密儲存在資料分割 叫用您的應用程式的執行來源會決定要使用的資料分割。

.NET Core 提供三個執行來源： [appHost](#apphost-is-disabled-by-default)、預設主機（ `dotnet` 命令）和自訂主機。 每個執行模型可能會有不同的身分識別（帶正負號或不帶正負號），並可存取 Keychain 內的不同分割區。 一種模式匯入的憑證可能無法從另一種方式存取。 例如，公證版本的 .NET Core 具有已簽署的預設主控制項。 憑證會根據其身分識別匯入到安全的磁碟分割中。 因為 appHost 不帶正負號，所以無法從產生的 appHost 存取這些憑證。

另一個範例是，ASP.NET Core 預設會透過預設主機匯入預設的 SSL 憑證。 ASP.NET Core 使用 appHost 的應用程式不會有此憑證的存取權，而且當 .NET Core 偵測到無法存取憑證時，將會收到錯誤。 錯誤訊息提供如何修正此問題的指示。

如果需要共用憑證，macOS 會提供公用程式的設定選項 `security` 。

如需有關如何針對 ASP.NET Core 憑證問題進行疑難排解的詳細資訊，請參閱[在 ASP.NET Core 中強制執行 HTTPS](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems)。

## <a name="default-entitlements"></a>預設權利

.NET Core 的預設主機（ `dotnet` 命令）具有一組預設權利。 需要這些權利，才能正常運作 .NET Core。 您的應用程式可能需要額外的權利，在此情況下，您必須產生並使用[appHost](#apphost-is-disabled-by-default) ，然後在本機新增必要的權利。

.NET Core 的預設權利集：

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a>Notarize .NET Core 應用程式

如果您想要讓應用程式在 macOS Catalina （10.15 版）或更新版本上執行，您會想要 notarize 您的應用程式。 您使用應用程式進行 notarization 所提交的 appHost，應至少與 .NET Core 的相同[預設權利](#default-entitlements)搭配使用。

## <a name="next-steps"></a>後續步驟

- [.Net Core 相依性和需求](dependencies.md)。
- [安裝 .Net Core 執行時間和 SDK](macos.md)。
