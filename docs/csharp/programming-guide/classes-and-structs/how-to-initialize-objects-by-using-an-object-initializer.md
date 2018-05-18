---
title: 如何：使用物件初始設定式初始化物件 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 1f5f068cd8dc3787eb8cb2cd72cc30e9ea159390
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>如何：使用物件初始設定式初始化物件 (C# 程式設計手冊)
您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。  
  
 下列範例示範如何搭配具名物件使用物件初始設定式。 編譯器會先存取預設執行個體建構函式，再處理成員初始化，來處理物件初始設定式。 因此，如果預設建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。  
  
 如果您要定義匿名型別，則必須使用物件初始設定式。 如需詳細資訊，請參閱[如何：在查詢中傳回項目屬性的子集](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。  
  
 [!code-csharp[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用集合初始設定式，來初始化 `StudentName` 類型的集合。 請注意，集合初始設定式是一系列以逗號分隔的物件初始設定式。  
  
 [!code-csharp[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將該類別複製並貼到已在 Visual Studio 中建立的 Visual C# 主控台應用程式專案。  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
