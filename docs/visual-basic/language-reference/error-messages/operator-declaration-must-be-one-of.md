---
title: 運算子宣告必須是下列其中一個： +,-, *,-,-, ^、 &amp; 、Like、Mod、And、Or、Xor、Not、 <<、 >>、=、 <>、<、<=、>、>=、CType、IsTrue、IsFalse
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: a94e62e33427987a302a6244b2b8ce8d295e4f11
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159894"
---
# <a name="bc33000-operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a>BC33000：運算子宣告必須是下列其中一個： +,-, *、 \, /、^、 &amp; 、Like、Mod、And、Or、Xor、Not、 \<\<, >> .。。

您只能宣告有資格進行多載的運算子。 下表列出您可以宣告的運算子。

|類型|運算子|
|----------|---------------|
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|
|轉換 (一元)|`CType`|

 請注意， `=` 二進位清單中的運算子是比較運算子，而不是指派運算子。

 **錯誤識別碼：** BC33000

## <a name="to-correct-this-error"></a>更正這個錯誤

- 從一組可多載的運算子中選取運算子。

- 如果您需要多載無法直接多載之運算子的功能，請建立接受適當參數並傳回適當值的 `Function` 程序。

## <a name="see-also"></a>另請參閱

- [Operator Statement](../statements/operator-statement.md)
- [運算子程序](../../programming-guide/language-features/procedures/operator-procedures.md)
- [如何：定義運算子](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Function 陳述式](../statements/function-statement.md)
