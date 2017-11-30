---
title: "使用 F # 使用 Azure 封裝管理"
description: "使用 Paket 或 Nuget 來管理 F # Azure 相依性"
keywords: "visual f #、 f #，功能性程式設計，.NET 中，.NET Core，Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: 22dc94ea69e0dfb95e22da4bc64ce915398190d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="package-management-for-f-azure-dependencies"></a>F# Azure 相依性的套件管理

當您使用封裝管理員時，取得 Azure 開發的封裝很容易。 有兩種選項[Paket](https://fsprojects.github.io/Paket/)和[NuGet](https://www.nuget.org/)。

## <a name="using-paket"></a>使用 Paket

如果您使用[Paket](https://fsprojects.github.io/Paket/)為相依性管理員中，您可以使用`paket.exe`工具來加入 Azure 相依性。 例如: 

    > paket add nuget WindowsAzure.Storage

或者，如果您使用[Mono](http://www.mono-project.com/)適用於跨平台.NET 開發：

    > mono paket.exe add nuget WindowsAzure.Storage

這會新增`WindowsAzure.Storage`至目前目錄中專案的封裝相依性的設定，修改`paket.dependencies`檔案，並下載套件。 如果您先前設定的相依性，或使用專案所在的相依性已設定由另一個開發人員，您可以解決並安裝相依項目在本機像這樣：

    > paket install

或者，若為單聲道開發：

    > mono paket.exe install

您可以更新所有套件相依性的最新版本，就像這樣：

    > paket update

或者，若為單聲道開發：

    > mono paket.exe update

## <a name="using-nuget"></a>使用 Nuget

如果您使用[NuGet](https://www.nuget.org/)為相依性管理員中，您可以使用`nuget.exe`工具來加入 Azure 相依性。 例如: 

    > nuget install WindowsAzure.Storage -ExcludeVersion

或者，若為單聲道開發：

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

這會新增`WindowsAzure.Storage`至目前的目錄和下載封裝中的專案的封裝相依性的設定。 如果您先前設定的相依性，或使用專案所在的相依性已設定由另一個開發人員，您可以解決並安裝相依項目在本機像這樣：

    > nuget restore 

或者，若為單聲道開發：

    > mono nuget.exe restore

您可以更新所有套件相依性的最新版本，就像這樣：

    > nuget update

或者，若為單聲道開發：

    > mono nuget.exe update

## <a name="referencing-assemblies"></a>參考組件

若要在 F # 指令碼中使用您的封裝，您需要參考組件中使用的封裝包含`#r`指示詞。 例如: 

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

如您所見，您必須指定 DLL 和完整的 DLL 名稱可能不完全與封裝名稱相同的相對路徑。 路徑必須包含的 framework 版本，可能是封裝的版本號碼。 若要尋找所有已安裝的組件，您可以使用類似下面的 Windows 命令列上：

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

或 Unix 殼層，如下：

    > find packages/WindowsAzure.Storage -name "*.dll"

這可讓您的路徑已安裝的組件。 從該處，您可以選取 framework 版本的正確路徑。
