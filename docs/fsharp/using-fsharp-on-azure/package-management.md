---
title: 使用封裝管理與F#適用於 Azure
description: 使用 Paket 或 Nuget 來管理F#Azure 相依性
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: b180024e2276a2fd7786f35cb922b1aa1d91f0ad
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880011"
---
# <a name="package-management-for-f-azure-dependencies"></a>F# Azure 相依性的套件管理

取得適用於 Azure 的開發套件，很容易使用的套件管理員。 兩個選項都[Paket](https://fsprojects.github.io/Paket/)並[NuGet](https://www.nuget.org/)。

## <a name="using-paket"></a>使用 Paket

如果您使用[Paket](https://fsprojects.github.io/Paket/)為您的相依性管理員，您可以使用`paket.exe`加入 Azure 的相依性的工具。 例如：

```
> paket add nuget WindowsAzure.Storage
```

或者，如果您使用[Mono](https://www.mono-project.com/)適用於跨平台.NET 開發：

```
> mono paket.exe add nuget WindowsAzure.Storage
```

這會新增`WindowsAzure.Storage`到目前的目錄中專案的套件相依性，修改`paket.dependencies`檔案，並下載套件。 如果您先前已設定相依性，或正在使用專案所在的相依性已設定的另一個開發人員，您可以解決，並安裝相依項目，在本機像這樣：

```
> paket install
```

或者，若為 Mono 的開發：

```
> mono paket.exe install
```

您可以更新所有套件相依性的最新的版本，就像這樣：

```
> paket update
```

或者，若為 Mono 的開發：

```
> mono paket.exe update
```

## <a name="using-nuget"></a>使用 Nuget

如果您使用[NuGet](https://www.nuget.org/)為您的相依性管理員，您可以使用`nuget.exe`加入 Azure 的相依性的工具。 例如: 

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

或者，若為 Mono 的開發：

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

這會新增`WindowsAzure.Storage`到目前的目錄，並下載封裝中的專案的套件相依性。 如果您先前已設定相依性，或正在使用專案所在的相依性已設定的另一個開發人員，您可以解決，並安裝相依項目，在本機像這樣：

```
> nuget restore
```

或者，若為 Mono 的開發：

```
> mono nuget.exe restore
```

您可以更新所有套件相依性的最新的版本，就像這樣：

```
> nuget update
```

或者，若為 Mono 的開發：

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>參考組件

若要使用您的套件，在您F#指令碼中，您必須參考包含在封裝中使用的組件`#r`指示詞。 例如: 

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

如您所見，您必須指定 DLL 和可能不會完全封裝名稱相同的完整 DLL 名稱的相對路徑。 路徑必須包含的 framework 版本和可能的套件版本號碼。 若要尋找所有已安裝的組件，您可以在 Windows 命令列上使用起來像這樣：

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

或者，在 Unix 殼層中，項目如下所示：

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

這可讓您的路徑已安裝的組件。 從該處，您可以選取正確的路徑的 framework 版本。
