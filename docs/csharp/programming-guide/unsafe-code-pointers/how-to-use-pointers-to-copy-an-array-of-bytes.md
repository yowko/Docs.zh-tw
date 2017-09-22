---
title: "如何：使用指標複製位元組陣列 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: 21
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
ms.openlocfilehash: 808a74f75e4dcbcec47735d98063138e2c7456e5
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：使用指標複製位元組陣列 (C# 程式設計手冊)
下列範例會使用指標在陣列之間複製位元組。  
  
 這個範例使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，可讓您在 `Copy` 方法中使用指標。  [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式是用於宣告指向來源和目標陣列的指標。  這會「*固定*」\(Pin\) 來源和目的地陣列在記憶體中的位置，如此一來就不會因記憶體回收而移動。  陣列的記憶體區塊會在 `fixed` 區塊完成時解除固定狀態。  由於這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，因此必須使用 **\/unsafe** 編譯器選項進行編譯。  若要在 Visual Studio 中設定選項，以滑鼠右鍵按一下專案名稱，然後按一下 \[**屬性**\]。  在 \[**建置**\] 索引標籤上，選取 \[**容許 Unsafe 程式碼**\]。  
  
## 範例  
 [!code-cs[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-cs[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)   
 [/unsafe (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)   
 [記憶體回收](../../../standard/garbage-collection/index.md)

