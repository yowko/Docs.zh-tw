---
title: Imports '<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 284a8c71fee8835f78ca5435932819fded1b1f30
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160128"
---
# <a name="bc40056-namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>BC40056： Imports ' ' 中指定的命名空間或類型 \<qualifiedelementname> 不包含任何 public 成員，或找不到

Imports ' ' 中指定的命名空間或類型 \<qualifiedelementname> 不包含任何 public 成員，或找不到。 請確定命名空間或類型已定義，而且至少包含一個公用成員。 請確定別名名稱不包含其他別名。

`Imports`語句指定的包含專案找不到或未定義任何 `Public` 成員。

*包含元素*可以是命名空間、類別、結構、模組、介面或列舉。 包含的專案包含成員，例如變數、程式或其他包含元素。

匯入的目的是要讓您的程式碼存取命名空間或類型成員，而不需限定它們。 您的專案可能也需要加入命名空間或類型的參考。 如需詳細資訊，請參閱宣告專案 [參考](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)中的「匯入包含的元素」。

如果編譯器找不到指定的包含元素，則無法解析使用它的參考。 如果它找到元素，但元素未公開任何 `Public` 成員，則不會成功參考。 在任一種情況下，匯入元素沒有意義。

請記住，如果您匯入包含的專案，並將匯入別名指派給它，就不能使用該匯入別名來匯入另一個元素。 下列程式碼會產生編譯器錯誤。

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

**錯誤識別碼：** BC40056

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 確認可從專案存取包含的元素。

2. 確認包含元素的規格不包含來自另一個匯入的任何匯入別名。

3. 確認包含的元素至少會公開一個 `Public` 成員。

## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (.NET 命名空間和類型)](../statements/imports-statement-net-namespace-and-type.md)
- [Namespace 陳述式](../statements/namespace-statement.md)
- [公用](../modifiers/public.md)
- [Visual Basic 中的命名空間](../../programming-guide/program-structure/namespaces.md)
- [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
