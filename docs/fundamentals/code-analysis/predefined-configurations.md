---
title: '預先定義的設定檔 (程式碼分析) '
description: 瞭解如何使用預先定義的 editorconfig 和規則集檔案，以特定類型的程式碼分析為目標。
ms.date: 09/24/2020
ms.topic: conceptual
ms.openlocfilehash: 4937dcab1183fa3f63be4afc71627a7c7c08c6bd
ms.sourcegitcommit: 665f8fc55258356f4d2f4a6585b750c974b26675
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2020
ms.locfileid: "96586219"
---
# <a name="predefined-configuration-files"></a>預先定義的設定檔

預先定義的 EditorConfig 和 [規則集](/visualstudio/code-quality/using-rule-sets-to-group-code-analysis-rules) 檔案可讓您快速且輕鬆地啟用類別的程式碼品質規則，例如安全性或設計規則。 藉由啟用特定類別的規則，您可以識別目標問題和特定條件。 若要存取這些預先定義的檔案，請安裝 [CodeAnalysis NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) NuGet analyzer 套件。

[CodeAnalysis. NetAnalyzers](https://github.com/dotnet/roslyn-analyzers#microsoftcodeanalysisnetanalyzers) 包含預先定義的 EditorConfig 檔案和規則集，適用于下列規則類別：

- 所有規則
- 資料流程
- 設計
- 文件
- 全球化
- 互通性
- 可維護性
- 命名
- 效能
- 從 FxCop 移植
- 可靠性
- 安全性
- 使用方式

每個規則類別都有 EditorConfig 或規則集檔案，以：

- 啟用類別 (中的所有規則，並停用所有其他規則) 
- 使用每個規則的預設嚴重性，並預設為啟用 (並停用所有其他規則) 

> [!TIP]
> 「所有規則」類別具有其他 EditorConfig 或規則集檔案，以停用所有規則。 使用此檔案可快速清除專案中的任何分析器警告或錯誤。

## <a name="predefined-editorconfig-files"></a>預先定義的 EditorConfig 檔案

CodeAnalysis. NetAnalyzers analyzer 套件的預先定義 EditorConfig 檔位於安裝 NuGet 套件的 *EditorConfig* 子目錄中。 例如，啟用所有安全性規則的 EditorConfig 檔案位於 *EditorConfig/SecurityRulesEnabled/EditorConfig*。

將所選的 *editorconfig* 檔案複製到您專案的根目錄。

## <a name="predefined-rule-sets"></a>預先定義的規則集

適用于 CodeAnalysis. NetAnalyzers 分析器套件的預先定義規則集檔案，位於安裝 NuGet 套件的 [ *規則* 集] 子目錄中。 例如，用來啟用所有安全性規則的規則集檔案位於 [規則集] */[SecurityRulesEnabled*]。 複製一或多個規則集，並將其貼到包含專案的目錄中。

## <a name="see-also"></a>另請參閱

- [分析器設定](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md)
- [適用于 EditorConfig 的 .NET 程式碼樣式規則選項](code-style-rule-options.md)
