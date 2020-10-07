---
title: '使用套件管理搭配適用于 Azure 的 F #'
description: '使用 Paket 或 NuGet 來管理 F # Azure 相依性'
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 7816c82e87db113a35fef967886c8c3e27959332
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756230"
---
# <a name="package-management-for-f-azure-dependencies"></a>F# Azure 相依性的套件管理

當您使用套件管理員時，取得 Azure 開發的套件很簡單。 這兩個選項為 [Paket](https://fsprojects.github.io/Paket/) 和 [NuGet](https://www.nuget.org/)。

## <a name="using-paket"></a>使用 Paket

如果您使用 [Paket](https://fsprojects.github.io/Paket/) 作為相依性管理員，您可以使用此 `paket.exe` 工具來新增 Azure 相依性。 例如：

```console
> paket add nuget WindowsAzure.Storage
```

或者，如果您要使用 [Mono](https://www.mono-project.com/) 進行跨平臺 .net 開發：

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

這會將 `WindowsAzure.Storage` 您在目前目錄中的專案套件相依性集合新增至您的套件相依性集合，並修改該檔案 `paket.dependencies` ，然後下載封裝。 如果您先前已設定相依性，或正在使用另一個開發人員已設定相依性的專案，您可以在本機解析並安裝相依性，如下所示：

```console
> paket install
```

或者，對於 Mono 開發：

```console
> mono paket.exe install
```

您可以將所有套件相依性更新為最新版本，如下所示：

```console
> paket update
```

或者，對於 Mono 開發：

```console
> mono paket.exe update
```

## <a name="using-nuget"></a>使用 NuGet

如果您使用 [NuGet](https://www.nuget.org/) 做為您的相依性管理員，您可以使用此 `nuget.exe` 工具來新增 Azure 相依性。 例如：

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

或者，對於 Mono 開發：

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

這會將 `WindowsAzure.Storage` 您在目前目錄中的專案套件相依性集合新增至集合，並下載套件。 如果您先前已設定相依性，或正在使用另一個開發人員已設定相依性的專案，您可以在本機解析並安裝相依性，如下所示：

```console
> nuget restore
```

或者，對於 Mono 開發：

```console
> mono nuget.exe restore
```

您可以將所有套件相依性更新為最新版本，如下所示：

```console
> nuget update
```

或者，對於 Mono 開發：

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>參考組件

若要在 F # 腳本中使用您的封裝，您需要使用指示詞來參考封裝中包含的元件 `#r` 。 例如：

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

如您所見，您必須指定 DLL 的相對路徑和完整的 DLL 名稱，這可能與封裝名稱不完全相同。 路徑將包含 framework 版本，也可能包含套件版本號碼。 若要尋找所有已安裝的元件，您可以在 Windows 命令列上使用像這樣的內容：

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

或在 Unix shell 中，如下所示：

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

這會提供您已安裝元件的路徑。 您可以從該處選取您 framework 版本的正確路徑。
