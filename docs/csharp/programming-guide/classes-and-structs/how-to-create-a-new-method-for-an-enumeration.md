---
title: "如何：建立列舉的新方法 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- enumerations [C#]
- extension methods [C#], for enums
- enum extensibility [C#]
ms.assetid: 100106f9-1e54-462c-8ebe-3892fe23b6eb
caps.latest.revision: 7
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
ms.openlocfilehash: 3d15cbcdd81584ea5c6ab40d231183f883a7a805
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-new-method-for-an-enumeration-c-programming-guide"></a>如何：建立列舉類型的新方法 (C# 程式設計手冊)
您可以使用擴充方法來新增專屬於特定列舉類型的功能。  
  
## <a name="example"></a>範例  
 在下例中，`Grades` 列舉代表班上學生可能得到的字母分級成績。 已將名為 `Passing` 的擴充方法新增至 `Grades` 類型，以便該類型的每個執行個體現在都「知道」它是否代表傳遞等級。  
  
 [!code-cs[csProgGuideExtensionMethods#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-create-a-new-method-for-an-enumeration_1.cs)]  
  
 請注意，`Extensions` 類別也包含動態更新的靜態變數，以及反映該變數目前值的擴充方法傳回值。 本例示範，在幕後直接對定義所在的靜態類別叫用擴充方法。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 若要執行此程式碼，請將它複製並貼至已在 [!INCLUDE[vs_current_short](../../../csharp/programming-guide/classes-and-structs/includes/vs_current_short_md.md)] 中建立的 Visual C# 主控台應用程式專案。 根據預設，此專案是以 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 `using` 指示詞。 如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。   
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
