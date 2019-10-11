---
title: C# 參考
ms.date: 02/14/2017
helpviewer_keywords:
- Visual C#, language reference
- language reference [C#]
- Programmer's Reference for C#
- C# language, reference
- reference, C# language
ms.assetid: 06de3167-c16c-4e1a-b3c5-c27841d4569a
ms.openlocfilehash: df56287d161f7760e136eb80aa1a9171966df794
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275809"
---
# <a name="c-reference"></a>C# 參考
本節提供有關 C# 關鍵字、運算子、特殊字元、前置處理器指示詞、編譯器選項以及編譯器錯誤和警告的參考資料。  
  
## <a name="in-this-section"></a>本節內容  
 [C# 關鍵字](./keywords/index.md)  
 提供有關 C# 關鍵字和語法的資訊連結。  
  
 [C# 運算子](./operators/index.md)  
 提供有關 C# 運算子和語法的資訊連結。  

 [C# 特殊字元](./tokens/index.md)  
 提供有關 C# 中特殊內容字元及其使用方式之相關資訊的連結。  

 [C# 前置處理器指示詞](./preprocessor-directives/index.md)  
 提供有關 C# 原始程式碼內嵌之編譯器命令的資訊連結。  
  
 [C# 編譯器選項](./compiler-options/index.md)  
 包含編譯器選項及其使用方式的相關資訊。  
  
 [C# 編譯器錯誤](./compiler-messages/index.md)  
 包含示範 C# 編譯器錯誤和警告之原因和修正的程式碼片段。  
  
 [C# 語言規格](../../../_csharplang/spec/introduction.md)  
 C# 6.0 語言規格。 這是 C# 6.0 語言的草稿提案。 本檔將透過使用 ECMA C#標準委員會的方式進行精簡。 版本 5.0 已在 2017年 12 月發行為[標準 ECMA-334 第 5 版](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf) \(英文\) 文件。

語言規格提案中會說明已在 C# 6.0 之後版本中實作的功能。 這些文件會描述為了新增這些功能，而產生的語言規格差異。 這些都是草稿提案表單。 這些規格將會調整並提交給 ECMA 標準委員會，以進行正式審查，並將其合併至未來C#的標準版本。

 [C#7.0 規格提案](../../../_csharplang/proposals/csharp-7.0/pattern-matching.md)  
 C# 7.0 中實作了一些新功能。 它們包括模式比對、區域函式、out 變數宣告、擲回例外狀況、二進位常值，以及數字分隔符號。 此資料夾包含這些功能中每個功能的規格。
  
 [C#7.1 規格提案](../../../_csharplang/proposals/csharp-7.1/async-main.md)  
 C# 7.1 中有新增的功能。 首先，您可以撰寫會傳回 `Task` 或 `Task<int>`的 `Main` 方法。 這可讓您將 `async` 修飾詞新增到 `Main`。 `default` 運算式在能夠推斷類型的位置，可以不搭配類型使用。 Tuple 成員名稱也可推斷。 最後一點，模式比對可用於泛型。

 [C#7.2 規格提案](../../../_csharplang/proposals/csharp-7.2/readonly-ref.md)  
 C# 7.2 新增了數個次要功能。 您可以使用 `in` 關鍵字隨機參考，以此方式傳遞引數。 為了支援 `Span` 及相關類型的編譯時間安全性，而進行了數項細微的變更。 在某些情況下，您可在後續引數為位置引數的地方使用具名引數。 `private protected` 存取修飾詞可讓您指定呼叫者僅限於相同組件中實作的衍生類型。 `?:` 運算子可以解析成變數的參考。 您也可以使用前置的數字分隔符號來設定十六進位與二進位數字的格式。

 [C#7.3 規格提案](../../../_csharplang/proposals/csharp-7.3/blittable.md)  
 C# 7.3 是另一個包含數項次要更新的小數點版本。 您可以在泛型型別參數使用新的限制式。 另有幾項變更可讓您更輕鬆地使用 `fixed` 欄位，包括使用 [`stackalloc`](./operators/stackalloc.md) 配置。 使用 `ref` 關鍵字宣告的區域變數可以重新指派，以參考新的儲存體。 您可以將屬性放在自動實作的屬性，該屬性以編譯器產生的支援欄位為目標。 運算式變數可用於初始設定式。 Tuple 可用於比較是否相等 (或不相等)。 多載解析也有幾項功能改進。
  
 [C#8.0 規格提案](../../../_csharplang/proposals/csharp-8.0/nullable-reference-types.md)  
 C#8.0 適用 .NET Core 3.0。 這些功能包括可為 null 的參考型別、遞迴模式比對、預設介面方法、非同步資料流程、範圍和索引、使用和 using 宣告的模式、null 聯合指派，以及 readonly 實例成員。
  
## <a name="related-sections"></a>相關章節  

 [C# 指南](../index.md)  
 提供 Visual C# 文件入口網站。  
  
 [使用 C# 的 Visual Studio 開發環境](/visualstudio/get-started/csharp)  
 提供描述 IDE 和編輯器的概念和工作主題連結。  
  
 [C# 程式設計指南](../programming-guide/index.md)  
 包含如何使用 C# 程式設計語言的相關資訊。
