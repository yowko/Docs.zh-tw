---
title: Checked 與 Unchecked (C# 參考)
ms.date: 07/20/2015
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 26ea8a7864d93b8d64661db2b0dc1df6634f989a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="checked-and-unchecked-c-reference"></a>Checked 與 Unchecked (C# 參考)
C# 陳述式可在 checked 或 unchecked 內容中執行。 在 checked 內容中，算術溢位會引發例外狀況。 在 unchecked 內容中，會忽略算術溢位並截斷結果。  
  
-   [checked](../../../csharp/language-reference/keywords/checked.md) 指定 checked 內容。  
  
-   [unchecked](../../../csharp/language-reference/keywords/unchecked.md) 指定 unchecked 內容。  
  
 如果未指定 `checked` 或 `unchecked`，預設內容會取決於編譯器選項等外部因素。  
  
 溢位檢查會影響下列作業：  
  
-   在整數類型上使用下列預先定義之運算子的運算式：  
  
     `++` `--` - (一元)   `+` -   `*` `/`  
  
-   整數類型之間的明確數值轉換。  
  
 [/checked](../../../csharp/language-reference/compiler-options/checked-compiler-option.md) 編譯器選項可讓您針對明確不在 `checked` 或 `unchecked` 關鍵字範圍中的所有整數算術陳述式，指定 checked 或 unchecked 內容。  
  
## <a name="see-also"></a>請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [陳述式關鍵字](../../../csharp/language-reference/keywords/statement-keywords.md)
