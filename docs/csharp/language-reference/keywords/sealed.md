---
title: sealed 修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: babad3b07c5faea1381e6af13d3c713122de2332
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235172"
---
# <a name="sealed-c-reference"></a>sealed (C# 參考)

套用至類別時，`sealed` 修飾詞可防止其他類別繼承自它。 在下列範例中，`B` 類別繼承自 `A`類別，但類別無法繼承自 `B` 類別。

```csharp
class A {}
sealed class B : A {}
```

您也可以在方法或屬性上使用可覆寫基底類別中虛擬方法或屬性的 `sealed` 修飾詞。 這可讓您允許類別衍生自您的類別，並防止它們覆寫特定虛擬方法或屬性。

## <a name="example"></a>範例

在下列範例中，`Z` 繼承自 `Y`，但 `Z` 無法覆寫宣告於 `X` 並密封於 `Y` 的虛擬函式 `F`。

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

當您在類別中定義新方法或屬性時，可以不將這些方法或屬性宣告為 [virtual](virtual.md)，以防止衍生類別覆寫它們。

搭配使用 [abstract](abstract.md) 修飾詞與 sealed 類別會產生錯誤，因為提供 abstract 方法或屬性實作的類別必須繼承 abstract 類別。

套用至方法或屬性時，`sealed` 修飾詞必須一律與 [override](override.md) 搭配使用。

結構會隱含地進行密封，因此無法進行繼承。

如需詳細資訊，請參閱[繼承](../../programming-guide/classes-and-structs/inheritance.md)。

如需更多範例，請參閱[抽象和密封類別以及類別成員](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)。

## <a name="example"></a>範例

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

在上述範例中，您可以嘗試使用下列陳述式從 sealed 類別繼承︰

`class MyDerivedC: SealedClass {}   // Error`

結果是錯誤訊息：

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a>C# 語言規格

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a>備註

若要判斷是否密封類別、方法或屬性，您通常應該考慮下列兩點︰

- 衍生類別的潛在優點可能是透過類別自訂功能所取得。

- 衍生類別可能會修改您的類別，因此它們無法再正確運作或如預期運作。

## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](index.md)
- [靜態類別和靜態類別成員](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [抽象和密封類別以及類別成員](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [存取修飾詞](../../programming-guide/classes-and-structs/access-modifiers.md)
- [修飾詞](modifiers.md)
- [override](override.md)
- [virtual](virtual.md)