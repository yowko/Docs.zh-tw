---
title: Imports '<qualifiedelementname>' 中指定的命名空間或類型不包含任何 Public 成員，或是找不到該命名空間或類型
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: 1873c0af7a251afd7754557f5dcb6aed13eb9f11
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357881"
---
# <a name="namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a>中的匯入的命名空間或類型指定\<完整項目名稱 >' 不包含任何 public 成員，或是找不到

中的匯入的命名空間或類型指定\<完整項目名稱 >' 不包含任何 public 成員，或是找不到。 請確定命名空間或類型定義，而且包含至少一個 public 成員。 請確定別名名稱不包含其他別名。

`Imports`陳述式會指定包含的項目不能找到，或未定義任何`Public`成員。

A*包含項目的*可以是命名空間、 類別、 結構、 模組、 介面或列舉型別。 包含的項目包含成員，例如變數、 程序或其他內含項目。

匯入的目的是允許您存取命名空間或類型成員的程式碼，而不必加以限定。 若要加入的命名空間或類型的參考，可能也需要您的專案。 如需詳細資訊，請參閱 < 匯入包含項目 」 中[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。

如果編譯器找不到指定的包含項目，所以無法解析使用它的參考。 如果它找到的項目，但項目不會公開任何`Public`成員，則任何參考可成功。 在任一情況下它是無意義的匯入之項目的項目。

請記住，如果您匯入包含項目，並將匯入別名指派給它，則您無法使用該匯入別名匯入另一個項目。 下列程式碼會產生編譯器錯誤。

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

**錯誤 ID:** BC40056

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 請確認包含的項目是從您的專案存取。

2. 請確認包含的項目規格不會包含從另一個匯入任何匯入別名。

3. 請確認包含的項目會公開至少一個`Public`成員。

## <a name="see-also"></a>另請參閱

- [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [Namespace 陳述式](../../../visual-basic/language-reference/statements/namespace-statement.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [在 Visual Basic 中的命名空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)
- [對已宣告項目的參考](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
