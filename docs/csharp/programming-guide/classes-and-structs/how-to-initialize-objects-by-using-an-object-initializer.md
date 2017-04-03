---
title: "如何：使用物件初始設定式初始化物件 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
caps.latest.revision: 20
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9d6537332b4ddcca185a0ac3039a925e0b3fcef2
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a>如何：使用物件初始設定式初始化物件 (C# 程式設計手冊)
您可以使用物件初始設定式以宣告方式初始化類型物件，而不需要明確叫用該類型的建構函式。  
  
 下列範例示範如何搭配具名物件使用物件初始設定式。 編譯器會先存取預設執行個體建構函式，再處理成員初始化，來處理物件初始設定式。 因此，如果預設建構函式在類別中宣告為 `private`，需要公用存取的物件初始設定式將會失敗。  
  
 如果您要定義匿名型別，則必須使用物件初始設定式。 如需詳細資訊，請參閱[如何：在查詢中傳回項目屬性的子集](../../../csharp/programming-guide/classes-and-structs/how-to-return-subsets-of-element-properties-in-a-query.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用物件初始設定式，來初始化新的 `StudentName` 類型。  
  
 [!code-cs[csProgGuideLINQ#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_1.cs)]  
  
## <a name="example"></a>範例  
 下列範例示範如何使用集合初始設定式，來初始化 `StudentName` 類型的集合。 請注意，集合初始設定式是一系列以逗號分隔的物件初始設定式。  
  
 [!code-cs[csProgGuideLINQ#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-objects-by-using-an-object-initializer_2.cs)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將該類別複製並貼到 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 中所建立的 Visual C# 主控台應用程式專案。   
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
