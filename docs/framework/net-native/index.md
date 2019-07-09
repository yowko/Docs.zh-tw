---
title: 使用 .NET Native 編譯應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d295d0b35b4b93425c825f75857881a2e2ddc57
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660896"
---
# <a name="compiling-apps-with-net-native"></a>使用 .NET Native 編譯應用程式

.NET native 是隨附於 Visual Studio 2015 和更新版本的先行編譯技術來建置和部署 Windows 應用程式。 此工具可將以 Managed 程式碼 (C# 或 Visual Basic) 撰寫且目標為 .NET Framework 和 Windows 10 的應用程式發行版本自動編譯為機器碼。

一般而言，以 .NET Framework 為目標的應用程式會編譯成中繼語言 (IL)。 在執行階段，just-in-time (JIT) 編譯器會將 IL 轉譯成機器碼。 相反地，.NET Native 編譯 Windows 應用程式，直接以原生程式碼。 對開發人員而言，這表示：

- 您的應用程式功能的原生程式碼的效能。 通常，效能將會優先於第一次編譯成 IL 並由 JIT 編譯器編譯成原生程式碼的程式碼。

- 您可以繼續以 C# 或 Visual Basic 進行程式設計。

- 您可以繼續利用 .NET Framework 所提供的資源，包括其類別庫、自動記憶體管理和記憶體回收，以及例外狀況處理。

您的應用程式的使用者，.NET Native，請提供下列優點：

- 大部分的應用程式與案例可更快速的執行時間。

- 對於大部分的應用程式與案例的啟動時間更快。

- 低的部署和更新成本。

- 最佳化應用程式記憶體使用量。

> [!IMPORTANT]
> 針對絕大部分的應用程式和案例中，.NET 原生提供明顯更快的啟動時間和更優異的效能，相較於應用程式編譯成 IL 或 NGEN 映像。 不過，您的結果可能不同。 若要確保您的應用程式，受益的.NET 原生的效能增強功能，您應該比較它與您的應用程式的非-.NET 原生版本的效能。 如需詳細資訊，請參閱 <<c0> [ 效能工作階段概觀](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview)。

但.NET 原生需要超過原生程式碼編譯。 它會將轉換 .NET Framework 應用程式建置和執行的方式。 特別之處在於：

- 在預先編譯期間，.NET Framework 的必要部分會以靜態方式連結到您的應用程式。 這樣可以讓應用程式以 .NET Framework 的 app-local 程式庫來執行，並且讓編譯器執行全域分析，以提供優異的效能。 如此一來，即使 .NET Framework 更新之後，應用程式還是一貫地會以更快的速度啟動。

- .NET Native 的執行階段已針對靜態預先編譯最佳化，並在大部分情況下提供更優異的效能。 同時，它還保留了開發人員會覺得生產力極佳的核心反映功能。

- .NET 原生使用相同的後端，為C++編譯器，並已針對靜態預先編譯案例最佳化。

.NET native 是能夠使效能優勢C++至 managed 程式碼開發人員，因為它會使用相同或類似工具C++在幕後，如本表所示。

||.NET Native|C++|
|-|----------------------------------------------------------------|-----------|
|程式庫|.NET Framework + Windows 執行階段|Win32 + Windows 執行階段|
|編譯器|UTC 最佳化編譯器|UTC 最佳化編譯器|
|已部署|可立即執行的二進位檔案|可立即執行的二進位檔案 (ASM)|
|執行階段|MRT.dll (最小 CLR 執行階段)|CRT.dll (C 執行階段)|

針對適用於 Windows 10 的 Windows 應用程式，您要將應用程式封裝 (.appx 檔) 中的 .NET 機器碼編譯二進位檔上傳至 Windows 市集。

## <a name="in-this-section"></a>本節內容

如需有關使用 .NET 機器碼編譯來開發應用程式的詳細資訊，請參閱下列主題：

- [開始使用.NET Native 機器碼編譯：開發人員經驗逐步解說](../../../docs/framework/net-native/getting-started-with-net-native.md)

- [.NET native 和編譯：](../../../docs/framework/net-native/net-native-and-compilation.md)如何.NET Native 編譯原生程式碼專案。

- [反映和 .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)

  - [依賴反映的 API](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)

  - [反映 API 參考](../../../docs/framework/net-native/net-native-reflection-api-reference.md)

  - [執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)

- [序列化和中繼資料](../../../docs/framework/net-native/serialization-and-metadata.md)

- [將您的 Windows 市集應用程式移轉至 .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

- [針對 .NET Native 進行疑難排解](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
