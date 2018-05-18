---
title: 如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: b8c44ebbdc89d72398c3380d708b45d0b7dfdad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)
<xref:System.Collections.Generic.Dictionary`2> 包含索引鍵/值組的集合。 其 <xref:System.Collections.Generic.Dictionary`2.Add*> 方法採用兩個參數，其中之一供索引鍵之用，而另一個則供值之用。 若要初始化 <xref:System.Collections.Generic.Dictionary`2> 或任何其 `Add` 方法採用多重參數的所有集合，請將每個參數集以括號括住，如下列範例所示。  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary`2> 會使用類型 `StudentName` 的執行個體進行初始化。  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 請注意，該集合的每個項目中都有兩組括號。 最內層的括號會括住 `StudentName` 的物件初始設定式，最外層的括號會括住機碼值組，這組值會新增至 `students`<xref:System.Collections.Generic.Dictionary`2>。 最後，會以括號括住目錄的整個集合初始設定式。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將該類別複製並貼到已在 Visual Studio 中建立的 Visual C# 主控台應用程式專案。 根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。 如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
