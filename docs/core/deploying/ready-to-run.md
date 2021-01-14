---
title: ReadyToRun 部署總覽
description: 瞭解什麼是 ReadyToRun 部署，以及為什麼您應該考慮在使用 .NET 5 和 .NET Core 3.0 和更新版本發行應用程式時使用它。
author: davidwr
ms.author: davidwr
ms.date: 09/21/2020
ms.openlocfilehash: 3302e5e18a20965a1eff1f09737910e924ed6d08
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188604"
---
# <a name="readytorun-compilation"></a>ReadyToRun 編譯

將您的應用程式元件編譯為 ReadyToRun (R2R) 格式，即可改善 .NET 應用程式啟動時間和延遲。 R2R 是一種預先(AOT) 編譯。

R2R 二進位檔會透過減少 Just-In-Time (JIT) 編譯器在應用程式載入時所需執行的工作量，來改善啟動效能。 二進位檔包含的機器碼，與 JIT 所會產生的內容類似。 但是，R2R 二進位檔大小較大，因為它們會同時包含中繼語言 (IL) 程式碼 (在某些案例下仍需要使用)，以及相同程式碼的原生版本。 只有當您發佈以特定執行時間環境為目標的應用程式時，才可使用 R2R， (RID) 例如 Linux x64 或 Windows x64。

若要將您的專案編譯為 ReadyToRun，必須將 PublishReadyToRun 屬性設定為來發行應用程式 `true` 。

有兩種方式可以將您的應用程式發佈為 ReadyToRun：

01. 直接指定 dotnet publish 命令的 PublishReadyToRun 旗標。 如需詳細資訊，請參閱 [dotnet publish](../tools/dotnet-publish.md) 。

    ```dotnetcli
    dotnet publish -c Release -r win-x64 -p:PublishReadyToRun=true
    ```

02. 在專案中指定屬性。

    - 將 `<PublishReadyToRun>` 設定新增至您的專案。

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

    - 發佈沒有任何特殊參數的應用程式。

    ```dotnetcli
    dotnet publish -c Release -r win-x64
    ```

## <a name="impact-of-using-the-readytorun-feature"></a>使用 ReadyToRun 功能的影響

預先編譯會對應用程式效能造成複雜的效能影響，這可能很難預測。 一般情況下，元件的大小會增加到兩到三倍以上。 檔案的實體大小增加可能會降低從磁片載入元件的效能，並增加進程的工作集。 不過，在執行時間編譯的方法數目通常會大幅減少。 結果是，大部分的應用程式都有大量的程式碼可獲得 ReadyToRun 的大型效能優勢。 由於 .NET 執行時間程式庫已經使用 ReadyToRun 先行編譯，因此具有少量程式碼的應用程式可能不會遇到大幅改進而無法啟用 ReadyToRun。

此處所討論的啟始改進不僅適用于應用程式啟動，也適用于應用程式中的任何程式碼首次使用。 比方說，ReadyToRun 可以用來減少在 ASP.NET 應用程式中第一次使用 Web API 時的回應延遲。

### <a name="interaction-with-tiered-compilation"></a>與分層式編譯的互動

預先產生的程式碼並不像 JIT 所產生的程式碼一樣高度優化。 為了解決這個問題，階層式編譯會以 JIT 產生的方法取代常用的 ReadyToRun 方法。

## <a name="how-is-the-set-of-precompiled-assemblies-chosen"></a>如何選擇預先編譯的元件集？

SDK 將會先行編譯隨應用程式散發的元件。 若為獨立應用程式，這組元件將包含架構。 C + +/CLI 二進位檔不符合 ReadyToRun 編譯的資格。

## <a name="how-is-the-set-of-methods-to-precompile-chosen"></a>如何選擇預先編譯的一組方法？

編譯器會嘗試預先編譯的方法越多。 但基於各種原因，使用 ReadyToRun 功能將無法讓 JIT 執行。 這類原因可能包括但不限於：

- 使用在個別元件中定義的泛型型別。
- 使用機器碼進行 Interop。
- 使用編譯器無法證明的硬體內建函式可以安全地在目的電腦上使用。
- 某些不尋常的 IL 模式。
- 透過反映或 LINQ 建立動態方法。

## <a name="cross-platformarchitecture-restrictions"></a>跨平台/架構限制

針對某些 SDK 平臺，ReadyToRun 編譯器可以跨平臺編譯其他目標平臺。 下表說明支援的編譯目標。

| SDK 平台 | 支援的目標平台 |
| ------------ | --------------------------- |
| Windows X64  | Windows X86、Windows X64、Windows ARM32、Windows ARM64 |
| Windows X86  | Windows X86、Windows ARM32 |
| Linux X64    | Linux X86、Linux X64、Linux ARM32、Linux ARM64 |
| Linux ARM32  | Linux ARM32 |
| Linux ARM64  | Linux ARM64 |
| macOS X64    | macOS X64 |
