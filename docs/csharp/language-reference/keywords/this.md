---
title: this (C# 參考)
description: this 關鍵字 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: df1bf6a3e6d24b231bf5e3c7a960f49084c4e53a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48026564"
---
# <a name="this-c-reference"></a>this (C# 參考)
`this` 關鍵字指的是類別的目前執行個體，也用作擴充方法第一個參數的修飾詞。  
  
> [!NOTE]
>  本文討論如何搭配使用 `this` 與類別執行個體。 如需其在擴充方法中之用法的詳細資訊，請參閱[擴充方法](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)。  
  
 下列是 `this` 的常見用法：  
  
-   限定透過類似名稱所隱藏的成員，例如︰  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   傳遞物件作為其他方法的參數，例如：  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   宣告索引子，例如︰  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 靜態成員函式存在於類別層級，而不是物件的一部分，因此沒有 `this` 指標。 在靜態方法中參照 `this` 會產生錯誤。  
  
## <a name="example"></a>範例  
 在此範例中，`this` 是用來限定 `Employee` 類別成員 `name` 和 `alias`，而這些是透過類似的名稱進行隱藏。 它也會用來將物件傳遞給屬於另一個類別的 `CalcTax` 方法。  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱

- [C# 參考](../../../csharp/language-reference/index.md)  
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
- [base](../../../csharp/language-reference/keywords/base.md)  
- [方法](../../../csharp/programming-guide/classes-and-structs/methods.md)
