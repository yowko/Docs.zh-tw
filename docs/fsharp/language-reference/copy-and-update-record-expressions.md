---
title: 複製和更新記錄運算式
description: 瞭解如何編寫複製現有記錄或匿名記錄、更新指定欄位以及返回更新的記錄或匿名記錄的"複製和更新表達式」。
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739279"
---
# <a name="copy-and-update-record-expressions"></a>複製和更新記錄運算式

*複製和更新記錄表達式*是複製現有記錄、更新指定欄位並返回更新的記錄的運算式。

## <a name="syntax"></a>語法

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>備註

預設情況下,記錄和匿名記錄是不可變的,因此無法更新現有記錄。 要創建更新的記錄,必須再次指定記錄的所有欄位。 為了簡化此工作,可以使用*複製與更新表示式*。 此表示式採用現有記錄,使用運算式中的指定欄位和表示式指定的缺失欄位創建新的相同類型。

當您必須複製現有記錄並可能更改某些欄位值時,這非常有用。

例如,以新創建的記錄為例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

要僅更新該紀錄中的兩個字段,可以使用*複製和更新記錄表示式*:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>另請參閱

- [記錄](records.md)
- [匿名記錄](anonymous-records.md)
- [F# 語言參考](index.md)
