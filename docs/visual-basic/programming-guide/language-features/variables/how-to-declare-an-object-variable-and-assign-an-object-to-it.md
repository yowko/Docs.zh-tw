---
title: 如何：宣告物件變數並指派物件給它
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
ms.openlocfilehash: d9a8c1fb30bfa5988d48202e41202e7ede0f5f27
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410499"
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>如何：在 Visual Basic 中宣告物件變數，並指派物件給它

您可以[Object Data Type](../../../language-reference/data-types/object-data-type.md) `As Object` 在[Dim 語句](../../../language-reference/statements/dim-statement.md)中指定，以宣告 Object 資料類型的變數。 將物件放 `=` 在指派語句或初始化子句中的等號（）後面，即可將物件指派給這類變數。

## <a name="example"></a>範例

下列範例會宣告一個 `Object` 變數，並將目前的實例指派給它。

```vb
Dim thisObject As Object
thisObject = "This is an Object"
```

您可以將變數初始化為其宣告的一部分，藉此結合宣告和指派。 下列範例相當於上述範例。

```vb
Dim thisObject As Object= "This is an Object"
```

## <a name="compile-the-code"></a>編譯程式碼

這個範例需要：

- <xref:System> 命名空間的參考。

- 要在其中放置語句的類別、結構或模組 `Dim` 。

- 要在其中放置指派語句的程式。

## <a name="see-also"></a>另請參閱

- [變數宣告](variable-declaration.md)
- [物件變數](object-variables.md)
- [物件變數宣告](object-variable-declaration.md)
- [Object Data Type](../../../language-reference/data-types/object-data-type.md)
- [Dim 陳述式](../../../language-reference/statements/dim-statement.md)
- [區域型別推斷](local-type-inference.md)
- [Long](../../../language-reference/statements/option-strict-statement.md)
