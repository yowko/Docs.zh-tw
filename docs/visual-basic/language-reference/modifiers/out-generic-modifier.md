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

若為泛型型別參數，`Out` 關鍵字會指定型別為「協變數」。

## <a name="remarks"></a>備註

共變數可讓您使用比泛型參數指定的衍生程度更高的衍生型別。 這可隱含轉換實作 variant 介面的類別和隱含轉換委派類型。

如需詳細資訊，請參閱 [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md) (共變數和反變數 (C# 和 Visual Basic))。

## <a name="rules"></a>規則

您可以在泛型介面及委派中使用 `Out` 關鍵字。

在泛型介面中，型別參數如果滿足下列條件即可宣告為 Covariant︰

- 型別參數僅用為介面方法的傳回型別，不用為方法引數的型別。

    > [!NOTE]
    > 這個規則只有一個例外。 如果您在 Covariant 介面中以 Contravariant 泛型委派作為方法參數，則可將 Covariant 型別用為此委派的泛型型別參數。 如需 Covariant 和 Contravariant 泛型委派的詳細資訊，請參閱 [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) (委派中的變異數) 和 [Using Variance for Func and Action Generic Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md) (針對 Func 與 Action 委派使用變異數)。

- 型別參數不是用為介面方法的泛型條件約束。

在泛型委派中，如果型別參數僅做為方法傳回型別使用，而不是用於方法引數，則可以宣告為「不可變」。

參考型別支援共變數和反變數，但實值型別不支援它們。

在 Visual Basic 中，您不能在不指定委派類型的情況下，于協變數介面中宣告事件。 此外，協變數介面不能有嵌套的類別、列舉或結構，但它們可以有嵌套介面。

## <a name="behavior"></a>行為

具有 Covariant 型別參數的介面可讓其方法傳回的衍生型別，衍生程度高過型別參數指定的衍生型別。 例如，因為在 .NET Framework 4 的 <xref:System.Collections.Generic.IEnumerable%601> 中，T 類型是 Covariant，所以您可以不使用任何特殊的轉換方法，將 `IEnumerable(Of String)` 類型的物件指派給 `IEnumerable(Of Object)` 類型的物件。

Covariant 委派可以指派給同型別的另一個委派，但具有衍生程度較大的泛型型別參數。

## <a name="example"></a>範例

下例會示範如何宣告、擴充及實作 Covariant 泛型介面。 它也會示範如何針對實作 Covariant 介面的類別使用隱含轉換。

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>範例

下例會示範如何宣告、具現化及叫用 Covariant 泛型委派。 它也會說明如何使用委派類型的隱含轉換。

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>請參閱

- [泛型介面中的變異數](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
