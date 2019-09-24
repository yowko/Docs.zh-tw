---
title: 使用F#適用于 Azure 的套件管理
description: 使用 Paket 或 Nuget 來管理F# Azure 相依性
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 4aa32ace91f30d0e43b9c40067f5f0f456cc4069
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214222"
---
# <a name="package-management-for-f-azure-dependencies"></a>F# Azure 相依性的套件管理

當您使用套件管理員時，取得 Azure 開發的套件很容易。 這兩個選項為[Paket](https://fsprojects.github.io/Paket/)和[NuGet](https://www.nuget.org/)。

## <a name="using-paket"></a>使用 Paket

如果您使用[Paket](https://fsprojects.github.io/Paket/)做為相依性管理員，您可以使用`paket.exe`工具來新增 Azure 相依性。 例如：

```console
> paket add nuget WindowsAzure.Storage
```

或者，如果您要使用[Mono](https://www.mono-project.com/)進行跨平臺 .net 開發：

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

這會新增`WindowsAzure.Storage`至目前目錄中專案的封裝相依性集合、 `paket.dependencies`修改檔案，並下載封裝。 如果您先前已設定相依性，或正在使用已由另一個開發人員設定相依性的專案，您可以在本機解析並安裝相依性，如下所示：

```console
> paket install
```

或者，針對 Mono 開發：

```console
> mono paket.exe install
```

您可以將所有套件相依性更新為最新版本，如下所示：

```console
> paket update
```

或者，針對 Mono 開發：

```console
> mono paket.exe update
```

## <a name="using-nuget"></a>使用 Nuget

如果您使用[NuGet](https://www.nuget.org/)做為相依性管理員，您可以使用`nuget.exe`工具來新增 Azure 相依性。 例如：

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

或者，針對 Mono 開發：

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

這會在`WindowsAzure.Storage`目前目錄中加入專案的封裝相依性集合，並下載封裝。 如果您先前已設定相依性，或正在使用已由另一個開發人員設定相依性的專案，您可以在本機解析並安裝相依性，如下所示：

```console
> nuget restore
```

或者，針對 Mono 開發：

```console
> mono nuget.exe restore
```

您可以將所有套件相依性更新為最新版本，如下所示：

```console
> nuget update
```

或者，針對 Mono 開發：

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>參考組件

若要在您F#的腳本中使用您的封裝，您需要使用`#r`指示詞來參考封裝中包含的元件。 例如：

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

如您所見，您必須指定 DLL 的相對路徑以及完整的 DLL 名稱，這可能不會與封裝名稱完全相同。 此路徑會包含架構版本，而且可能會有套件版本號碼。 若要尋找所有已安裝的元件，您可以在 Windows 命令列上使用類似以下的內容：

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

或在 Unix shell 中，如下所示：

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

這會提供您已安裝元件的路徑。 您可以從該處選取架構版本的正確路徑。
