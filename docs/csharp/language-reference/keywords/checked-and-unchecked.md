---
title: Checked 與 Unchecked (C# 參考)
ms.date: 05/15/2018
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
ms.openlocfilehash: 04f603905690497bcd4249f73c7296be2c269a60
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43741928"
---
# <a name="checked-and-unchecked-c-reference"></a>Checked 與 Unchecked (C# 參考)
C# 陳述式可在 checked 或 unchecked 內容中執行。 在 checked 內容中，算術溢位會引發例外狀況。 在未經檢查的內容中，會忽略算術溢位，並捨棄目的型別不適用的高序位位元，以便將結果截斷。  
  
-   [checked](checked.md) 指定 checked 內容。  
  
-   [unchecked](unchecked.md) 指定 unchecked 內容。  
  
 溢位檢查會影響下列作業：  
  
-   在整數類型上使用下列預先定義之運算子的運算式：  
  
     `++`、`--`、一元 `-`、`+`、`-`、`*`、`/`  
  
-   整數型別之間的明確數值轉換，或從 `float` 或 `double` 轉換為整數型別。  
  
 如果未指定 `checked` 和 `unchecked`，則非常數運算式 (在執行階段所評估的運算式) 的預設內容由 [-checked](../compiler-options/checked-compiler-option.md) 編譯器選項的值所定義。 根據預設，該選項的值是 unset，且算術運算在未經檢查的內容中執行。
 
 針對常數運算式 (可以在編譯時期完整評估的運算式)，一律會檢查預設內容。 除非將一個常量表達式顯式放置在未經檢查的上下文中，否則在對該表達式進行編譯時評估期間發生的溢出會導致編譯時錯誤。
  
## <a name="see-also"></a>請參閱  

- [C# 參考](../index.md)  
- [C# 程式設計指南](../../programming-guide/index.md)  
- [C# 關鍵字](index.md)  
- [陳述式關鍵字](statement-keywords.md)
