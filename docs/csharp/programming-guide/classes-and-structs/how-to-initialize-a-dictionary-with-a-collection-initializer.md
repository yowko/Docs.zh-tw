---
title: "如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)
<xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> 方法會採用兩個參數，一個針對索引鍵，另一個針對值。 若要初始化 <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` 方法採用多個參數的任何集合，請將每個參數集以括號括住，如下列範例所示。  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName` 的執行個體進行初始化。  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 請注意，該集合的每個項目中都有兩組括號。 最內層的括號會括住 `StudentName` 的物件初始設定式，最外層的括號會括住機碼值組，這組值會新增至 `students`<xref:System.Collections.Generic.Dictionary`2>。 最後，會以括號括住目錄的整個集合初始設定式。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將該類別複製並貼到 [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] 中所建立的 Visual C# 主控台應用程式專案。 根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。 如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
