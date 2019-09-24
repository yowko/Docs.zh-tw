---
title: 類別中的 let 繫結
description: 瞭解如何使用類別定義中的「let」 F#系結，定義類別的私用欄位和私用函式。
ms.date: 05/16/2016
ms.openlocfilehash: 1366ab8f1f4f606fe5947a8fc4df10de49346b3e
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216525"
---
# <a name="let-bindings-in-classes"></a>類別中的 let 繫結

您可以使用`let`類別定義中的系結F# ，定義類別的私用欄位和私用函式。

## <a name="syntax"></a>語法

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>備註

先前的語法會出現在類別標題和繼承宣告之後，但在任何成員定義之前。 語法類似于`let`類別外的系結，但是在類別中定義的名稱具有限制為類別的範圍。 `let`系結會建立私用欄位或函式; 若要公開資料或函數，請宣告屬性或成員方法。

不是靜態的系結稱為「實例系`let`結」（instance binding）。 `let` 建立`let`物件時，會執行實例系結。 靜態`let`系結是類別之靜態初始化運算式的一部分，保證會在第一次使用型別之前執行。

實例`let`系結中的程式碼可以使用主要的函式的參數。

類別中的系結不允許`let`屬性和存取範圍修飾詞。

下列程式碼範例說明類別中的`let`數種系結類型。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

輸出如下。

```console
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>建立欄位的替代方式

您也可以使用`val`關鍵字來建立私用欄位。 使用`val`關鍵字時，不會在建立物件時指定欄位的值，而是使用預設值來初始化。 如需詳細資訊, [請參閱明確欄位:Val 關鍵字](explicit-fields-the-val-keyword.md)。

您也可以使用成員定義來定義類別中的私用欄位，並將關鍵字`private`新增至定義。 如果您想要變更成員的存取範圍，而不需要重寫程式碼，這會很有用。 如需詳細資訊，請參閱[存取控制](../access-control.md)。

## <a name="see-also"></a>另請參閱

- [成員](index.md)
- [類別中的 `do` 繫結](do-bindings-in-classes.md)
- [`let`關係](../functions/let-bindings.md)
