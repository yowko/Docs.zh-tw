---
title: In （泛型修飾詞）-Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004877"
---
# <a name="in-generic-modifier-visual-basic"></a>In (泛型修飾詞) (Visual Basic)

若為泛型型別參數，`In` 關鍵字會指定型別參數是 Contravariant。

## <a name="remarks"></a>備註

反變數可讓您使用比泛型參數指定的衍生程度更低的衍生類型。 這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。

如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。

## <a name="rules"></a>規則

您可以在泛型介面及委派中使用 `In` 關鍵字。
  
如果型別參數僅做為方法引數的型別，而不當做方法的傳回型別使用，則可以在泛型介面或委派中宣告為逆變。 `ByRef` 參數不可以是協變數或逆變性。

參考型別支援共變數和反變數，而實數值型別則不支援。

在 Visual Basic 中，您不能在不指定委派類型的情況下，于逆變性介面中宣告事件。 此外，逆變性介面不能有嵌套的類別、列舉或結構，但它們可以有嵌套介面。

## <a name="behavior"></a>行為

具有 Contravariant 型別參數的介面可讓其方法接受衍生程度低於介面型別參數指定之衍生類型的引數。 例如，因為在 .NET Framework 4 中，在 <xref:System.Collections.Generic.IComparer%601> 介面中，類型 T 是逆變的，您可以將 `IComparer(Of Person)` 類型的物件指派給 `IComparer(Of Employee)` 類型的物件，而不需使用任何特殊轉換方法（如果 `Employee` 繼承自 `Person`）。

您可以將類型相同但具有衍生程度較低之泛型型別參數的另一個委派指派給 Contravariant 委派。

## <a name="example---contravariant-generic-interface"></a>範例-逆變性泛型介面

下例範例示範如何宣告、擴充及實作 Contravariant 泛型介面。 它也會示範如何針對實作此介面的類別使用隱含轉換。

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a>範例-逆變性泛型委派

下例範例示範如何宣告、具現化及叫用 Contravariant 泛型委派。 它也會示範如何以隱含方式轉換委派類型。

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a>另請參閱

- [泛型介面中的變異數](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Out](out-generic-modifier.md)
