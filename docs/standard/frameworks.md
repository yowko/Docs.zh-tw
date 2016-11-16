---
title: "架構"
description: "架構"
keywords: .NET, .NET Core
author: richlander
manager: wpickett
ms.date: 09/19/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
translationtype: Human Translation
ms.sourcegitcommit: 246d381246e78a27b7097d6b8126f421b52014de
ms.openlocfilehash: 5b87ddfcfc66ebc05e2e559517180f93813a0806

---

# <a name="frameworks"></a>架構

.NET 生態系統有一個架構概念。 架構定義您可以用來鎖定特定平台的 API。 .NET Framework 4.6 即為其中一個平台。 這些架構會在 Visual Studio 以及其他 IDE 和編輯器中使用，以提供您正確的 API 集合。 它們也可供 NuGet 使用 (用於 NuGet 套件的生產和使用)，以確保您產生及使用的是適用於目標架構的套件 (及基礎資產)。 您可以將架構想成是 .NET 生態系統的主要貨幣。 有了正確的概念後，可協助您及您的客戶在執行時避免收到 @System.MissingMethodException 及其類似的例外狀況。

## <a name="framework-versions"></a>架構版本

下表定義一組您可以使用的架構、其參考方式，以及其實作的 [.NET 標準程式庫](library.md)版本。

| 架構 | 最新的版本 | 目標 Framework Moniker (TFM) | Compact 目標 Framework Moniker (TFM) | .NET Standard 版本 | 中繼套件 |
|:--------: | :--: | :--: | :--: | :--: | :--: | :--: |
| .NET Standard | 1.6 | .NETStandard,Version=1.6 | netstandard1.6 | N/A | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library)|
| .NET Core 應用程式 | 1.0.1 | .NETCoreApp,Version=1.0 | netcoreapp1.0 | 1.6 | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App)|
| .NET Framework | 4.6.2 | .NETFramework,Version=4.6.2 | net462 | 1.5 | N/A |

> [!NOTE]
> 這些架構版本是最新穩定版本。 也可能有此表格所未描述的發行前版本。

## <a name="writing-about-frameworks"></a>撰寫架構

您可以使用多種方式以書面格式來參考架構，大多數已在本文件中使用。 其說明如下，除了作為解譯文件的說明，也可輔助用於其他文件。

以 .NET Framework 4.6.1 為例，您可以使用下列格式：

**參考產品**

您可以參考 .NET 平台或執行階段。

- ".NET Framework 4.6.1"

**參考架構**

您可以使用完整格式或簡短形式的 TFM，來參考架構或架構的目標。 在一般情況下，這兩者同樣有效。

- `.NETFramework,Version=4.6.1`
- `net461`

**參考一系列的架構**

您可以使用完整格式或簡短形式的架構識別碼，來參考一系列的架構。 在一般情況下，這兩者同樣有效。

- `.NETFramework`
- `net`



<!--HONumber=Nov16_HO1-->


