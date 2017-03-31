---
title: "in (泛型修飾詞) (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: 17
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
ms.openlocfilehash: b6c490d14b47aaa527fe2ddb3627ea0a84bfe604
ms.lasthandoff: 03/13/2017

---
# <a name="in-generic-modifier-c-reference"></a>in (泛型修飾詞) (C# 參考)
若為泛型型別參數，`in` 關鍵字會指定型別參數是 Contravariant。 您可以在泛型介面及委派中使用 `in` 關鍵字。  
  
 反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。 這可隱含轉換實作 variant 介面的類別和隱含轉換委派類型。 參考型別支援在泛型型別參數中使用共變數和反變數，但實值型別則不支援。  
  
 如果類型只用作方法引數類型，而不用作方法傳回型別，則可以在泛型介面或委派中宣告為 Contravariant。 `Ref` 和 `out` 參數不可以是變數。  
  
 具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。 例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 是 Contravariant，所以您可以不使用任何特殊的轉換方法，將 `IComparer(Of Person)` 類型的物件指派給 `IComparer(Of Employee)` 類型的物件 (如果 `Employee` 繼承 `Person`)。  
  
 您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。  
  
 如需詳細資訊，請參閱 [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) (共變數和反變數)。  
  
## <a name="example"></a>範例  
 下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。 它也會示範如何針對實作此介面的類別使用隱含轉換。  
  
 [!code-cs[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a>範例  
 下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。 它也會示範如何以隱含方式轉換委派類型。  
  
 [!code-cs[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)   
 [Covariance and Contravariance](http://msdn.microsoft.com/library/a58cc086-276f-4f91-a366-85b7f95f38b8) (共變數和反變數)   
 [修飾詞](../../../csharp/language-reference/keywords/modifiers.md)
