---
title: 如何安裝 ML.NET 命令列介面 (CLI) 工具
description: ML.NET 命令列介面 (CLI) 工具的概觀與安裝。
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: baced9bbcc72153458d42d4b6d8206921bf187b8
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117996"
---
# <a name="how-to-install-the-mlnet-command-line-interface-cli-tool"></a>如何安裝 ML.NET 命令列介面 (CLI) 工具

ML.NET CLI (命令列介面) 是您可以在任何命令提示字元 (Windows、Mac 或 Linux) 中執行的工具，根據您提供的定型資料集產生高品質 ML.NET 模型和原始程式碼。

> [!NOTE]
> 本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。

## <a name="pre-requisites"></a>必要條件

- [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2)

- (選擇性) [Visual Studio 2017 或 2019](https://visualstudio.microsoft.com/vs/)

您可以使用 Visual Studio F5 或 `dotnet run` (.NET Core CLI) 執行已產生的 C# 程式碼專案。

注意：如果在安裝 [.NET Core 2.2 SDK](https://dotnet.microsoft.com/download/dotnet-core/2.2) 後，`dotnet tool` 命令無法運作，請登出 Windows，並再次登入。

## <a name="install"></a>安裝

ML.NET CLI 的安裝就像任何其他 dotnet 通用工具。 您會使用 `dotnet tool install` .NET Core CLI 命令。 

下列範例示範如何在 NuGet 摘要位置中安裝 ML.NET CLI：

```dotnetcli
dotnet tool install -g mlnet
```

如果無法安裝此工具 (亦即如果它無法自預設的 NuGet 摘要取得)，則會顯示錯誤訊息。 請確認正在檢查您所預期的摘要。

如果安裝成功，則會顯示一則訊息，其中顯示用來呼叫此工具的命令以及安裝的版本，類似於下例範例：

```console
You can invoke the tool using the following command: mlnet
Tool 'mlnet' (version 'X.X.X') was successfully installed.
```

您可以鍵入下列命令確認安裝是否成功：

```console
mlnet
```

您應該會看到 mlnet 工具可用命令的說明，例如 'auto-train' 命令。

## <a name="install-a-specific-release-version"></a>安裝特定的發行版本

如果您要嘗試安裝發行前版本或特定版本的工具，可以使用下列格式指定[架構](../../standard/frameworks.md)：

```dotnetcli
dotnet tool install -g mlnet --framework <FRAMEWORK>
```

您也可以鍵入下列命令，檢查套件是否正確安裝：

```dotnetcli
dotnet tool list -g
```

## <a name="uninstall-the-cli-package"></a>解除安裝 CLI 套件

鍵入下列命令，從本機電腦解除安裝套件：

```dotnetcli
dotnet tool uninstall mlnet -g
```

## <a name="update-the-cli-package"></a>更新 CLI 套件

鍵入下列命令，從本機電腦更新套件：

```dotnetcli
dotnet tool update -g mlnet
```

## <a name="set-up-cli-suggestions-tab-based-auto-completion"></a>設定 CLI 建議 (tab 鍵自動完成)

因為 ML.NET CLI 是以 `System.CommandLine` 為基礎，所以它有內建的 tab 鍵自動完成支援。

下列動畫展示 tab 鍵自動完成運作範例：

![影像](./media/cli-tab-completion.gif)

「tab 鍵自動完成」(參數建議) 適用於 *Windows PowerShell* 和 *macOS/Linux bash*，但不適用於 *Windows CMD*。

若要啟用它，在目前的預覽版本中，終端使用者必須針對每個 shell 各採取一些步驟，如下所述。 完成此作業後，使用 `System.CommandLine` 撰寫的所有應用程式，例如 ML.NET CLI，都會執行完成。

在您想要啟用完成的電腦上，您需要做兩件事。

1. 執行下列命令以安裝 `dotnet-suggest` 通用工具：

    ```dotnetcli
    dotnet tool install dotnet-suggest -g
    ```

2. 將適當的填充碼指令碼新增至 shell 設定檔。 您可能必須建立 shell 設定檔。 填充碼指令碼會將完成要求，從您的 shell 轉送至 `dotnet-suggest`工具，委派給 `System.CommandLine` 型的應用程式。

    - 若是 Bash，請將 [dotnet-suggest-shim.bash](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.bash) 的內容新增至 `~/.bash_profile`。

    - 若為 PowerShell，請將 [dotnet-suggest-shim.ps1](https://github.com/dotnet/System.CommandLine/blob/master/src/System.CommandLine.Suggest/dotnet-suggest-shim.ps1) 的內容新增至您的 PowerShell 設定檔。 您可在主控台中執行下列命令，找到 PowerShell 設定檔的預期路徑：

    ```console
    echo $profile
    ``` 

(若為其他 shell，請[尋求](https://github.com/dotnet/System.CommandLine/issues?q=is%3Aissue+is%3Aopen+label%3A%22shell+suggestion%22)或提出[問題](https://github.com/dotnet/System.CommandLine/issues)。)

## <a name="installation-directory"></a>安裝目錄

ML.NET CLI 可以安裝在預設目錄或特定位置。 預設目錄如下：

| 作業系統          | 路徑                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

第一次執行 SDK　時，這些位置會新增至使用者的路徑，因此可以直接呼叫安裝在該處的通用工具。

請注意，通用工具是使用者特定工具，而不是電腦全域工具。 使用者特定表示您無法安裝可供電腦上所有使用者使用的通用工具。 此工具只適用於已安裝工具的每個使用者設定檔。

通用工具也可以安裝在特定目錄中。 安裝在特定目錄時，使用者必須確保命令可用，方法是在路徑中包含該目錄、使用指定的目錄呼叫命令，或從指定的目錄中呼叫工具。
在此情況下，.NET Core CLI 不會將這個位置自動新增至 PATH 環境變數。

## <a name="see-also"></a>另請參閱

- [＜ML.NET CLI 工具使用者入門＞的教學課程](../tutorials/mlnet-cli.md)
- [如何使用 ML.NET CLI 工具自動定型模型](../automate-training-with-cli.md)
- [ML.NET CLI 自動定型命令參考指南](../reference/ml-net-cli-reference.md) 
- [ML.NET CLI 中的遙測](../resources/ml-net-cli-telemetry.md)
