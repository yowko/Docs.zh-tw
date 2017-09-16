---
title: "參考類型 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.referencetypes
dev_langs:
- CSharp
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
caps.latest.revision: 15
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
ms.openlocfilehash: ed7b9c8ed4aa1136c09049c8ffd6c68beeeb2a48
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="reference-types-c-reference"></a>參考類型 (C# 參考)
C# 中有兩種類型：參考類型和實值類型。 參考類型的變數會儲存期資料 (物件) 的參考，而實值類型的變數則會直接包含其資料。 使用參考類型時，這兩種變數可以參考相同的物件，因此對其中一個變數進行的作業可能會影響另一個變數所參考的物件。 使用實值型別時，每個變數都有自己的資料複本，因此在某一個變數上進行的作業不可能會影響其他變數 (但 ref 和 out 參數變數除外，請參閱 [ref](../../../csharp/language-reference/keywords/ref.md) 和 [out 參數修飾詞](../../../csharp/language-reference/keywords/out-parameter-modifier.md))。  
  
 下列關鍵字用來宣告參考類型：  
  
-   [class](../../../csharp/language-reference/keywords/class.md)  
  
-   [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   [delegate](../../../csharp/language-reference/keywords/delegate.md)  
  
 C# 還提供下列內建參考類型：  
  
-   [dynamic](../../../csharp/language-reference/keywords/dynamic.md)  
  
-   [object](../../../csharp/language-reference/keywords/object.md)  
  
-   [string](../../../csharp/language-reference/keywords/string.md)  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [類型](../../../csharp/language-reference/keywords/types.md)   
 [實值型別](../../../csharp/language-reference/keywords/value-types.md)

