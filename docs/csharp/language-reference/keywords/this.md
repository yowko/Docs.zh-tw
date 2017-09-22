---
title: "this (C# 參考)"
description: "this 關鍵字 (C# 參考)"
keywords: "this (C#), this 關鍵字 (C#), this 關鍵字 (C# 參考), this 關鍵字 (C# 語言參考)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
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
ms.openlocfilehash: 1e764bbd85d06a3b1898f6574064b2844f6d6813
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="this-c-reference"></a>this (C# 參考)
`this` 關鍵字指的是類別的目前執行個體，也用作擴充方法第一個參數的修飾詞。  
  
> [!NOTE]
>  本文討論如何搭配使用 `this` 與類別執行個體。 如需其在擴充方法中之用法的詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  
  
 下列是 `this` 的常見用法：  
  
-   限定透過類似名稱所隱藏的成員，例如︰  
  
 [!code-cs[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   傳遞物件作為其他方法的參數，例如：  
  
    ```  
    CalcTax(this);  
    ```  
  
-   宣告索引子，例如︰  
  
 [!code-cs[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 靜態成員函式存在於類別層級，而不是物件的一部分，因此沒有 `this` 指標。 在靜態方法中參照 `this` 會產生錯誤。  
  
## <a name="example"></a>範例  
 在此範例中，`this` 是用來限定 `Employee` 類別成員 `name` 和 `alias`，而這些是透過類似的名稱進行隱藏。 它也會用來將物件傳遞給屬於另一個類別的 `CalcTax` 方法。  
  
 [!code-cs[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [base](../../../csharp/language-reference/keywords/base.md)   
 [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)

