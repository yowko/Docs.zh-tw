---
title: "移轉到 .NET Core - 分析協力廠商相依性"
description: "移轉到 .NET Core - 分析協力廠商相依性"
keywords: ".NET、.NET Core"
author: cartermp
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
translationtype: Human Translation
ms.sourcegitcommit: 46061efa8e33c6a73befa5181eb33b8deb2fa637
ms.openlocfilehash: 7e4e96183484d102d102eeab97191f8be9b9be8a

---

# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a>移轉到 .NET Core - 分析協力廠商相依性

移轉程序的第一個步驟是了解您的協力廠商相依性。  您需要找出他們哪些尚未執行 .NET Core (如有)，並針對不執行 .NET Core 的開發應變計劃。

## <a name="prerequisites"></a>必要條件

本文假設您使用 Windows 和 Visual Studio，並且目前有在 .NET Framework 上執行的程式碼。

## <a name="analyzing-nuget-packages"></a>分析 NuGet 封裝

分析 NuGet 封裝的可攜性很簡單。  因為 NuGet 封裝本身是一組包含特定平台組件的資料夾，所以您只需要查看是否有包含 .NET Core 組件的資料夾即可。

使用 [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) 工具檢查 NuGet 封裝資料夾非常簡單。  以下為作法。

1. 下載並開啟 [NuGet Package Explorer] (NuGet 封裝總管)。
2. 按一下 「Open package from online feed」 (從線上摘要開啟封裝)。
3. 搜尋封裝的名稱。
4. 展開右手邊的 "lib" 資料夾，並查看資料夾名稱。

您也可以在 [nuget.org](https://www.nuget.org/) 該封裝頁面的 [相依性] 區段中查看封裝支援。

無論哪一種情況，您都需要在 [nuget.org](https://www.nuget.org/) 尋找有任何下列名稱的資料夾或項目︰

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

這些是對應 [.NET 標準程式庫](../../standard/library.md) 版本的目標 Framework Moniker (TFM) 版本，以及與 .NET Core 相容的傳統可攜式類別庫 (PCL) 設定檔。  請注意，當 `netcoreapp1.0` 相容時，是用於應用程式，不是程式庫。  雖然使用 `netcoreapp1.0` 型的程式庫沒有錯，但該程式庫可能原本只打算提供其他 `netcoreapp1.0` 應用程式使用。

還有在 .NET Core 發行前版本中使用的一些舊版 TFM 也可能是相容的：

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

**雖然這些可能適合您的程式碼使用，但不保證相容性**。  有這些 TFM 的封裝過去是使用發行前版本的 .NET Core 封裝建置的。  這類封裝更新為 `netstandard`型時請記錄。

> [!NOTE]
> 若要使用以傳統 PCL 或發行前版本 .NET Core 目標為目標的封裝，`project.json` 檔案中必須使用 `imports` 指示詞。

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>NuGet 封裝相依性在 .NET Core 上不執行時該怎麼辦

如果您依賴的 NuGet 封裝在 .NET Core 上不執行，您可以做幾件事。

1. 如果專案是開放原始碼並裝載在 GitHub 等位置，您可以直接連絡開發人員。
2. 您可以搜尋封裝，然後按一下封裝頁面左手邊的 「Contact Owners」 (連絡擁有者)，在 [nuget.org](https://www.nuget.org/) 直接連絡作者。
3. 您可以尋找另一個在 .NET Core 執行的封裝，與您所用封裝達成相同的工作。
4. 您可以嘗試自行撰寫封裝執行工作的程式碼。
5. 您可以變更應用程式的功能，消除封裝的相依性，至少等到有可用的相容版本封裝。

請記住，開放原始碼專案維護人員及 NuGet 封裝發行者通常是志願工作者，他們因為在乎指定的領域，所以無償付出，通常都有自己的正職工作。 如果連絡他們，請先提出對程式庫的正面評價，再要求 .NET Core 支援。

如果上述任何方法都無法解決您的問題，稍後可能必須移轉到 .NET Core。

.NET 小組希望知道哪些程式庫最重要，是 .NET Core 接下來要支援的對象。 您也可以傳送電子郵件至 dotnet@microsoft.com 討論您想使用的程式庫。

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a>分析不是 NuGet 封裝的相依性

您可能有不是 NuGet 封裝的相依性，例如檔案系統中的 DLL。  判斷該相依性可攜性的唯一方法，是執行 [ApiPort 工具](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/)。

## <a name="next-steps"></a>後續步驟

如要移轉程式庫，請參閱 [Porting to .NET Core - Libraries](libraries.md) (移轉至 .NET Core - 程式庫)。



<!--HONumber=Nov16_HO3-->


