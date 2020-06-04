---
title: 如何：指派一個陣列至另一個陣列
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, arrays
- arrays [Visual Basic], assigning
- arrays [Visual Basic], covariance
ms.assetid: 1ae89ea5-f292-4282-bcfc-e9b06b37fbd5
ms.openlocfilehash: c38def1ba9f3720bc760d6f6e4264510c884c930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413075"
---
# <a name="how-to-assign-one-array-to-another-array-visual-basic"></a>如何：指派一個陣列至另一個陣列 (Visual Basic)

因為陣列是物件，所以您可以在類似其他物件類型的指派語句中使用它們。 陣列變數會保存構成陣列元素的資料指標和排名和長度資訊，而指派只會複製此指標。

### <a name="to-assign-one-array-to-another-array"></a>若要將一個陣列指派給另一個陣列

1. 請確定這兩個數組具有相同的 rank （維度數目）和相容的元素資料類型。

2. 使用標準指派語句，將來源陣列指派給目的陣列。 請勿在陣列名稱稱後面加上括弧。

    ```vb
    Dim formArray() As System.Windows.Forms.Form
    Dim controlArray() As System.Windows.Forms.Control
    controlArray = formArray
    ```

當您將陣列指派給另一個陣列時，適用下列規則：

- **相等順位。** 目的陣列的順位（維度數目）必須與來源陣列的等級相同。

  假設兩個數組的次序相等，則維度不需要相等。 指定維度中的元素數目可能會在指派期間變更。

- **元素類型。** 這兩個數組都必須有*參考型別*元素，或這兩個數組都必須具有實*數值型別*元素。 如需詳細資訊，請參閱 [Value Types and Reference Types](../data-types/value-types-and-reference-types.md)。

  - 如果這兩個數組都具有實數值型別專案，則元素資料類型必須完全相同。 唯一的例外是您可以將元素的陣列指派 `Enum` 給該的基底類型陣列 `Enum` 。

  - 如果這兩個數組都有參考型別專案，則來源元素類型必須衍生自目的地元素類型。 當發生這種情況時，這兩個數組與其元素具有相同的繼承關係。 這稱為「*陣列共變數*」。

如果違反上述規則，則編譯器會報告錯誤，例如，如果資料類型不相容，或次序不相等。 您可以將錯誤處理新增至程式碼，以確保陣列相容，然後再嘗試指派。 如果您想要避免擲回例外狀況，也可以使用[TryCast Operator](../../../language-reference/operators/trycast-operator.md)關鍵字。

## <a name="see-also"></a>另請參閱

- [陣列](index.md)
- [針對陣列進行疑難排解](troubleshooting-arrays.md)
- [End 陳述式](../../../language-reference/statements/enum-statement.md)
- [陣列轉換](../data-types/array-conversions.md)
