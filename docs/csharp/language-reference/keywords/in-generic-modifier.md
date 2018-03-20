---
title: "in (泛型修飾詞) (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2af4e27034af0067e81a52c81991edaf5a5415d8
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2018
---
# <a name="in-generic-modifier-c-reference"></a>in (泛型修飾詞) (C# 參考)

若為泛型型別參數，`in` 關鍵字會指定型別參數是 Contravariant。 您可以在泛型介面及委派中使用 `in` 關鍵字。  
  
 反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。 這可隱含轉換實作 variant 介面的類別和隱含轉換委派類型。 參考型別支援在泛型型別參數中使用共變數和反變數，但實值型別則不支援。  
  
 只有當某一類型會定義方法參數的類型，且並非為方法的傳回類型時，才可在泛型介面或委派中，將類型宣告為 Contravariant。 `In`、`ref` 及 `out` 參數不得變更，這表示它們都不會是 covariant 或 contravariant。
  
 具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。 例如，在 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 為 Contravariant，所以您可以不使用任何特殊的轉換方法，即能將 `IComparer<Person>` 類型的物件指派給 `IComparer<Employee>` 類型的物件 (如果 `Employee` 繼承 `Person`)。  
  
 您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。  
  
 如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。  
  
## <a name="contravariant-generic-interface"></a>Contravariant 泛型介面   

 下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。 它也會示範如何針對實作此介面的類別使用隱含轉換。  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a>Contravariant 泛型委派  

 下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。 它也會示範如何以隱含方式轉換委派類型。  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [共變數和反變數](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)  
