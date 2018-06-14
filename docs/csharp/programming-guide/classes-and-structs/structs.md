---
title: 結構 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, structs
- structs [C#]
ms.assetid: b7cf4ff2-0eb7-4e5c-93d5-b2196b4f5d89
ms.openlocfilehash: ffb5b8da6c72056620cf890f38af4e7a8116ab3e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322984"
---
# <a name="structs-c-programming-guide"></a>結構 (C# 程式設計手冊)
您可以使用 [struct](../../../csharp/language-reference/keywords/struct.md) 關鍵字來定義結構，例如：  
  
 [!code-csharp[csProgGuideObjects#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/structs_1.cs)]  
  
 結構與類別共用大部分相同的語法，不過結構的限制高於類別︰  
  
-   在結構宣告內，除非欄位宣告為常數或靜態，否則無法初始化欄位。  
  
-   結構無法宣告預設建構函式 (不含參數的建構函式) 或完成項。  
  
-   指派時會複製結構。 將結構指派給新的變數時，會複製所有資料，而且對新複本進行的任何修改都不會變更原始複本的資料。 使用實值型別集合 (例如 Dictionary\<string, myStruct>) 時，請一定要記住這一點。  
  
-   結構是實值型別，而類別是參考型別。  
  
-   不同於類別，結構不需要使用 `new` 運算子就能具現化。  
  
-   結構可以宣告具有參數的建構函式。  
  
-   結構無法繼承自另一個結構或類別，而且不能作為類別的基底。 所有結構都直接繼承自 `System.ValueType`，該項則繼承自 `System.Object`。  
  
-   結構可以實作介面。  
  
-   結構可用作可為 Null 的型別，並可指派 Null 值。  
  
## <a name="related-sections"></a>相關章節  
 如需詳細資訊：  
  
-   [使用結構](../../../csharp/programming-guide/classes-and-structs/using-structs.md)  
  
-   [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [可為 Null 的型別](../../../csharp/programming-guide/nullable-types/index.md)  
  
-   [如何：了解將結構和類別參考傳遞給方法之間的差異](../../../csharp/programming-guide/classes-and-structs/how-to-know-the-difference-passing-a-struct-and-passing-a-class-to-a-method.md)  
  
-   [如何：在結構之間實作使用者定義的轉換](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [類別](../../../csharp/programming-guide/classes-and-structs/classes.md)
