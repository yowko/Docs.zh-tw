---
title: .NET Core 版本歷程記錄
description: 請參閱 .NET Core 執行階段、.NET Core SDK、C# 編譯器和 VB.NET 編譯器的版本時間軸。
ms.date: 07/26/2018
ms.openlocfilehash: 90fd4ba57620a3a005f2148c0335a76a6fa54a30
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42936641"
---
# <a name="net-core-version-history"></a>NET Core 版本歷程記錄

判斷 .NET Core 的版本號碼非常困難，因為 .NET Core SDK 和 .NET Core Runtime 是以不同的步調發行的。 不同的步調表示小組只能進行下列三項行為中的其中兩項：

1. 獨立發行，並特別讓工具、C# 和 VB 的進展速度比 .NET Core Runtime 更快。
2. 校準 .NET Core SDK 和 .NET Core Runtime 間的版本號碼。
3. 針對 .NET Core SDK 和 .NET Core Runtime 使用語意式版本設定。

2.0.0 曾強制校準版本，並順暢地繼續前進一個版本。 2017 年 12 月，.NET Core SDK 發行了新功能，但在 .NET Core Runtime 中卻沒有對應的版本。 小組選擇了目標 1 和 3，遺失 .NET Core Runtime 和 SDK 間的校準。 在 .NET Core Runtime 2.1 之前已發行過數個 .NET Core SDK 2.1.x 版本。 因為 SDK 與先前本版本不相容，這些 2.1.x SDK 版本無法瞄準 .NET Core Runtime 2.1。 為了回應極度混淆狀況，小組又切換至目標 1 和 2，放棄 [.NET Core 版本設定](index.md#versioning-details)中描述的語意式版本設定。

由於決定放棄語意式版本設定時機的關係，在 2.1.10x 和 2.1.20x 版本號碼範圍間也有無法瞄準 .NET Core Runtime 2.1 的轉換期版本。

版本號碼的前兩個數字與 .NET Core Runtime 的 2.1.0 版本和 .NET Core SDK 的 2.1.300 版本重新校準。

您可以在 [.NET Core downloads page](https://www.microsoft.com/net/download/dotnet-core/current) (.NET Core 下載頁面) 上找到個別元件版本的相關資訊，包括架構及語言編譯器版本。 如需先前版本的詳細資訊，請從 [.NET Core download archives page](https://www.microsoft.com/net/download/archives) (.NET Core 下載封存頁面) 選取要求的版本。 您可以在描述正式 [.NET Support Policy](https://www.microsoft.com/net/Support/Policy) (.NET 支援原則) 的文章中找到詳細的支援資訊。