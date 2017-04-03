---
title: "如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 60443456be4b4fbb13dad6cb9c372a1af332c2fd
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)
<xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> 方法會採用兩個參數，一個針對索引鍵，另一個針對值。 若要初始化 <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add` 方法採用多個參數的任何集合，請將每個參數集以括號括住，如下列範例所示。  
  
## <a name="example"></a>範例  
 在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName` 的執行個體進行初始化。  
  
 [!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 請注意，該集合的每個項目中都有兩組括號。 最內層的括號會括住 `StudentName` 的物件初始設定式，最外層的括號會括住機碼值組，這組值會新增至 `students`<xref:System.Collections.Generic.Dictionary`2>。 最後，會以括號括住目錄的整個集合初始設定式。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將該類別複製並貼到 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] 中所建立的 Visual C# 主控台應用程式專案。 根據預設，此專案是以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。 如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。   
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [物件和集合初始設定式](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
