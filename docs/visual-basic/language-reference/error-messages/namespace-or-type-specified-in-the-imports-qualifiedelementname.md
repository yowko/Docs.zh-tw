---
title: Imports '<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 8675d9c3b202200c89e12e7a5f51a19d9e3e0e64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409461"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>Imports '\<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型

匯入 ' ' 中指定的命名空間或類型 \<qualifiedelementname> 不包含任何 public 成員，或找不到。 請確定已定義命名空間或類型，而且包含至少一個公用成員。 請確定別名名稱不包含其他別名。

`Imports`語句指定了找不到或未定義任何成員的包含元素 `Public` 。

*包含元素*可以是命名空間、類別、結構、模組、介面或列舉。 包含的元素包含成員，例如變數、程式或其他包含專案。

匯入的目的是要讓您的程式碼可以存取命名空間或類型成員，而不需要限定它們。 您的專案可能也需要加入命名空間或類型的參考。 如需詳細資訊，請參閱宣告專案[參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「匯入包含元素」。

如果編譯器找不到指定的包含元素，就無法解析使用它的參考。 如果找到專案，但元素並未公開任何 `Public` 成員，則不會有任何參考成功。 在任一情況下，匯入元素都沒有意義。

請記住，如果您匯入包含專案，並為其指派匯入別名，則無法使用該匯入別名來匯入另一個元素。 下列程式碼會產生編譯器錯誤。

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

**錯誤識別碼：** BC40056

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 確認可從您的專案存取包含的元素。

2. 確認包含元素的規格不包含來自另一個匯入的任何匯入別名。

3. 請確認包含的元素至少會公開一個 `Public` 成員。

## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (.NET 命名空間和類型)](../statements/imports-statement-net-namespace-and-type.md)
- [Namespace 陳述式](../statements/namespace-statement.md)
- [公開](../modifiers/public.md)
- [Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
