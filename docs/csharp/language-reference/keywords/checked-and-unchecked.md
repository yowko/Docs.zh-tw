---
title: "Checked 與 Unchecked (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- operators [C#], checked and unchecked
- exceptions [C#], overflow checking
- checked statement [C#]
- overflow checking [C#]
- unchecked statement [C#]
- statements [C#], checked and unchecked
ms.assetid: a84bc877-2c7f-4396-8735-1ce97c42f35e
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 744f59dbf7ee8370010ff76d4e9dde20490de403
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

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
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [陳述式關鍵字](../../../csharp/language-reference/keywords/statement-keywords.md)

