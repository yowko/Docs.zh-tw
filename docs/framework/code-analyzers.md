---
title: .NET Framework 的程式碼分析器
titleSuffix: ''
description: 瞭解如何使用 .NET Framework 分析器套件中的分析器，找出並解決程式碼中的問題。
author: billwagner
ms.author: wiwagn
ms.date: 10/23/2020
ms.openlocfilehash: 69dfbc9f9645c7f602ffbce46308b241c119fd96
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687844"
---
# <a name="code-analysis"></a>程式碼分析

您可以使用程式碼分析器找出 .NET Framework 應用程式程式碼中的潛在問題。 分析器會找出潛在的問題，並為其提供建議的修正程式。

以 Roslyn 為基礎的程式碼分析器會在您撰寫程式碼時以互動方式在 Visual Studio 中執行，或作為 CI 組建的一部分執行。 您應儘早在開發週期中將分析器新增至專案。 在程式碼中找到任何潛在問題的速度愈快，修正就愈容易。 分析器會標示現有程式碼中的問題，並在您繼續開發時警告新問題。

## <a name="install-and-configure-analyzers"></a>安裝和設定分析器

[Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet 套件提供 .NET Framework Analyzer。 此套件提供 .NET Framework Api 專屬的分析器，包括安全性分析器。 套件隨附于 [CodeAnalysis. 將 microsoft.codeanalysis.fxcopanalyzers 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)，因此，如果您安裝該套件，則不需要個別安裝 .NET Framework 分析器。

在您想要執行分析器的每個專案上安裝 NuGet 套件。 只有一位開發人員必須將它們新增至專案。 分析器套件是一種專案相依性，而且會在具有已更新方案之後，於每位開發人員的電腦上執行。

若要安裝套件，請在專案上按一下滑鼠右鍵，然後選取 [管理相依性]。 從 NuGet explorer 搜尋 ".Netframework"。 在您方案的所有專案中安裝最新穩定版本。

## <a name="use-the-analyzers"></a>流量分析器

安裝 NuGet 套件之後，請建置方案。 分析器將會報告它在您的程式碼基底中找到的任何問題。 在 Visual Studio [錯誤清單] 視窗中，這些問題回報為警告，如下圖所示：

![.NET Framework 分析器回報的問題。](./media/framework-analyzers-2.png)

當您撰寫程式碼時，會在程式碼的任何潛在問題下方看到曲線。
將滑鼠停留在任何問題上以取得詳細資訊，並查看任何可能修正的建議，如下列影像所示：

![程式碼分析器發現的互動式問題報表。](./media/framework-analyzers-1.png)

如需詳細資訊，請參閱 [Visual Studio 中的程式碼分析](/visualstudio/code-quality/roslyn-analyzers-overview)。

## <a name="types-of-rules"></a>規則類型

分析器會檢查方案中的程式碼，並以前置詞呈現警告 `CA` 。 如需所有可能警告的清單，請參閱程式 [代碼品質規則](../fundamentals/code-analysis/quality-rules/index.md)。 只有部分警告適用于 .NET Framework 的 API，包括：

- [CA1058:類型不應該擴充特定基底類型](../fundamentals/code-analysis/quality-rules/ca1058.md)

- [CA2153：不要攔截損毀狀態例外](../fundamentals/code-analysis/quality-rules/ca2153.md)

- [CA2229:必須實作序列化建構函式](../fundamentals/code-analysis/quality-rules/ca2229.md)

- [CA2235:必須標記所有不可序列化的欄位](../fundamentals/code-analysis/quality-rules/ca2235.md)

- [CA2237：必須以可序列化標記 ISerializable 類型](../fundamentals/code-analysis/quality-rules/ca2237.md)

- [CA3075：XML 中的不安全 DTD 處理](../fundamentals/code-analysis/quality-rules/ca3075.md)

- [CA5350：請勿使用弱式密碼編譯演算法](../fundamentals/code-analysis/quality-rules/ca5350.md)

- [CA5351 不使用中斷的密碼編譯演算法](../fundamentals/code-analysis/quality-rules/ca5351.md)

## <a name="see-also"></a>請參閱

- [Visual Studio 中的程式碼分析](/visualstudio/code-quality/roslyn-analyzers-overview)
- [.NET SDK 中的程式碼分析](../fundamentals/code-analysis/overview.md)
