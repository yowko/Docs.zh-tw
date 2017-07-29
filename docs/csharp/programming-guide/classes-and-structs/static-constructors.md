---
title: "靜態建構函式 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- static constructors [C#]
- constructors [C#], static
ms.assetid: 151ec95e-3c4d-4ed7-885d-95b7a3be2e7d
caps.latest.revision: 23
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
ms.openlocfilehash: 73df76c61f393bf5fe09af66935acfbac4b5663f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="static-constructors-c-programming-guide"></a>靜態建構函式 (C# 程式設計手冊)
靜態建構函式用來初始化任何 [static](../../../csharp/language-reference/keywords/static.md) 資料，或執行只需要執行一次的特定動作。 在建立第一個執行個體或參考任何靜態成員之前，會自動進行呼叫。  
  
 [!code-cs[csProgGuideObjects#14](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_1.cs)]  
  
 靜態建構函式具有下列屬性：  
  
-   靜態建構函式不會接受存取修飾詞，也不會包含參數。  
  
-   系統會在建立第一個執行個體或參考任何靜態成員之前，自動呼叫靜態建構函式來初始化 [class](../../../csharp/language-reference/keywords/class.md)。  
  
-   靜態建構函式不能直接呼叫。  
  
-   使用者無法控制在程式中執行靜態建構函式的時間。  
  
-   靜態建構函式的一般用法為：當類別正在使用記錄檔，且建構函式用來將項目寫入這個檔案時。  
  
-   如果建構函式可以呼叫 `LoadLibrary` 方法，靜態建構函式在建立 unmanaged 程式碼的包裝函式類別時也很有用。  
  
-   如果靜態建構函式擲回例外狀況，執行階段不會叫用它第二次，而類型會在執行程式的應用程式定義域的存留期內保持未初始化。  
  
## <a name="example"></a>範例  
 在此範例中，`Bus` 類別具有靜態建構函式。 建立 `Bus` 的第一個執行個體 (`bus1`) 時，即會叫用靜態建構函式來初始化類別。 範例輸出可確認即使建立了兩個 `Bus` 執行個體，靜態建構函式也只執行一次，而且它是在執行個體建構函式執行之前執行。  
  
 [!code-cs[csProgGuideObjects#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/static-constructors_2.cs)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [類別和結構](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [建構函式](../../../csharp/programming-guide/classes-and-structs/constructors.md)   
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
 [完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)

