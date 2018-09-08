---
title: 類別中的 let 繫結 (F#)
description: "了解如何在類別定義中使用 'let' 的繫結來定義私用欄位和 F # 類別的私用函式。"
ms.date: 05/16/2016
ms.openlocfilehash: 237eb98a57571a21c9187abf31f05160374cf4fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186015"
---
# <a name="let-bindings-in-classes"></a>類別中的 let 繫結

您可以定義私用欄位和 F # 類別的私用函式使用`let`類別定義中的繫結。

## <a name="syntax"></a>語法

```fsharp
// Field.
[static] let [ mutable ] binding1 [ and ... binding-n ]

// Function.
[static] let [ rec ] binding1 [ and ... binding-n ]
```

## <a name="remarks"></a>備註

類別標題和繼承宣告之後，但任何成員定義之前，會顯示先前的語法。 語法是類似`let`類別，但在類別中定義的名稱以外的繫結需要僅限於此類別的範圍。 A`let`繫結會建立私用欄位或函式; 將資料公開或公開，函式宣告的屬性或成員方法。

A`let`繫結，不是靜態的執行個體稱為`let`繫結。 執行個體`let`繫結執行建立物件時。 靜態`let`繫結是執行之前先使用的型別類別的靜態初始設定式的一部分。

執行個體中的程式碼`let`繫結可以使用主要建構函式參數。

上不允許屬性和存取範圍修飾詞`let`類別中的繫結。

下列程式碼範例將說明數種`let`類別中的繫結。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3001.fs)]

輸出如下。

```
10 52 1 204
```

## <a name="alternative-ways-to-create-fields"></a>若要建立欄位的替代方式

您也可以使用`val`關鍵字來建立私用欄位。 當使用`val`關鍵字，欄位未指定值，當物件建立時，但改為使用預設值初始化。 如需詳細資訊，請參閱 <<c0> [ 明確欄位： val 關鍵字](explicit-fields-the-val-keyword.md)。

您也可以定義類別中私用欄位，藉由使用成員定義，以及加入關鍵字`private`的定義。 這可以是成員的很有用，如果您預期要變更存取範圍，而不需要重新撰寫程式碼。 如需詳細資訊，請參閱[存取控制](../access-control.md)。

## <a name="see-also"></a>另請參閱

- [成員](index.md)
- [類別中的 `do` 繫結](do-bindings-in-classes.md)
- [`let` 繫結](../functions/let-bindings.md)
