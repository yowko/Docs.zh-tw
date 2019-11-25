---
title: In (泛型修飾詞)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 0460015b44971fa638dba47183690ffcc89ca55f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351428"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (泛型修飾詞) (Visual Basic)

For generic type parameters, the `Out` keyword specifies that the type is covariant.

## <a name="remarks"></a>備註

共變數可讓您使用比泛型參數指定的衍生程度更高的衍生型別。 這可隱含轉換實作 Variant 介面的類別和隱含轉換委派型別。

如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數)。

## <a name="rules"></a>規則

您可以在泛型介面及委派中使用 `Out` 關鍵字。

在泛型介面中，型別參數如果滿足下列條件即可宣告為 Covariant︰

- 型別參數僅用為介面方法的傳回型別，不用為方法引數的型別。

    > [!NOTE]
    > 這個規則只有一個例外。 如果您在 Covariant 介面中以 Contravariant 泛型委派作為方法參數，則可將 Covariant 型別用為此委派的泛型型別參數。 如需 Covariant 和 Contravariant 泛型委派的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) (委派中的變異數) 和 [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md) (針對 Func 與 Action 委派使用變異數)。

- 型別參數不是用為介面方法的泛型條件約束。

In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.

參考型別支援共變數和反變數，但實值型別不支援它們。

In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type. Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.

## <a name="behavior"></a>行為

具有 Covariant 型別參數的介面可讓其方法傳回的衍生型別，衍生程度高過型別參數指定的衍生型別。 例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，T 類型是 Covariant，所以您可以不使用任何特殊的轉換方法，將 `IEnumerable(Of String)` 類型的物件指派給 `IEnumerable(Of Object)` 類型的物件。

Covariant 委派可以指派給同型別的另一個委派，但具有衍生程度較大的泛型型別參數。

## <a name="example"></a>範例

下例會示範如何宣告、擴充及實作 Covariant 泛型介面。 它也會示範如何針對實作 Covariant 介面的類別使用隱含轉換。

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>範例

下例會示範如何宣告、具現化及叫用 Covariant 泛型委派。 It also shows how you can use implicit conversion for delegate types.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>請參閱

- [泛型介面中的變異數](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
