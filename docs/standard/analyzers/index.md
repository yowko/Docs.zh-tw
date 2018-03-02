---
title: "Roslyn 分析器 - .NET"
description: "了解可找出問題並針對問題提供建議的 Roslyn 分析器相關資訊。"
keywords: .NET, .NET Core
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 8c6524716ba403bc426df8dc33e64b8b2934d3d7
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2018
---
# <a name="the-roslyn-based-analyzers"></a>Roslyn 分析器

Roslyn 分析器會使用 .NET Compiler SDK (Roslyn API) 來分析您專案的原始程式碼，以找出問題並建議修正。 不同的分析器會尋找不同類別的問題，範圍從可能導致錯誤 (bug) 的作法，以及安全性考量與 API 相容性等等。

Roslyn 分析器能夠以互動方式運作，也可以在建置期間運作。 當在 Visual Studio 或命令列組建中時，分析器會提供不同的指引。

在 Visual Studio 中編輯程式碼時，分析器會在您進行變更時執行，並在您建立會引發顧慮的程式碼時立刻攔截可能的問題。 任何問題底下都會以波浪線來突顯。 Visual Studio 會顯示燈泡，當您按一下燈泡時，分析器會針對該問題建議可能的修正。 當您建置專案時，不論在 Visual Studio 中或從命令列，都將會分析所有的原始程式碼，且分析器會提供潛在問題的完整清單。 下圖將示範一個範例。

![架構分析器回報的問題](./media/framework-analyzers-2.png)

根據問題的嚴重性，Roslyn 分析器會將潛在問題回報為錯誤、警告或資訊。

在您的專案中，您可以 NuGet 套件來安裝 Roslyn 分析器。 這會還原已設定的分析器以及各個分析器的所有設定，並在任何開發人員電腦上為該專案執行。

> [!NOTE]
> Roslyn 分析器的使用者體驗有別於「程式碼分析」程式庫 (例如舊版 FxCop 和安全性分析工具)。  您不需要明確地執行 Roslyn 分析器。 不需要使用 Visual Studio 中 [分析] 功能表上的 [執行程式碼分析] 功能表項目。 Roslyn 分析器會在您工作時以非同步方式執行。 

## <a name="more-information-on-specific-analyzers"></a>特定分析器的詳細資訊

此章節將討論下列分析器：

[API 分析器](api-analyzer.md)：此分析器會在您的程式碼中檢查潛在的相容性風險，或者檢查程式碼中是否使用已被取代的 API。    
[架構分析器](framework-analyzer.md)：此分析器會檢查您的程式碼，以確保程式碼遵循適用於 .NET Framework 應用程式的指導方針。 這些規則包含數個安全性建議。
