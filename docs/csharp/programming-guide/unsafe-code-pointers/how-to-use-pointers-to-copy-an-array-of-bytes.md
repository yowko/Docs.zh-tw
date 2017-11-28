---
title: "如何：使用指標複製位元組陣列 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.assetid: ec16fbb4-a24e-45f5-a763-9499d3fabe0a
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 375cab76063e4c77515d6b05b42f2d97ff3efc44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>如何：使用指標複製位元組陣列 (C# 程式設計手冊)
下列範例會使用指標，以將位元組從某個陣列複製到另一個陣列。  
  
 這個範例會使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字，讓您可以使用 `Copy` 方法中的指標。 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) 陳述式用來宣告來源和目的陣列的指標。 這會將來源和目的陣列的位置「釘選」到記憶體中，讓記憶體回收不會移動它們。 `fixed` 區塊完成時，會取消釘選陣列的記憶體區塊。 因為這個範例中的 `Copy` 方法使用 `unsafe` 關鍵字，所以必須使用 **/unsafe** 編譯器選項進行編譯。 若要在 Visual Studio 中設定選項，請以滑鼠右鍵按一下專案名稱，然後按一下 [屬性]。 在 [建置] 索引標籤上，選取 [容許 Unsafe 程式碼]。  
  
## <a name="example"></a>範例  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#18](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-use-pointers-to-copy-an-array-of-bytes_2.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [/unsafe (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md)  
 [記憶體回收](../../../standard/garbage-collection/index.md)
