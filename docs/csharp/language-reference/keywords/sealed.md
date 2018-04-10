---
title: sealed (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8248b451f0431286fdaba3583fc2031eb6cdbcd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="sealed-c-reference"></a>sealed (C# 參考)
套用至類別時，`sealed` 修飾詞可防止其他類別繼承自它。 在下列範例中，`B` 類別繼承自 `A`類別，但類別無法繼承自 `B` 類別。  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 您也可以在方法或屬性上使用可覆寫基底類別中虛擬方法或屬性的 `sealed` 修飾詞。 這可讓您允許類別衍生自您的類別，並防止它們覆寫特定虛擬方法或屬性。  
  
## <a name="example"></a>範例  
 在下列範例中，`Z` 繼承自 `Y`，但 `Z` 無法覆寫宣告於 `X` 並密封於 `Y` 的虛擬函式 `F`。  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 當您在類別中定義新方法或屬性時，可以不將這些方法或屬性宣告為 [virtual](../../../csharp/language-reference/keywords/virtual.md)，以防止衍生類別覆寫它們。  
  
 搭配使用 [abstract](../../../csharp/language-reference/keywords/abstract.md) 修飾詞與 sealed 類別會產生錯誤，因為提供 abstract 方法或屬性實作的類別必須繼承 abstract 類別。  
  
 套用至方法或屬性時，`sealed` 修飾詞必須一律與 [override](../../../csharp/language-reference/keywords/override.md) 搭配使用。  
  
 結構會隱含地進行密封，因此無法進行繼承。  
  
 如需詳細資訊，請參閱[繼承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)。  
  
 如需更多範例，請參閱[抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。  
  
## <a name="example"></a>範例  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 在上述範例中，您可以嘗試使用下列陳述式從 sealed 類別繼承︰  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 結果是錯誤訊息：  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a>備註  
 若要判斷是否密封類別、方法或屬性，您通常應該考慮下列兩點︰  
  
-   衍生類別的潛在優點可能是透過類別自訂功能所取得。  
  
-   衍生類別可能會修改您的類別，因此它們無法再正確運作或如預期運作。  
  
## <a name="see-also"></a>另請參閱  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [靜態類別和靜態類別成員](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [抽象和密封類別以及類別成員](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [存取修飾詞](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)
