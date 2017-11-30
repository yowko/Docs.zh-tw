---
title: "In (泛型修飾詞) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e9aab4fc361754cfd750ae68f04b36dce13d0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-visual-basic"></a>In (泛型修飾詞) (Visual Basic)
若為泛型型別參數，`In` 關鍵字會指定型別參數是 Contravariant。  
  
## <a name="remarks"></a>備註  
 反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。 這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。  
  
 如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。  
  
## <a name="rules"></a>規則  
 您可以在泛型介面及委派中使用 `In` 關鍵字。  
  
 如果它是只當做方法引數的型別，而且並未當做方法的傳回型別，型別參數可以宣告 contravariant 的泛型介面或委派中。 `ByRef`參數不能為 covariant 或 contravariant。  
  
 共變數和反變數參考類型和支援值型別不支援。  
  
 在 Visual Basic 中，您無法宣告但未指定委派類型的 contravariant 介面中的事件。 此外，類別、 列舉或結構，contravariant 介面不能有巢狀，但可以有巢狀介面。  
  
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
 [泛型介面中的變異數](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Out](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
