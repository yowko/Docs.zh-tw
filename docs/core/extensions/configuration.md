---
title: .NET 中的設定
description: 瞭解如何使用設定 API 來設定 .NET 應用程式。
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: overview
ms.openlocfilehash: f5dc7c99b209b16dfb8595f9d50dcb1428bbde84
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2020
ms.locfileid: "91607993"
---
# <a name="configuration-in-net"></a>.NET 中的設定

.NET 中的設定是使用一或多個設定 [提供者](#configuration-providers)來執行。 設定提供者會使用各種設定來源從機碼值組讀取設定資料：

- 設定檔，例如 *appsettings.js*
- 環境變數
- [Azure 金鑰保存庫](/azure/key-vault/general/overview)
- [Azure 應用程式組態](/azure/azure-app-configuration/overview)
- 命令列引數
- 自訂提供者、已安裝或已建立
- 目錄檔案
- 記憶體內部 .NET 物件

## <a name="configure-console-apps"></a>設定主控台應用程式

根據預設，使用 [dotnet new](../tools/dotnet-new.md) 或 Visual Studio 建立新的 .net 主控台應用程式 *不會* 公開設定功能。 若要在新的 .NET 主控台應用程式中加入設定，請 [將封裝參考加入](../tools/dotnet-add-package.md) 至 `Microsoft.Extensions.Hosting` 。 修改 *Program.cs* 檔案，以符合下列程式碼：

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

方法會依 <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> 下列順序提供應用程式的預設設定：

1. [ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource) ：加入現有的 `IConfiguration` 作為來源。
1. 使用[JSON 設定提供者](configuration-providers.md#file-configuration-provider)的*appsettings.js* 。
1. *appsettings。* `Environment`使用[json 設定提供者](configuration-providers.md#file-configuration-provider)的*json。* 例如， *appsettings*。***生產環境***。*json* 和 *appsettings*。***開發***。*json*。
1. 應用程式在環境中執行時的應用程式秘密 `Development` 。
1. 使用 [環境變數設定提供者](configuration-providers.md#environment-variable-configuration-provider)的環境變數。
1. 使用 [命令列設定提供者](configuration-providers.md#command-line-configuration-provider)的命令列引數。

稍後新增的設定提供者會覆寫先前的金鑰設定。 例如，如果在 `SomeKey` 和環境的 *appsettings.js* 中設定，則會使用環境值。 使用預設的設定提供者， [命令列設定提供者](configuration-providers.md#command-line-configuration-provider) 會覆寫所有其他提供者。

### <a name="binding"></a>繫結

在 .NET 中設定的主要優點之一，就是能夠將設定值系結至 .NET 物件的實例。 例如，JSON 設定提供者可以用來將檔案 * 上的appsettings.js* 對應至 .net 物件，並與相依性插入一起使用。 這會啟用選項模式，選項模式會使用類別來提供相關設定群組的強型別存取。

## <a name="configuration-providers"></a>設定提供者

下表顯示 .NET Core 應用程式可用的設定提供者。

| 提供者                                                                                                               | 從提供設定        |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [Azure App 設定提供者](/azure/azure-app-configuration/quickstart-aspnet-core-app)                          | Azure 應用程式組態            |
| [Azure Key Vault 設定提供者](/azure/key-vault/general/tutorial-net-virtual-machine)                        | Azure 金鑰保存庫                    |
| [命令列設定提供者](configuration-providers.md#command-line-configuration-provider)                  | 命令列參數            |
| [自訂設定提供者](custom-configuration-provider.md)                                                      | 自訂來源                      |
| [環境變數設定提供者](configuration-providers.md#environment-variable-configuration-provider) | 環境變數              |
| [檔案設定提供者](configuration-providers.md#file-configuration-provider)                                  | JSON、XML 和 INI 檔案           |
| [每個檔案的金鑰配置提供者](configuration-providers.md#key-per-file-configuration-provider)                  | 目錄檔案                    |
| [記憶體設定提供者](configuration-providers.md#memory-configuration-provider)                              | 記憶體內集合              |
| [ (秘密管理員) 的應用程式秘密 ](/aspnet/core/security/app-secrets)                                                      | 使用者設定檔目錄中的檔案 |

如需各種設定提供者的詳細資訊，請參閱 [.net 中的設定提供者](configuration-providers.md)。

## <a name="see-also"></a>另請參閱

- [.NET 中的設定提供者](configuration-providers.md)
- [實作自訂組態提供者](custom-configuration-provider.md)
- 應該在 [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues) 存放庫中建立設定錯誤
