---
title: dotnet list package 命令
description: "'dotnet list package' 命令提供一個便利選項，可列出適用於專案或解決方案的套件參考。"
ms.date: 06/26/2019
ms.openlocfilehash: 48eef0ccc6acf2bbd6c1acf748870882d2480ce5
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168026"
---
# <a name="dotnet-list-package"></a>dotnet list package

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>名稱

`dotnet list package` - 列出適用於專案或解決方案的套件參考。

## <a name="synopsis"></a>概要

```console
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>說明

`dotnet list package` 命令提供一個便利選項，可列出適用於特定專案或解決方案的所有 NuGet 套件參考。 您需要先建置專案，才能具備處理此命令所需的資產。 下列範例會針對 [SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 專案顯示 `dotnet list package` 命令的輸出：

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**Requested** 欄會參考專案檔中所指定的套件版本，而且可以是一個範圍。 **Resolved** 欄會列出專案目前正在使用的版本，且一律為單一值。 名稱旁邊顯示 `(A)` 的套件代表[隱含的套件參考](csproj.md#implicit-package-references)，可從您的專案設定 (`Sdk` 類型、`<TargetFramework>` 或 `<TargetFrameworks>` 屬性等) 進行推斷。

使用 `--outdated` 選項，以找出您在專案中所使用的套件是否有較新版本可供使用。 除非已解析的版本也是發行前版本，否則 `--outdated` 預設會列出最新的穩定套件。 若要在列出較新的版本時包含發行前版本，也需指定 `--include-prerelease` 選項。 下列範例會針對與上一個範例相同的專案顯示 `dotnet list package --outdated --include-prerelease` 命令的輸出：

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

如果您需要找出專案是否有可轉移的相依性，請使用 `--include-transitive` 選項。 當您在之後將依賴另一個套件的專案中新增套件時，就會發生可轉移的相依性。 下列範例會針對 [HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) 專案顯示執行 `dotnet list package --include-transitive` 命令的輸出，其會顯示最上層套件及其相依的套件：

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a>引數

`PROJECT | SOLUTION`

要在其上運作的專案或解決方案檔。 如果未指定，命令會在目前的目錄中搜尋一個專案檔。 如果找到一個以上的解決方案或專案，則會擲回錯誤。

## <a name="options"></a>選項

* **`--config <SOURCE>`**

  搜尋較新的套件時要使用的 NuGet 來源。 需要 `--outdated` 選項。

* **`--framework <FRAMEWORK>`**

  只顯示適用於所指定[目標 Framework](../../standard/frameworks.md) 的套件。 若要指定多個架構，請多次指定該選項。 例如：`--framework netcoreapp2.2 --framework netstandard2.0`。

* **`-h|--help`**

  印出命令的簡短說明。

* **`--highest-minor`**

  在搜尋較新的套件時，建議只搜尋主要版本號碼相符的套件。 需要 `--outdated` 選項。

* **`--highest-patch`**

  在搜尋較新的套件時，建議只搜尋主要和次要版本號碼相符的套件。 需要 `--outdated` 選項。

* **`--include-prerelease`**

  在搜尋較新的套件時，建議搜尋具有發行前版本的套件。 需要 `--outdated` 選項。

* **`--include-transitive`**

  列出可轉移的套件 (除了最上層套件)。 指定此選項時，您會取得最上層套件所依存的套件清單。

* **`--interactive`**

  可讓命令停止，並等候使用者輸入或進行動作。 例如完成驗證。 自 .NET Core 3.0 SDK 起提供使用。

* **`--outdated`**

  列出有較新版本可供使用的套件。

* **`-s|--source <SOURCE>`**

  搜尋較新的套件時要使用的 NuGet 來源。 需要 `--outdated` 選項。

## <a name="examples"></a>範例

* 列出特定專案的套件參考：

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* 列出有較新版本可供使用 (包括發行前版本) 的套件參考：

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* 列出適用於特定目標 Framework 的套件參考：

  ```console
  dotnet list package --framework netcoreapp3.0
  ```
