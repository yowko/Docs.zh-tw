---
title: In (泛型修飾詞) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 4d5909e6ee7436b7e4f7baa30bfe81eb8ba5441e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625742"
---
# <a name="in-generic-modifier-visual-basic"></a>In (泛型修飾詞) (Visual Basic)
若為泛型型別參數，`In` 關鍵字會指定型別參數是 Contravariant。  
  
## <a name="remarks"></a>備註  
 反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。 這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。  
  
 如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。  
  
## <a name="rules"></a>規則  
 您可以在泛型介面及委派中使用 `In` 關鍵字。  
  
 如果它是僅為方法引數的型別，不用為方法的傳回型別，類型參數可以宣告 contravariant 泛型介面或委派中。 `ByRef` 參數不可以是共變性或逆變性。  
  
 共變性與逆變性是參考型別支援和不支援的實值型別。  
  
 在 Visual Basic 中，您無法宣告 contravariant 介面中的事件，而不指定委派類型。 此外，類別、 列舉或結構，contravariant 介面不能有巢狀，但可以有巢狀介面。  
  
## <a name="behavior"></a>行為  
 具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。 例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 是 Contravariant，所以您可以不使用任何特殊的轉換方法，將 `IComparer(Of Person)` 類型的物件指派給 `IComparer(Of Employee)` 類型的物件 (如果 `Person` 繼承 `Employee`)。  
  
 您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。  
  
## <a name="example"></a>範例  
 下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。 它也會示範如何針對實作此介面的類別使用隱含轉換。  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a>範例  
 下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。 它也會示範如何以隱含方式轉換委派類型。  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>另請參閱
- [泛型介面中的變異數](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
