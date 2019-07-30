---
title: 複製和更新記錄運算式
description: 瞭解如何撰寫「複製和更新運算式」來複製現有的記錄或匿名記錄、更新指定的欄位, 並傳回更新的記錄或匿名記錄。
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630386"
---
# <a name="copy-and-update-record-expressions"></a>複製和更新記錄運算式

*複製和更新記錄運算式*是一個運算式, 可複製現有的記錄、更新指定的欄位, 並傳回更新的記錄。

## <a name="syntax"></a>語法

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a>備註

記錄和匿名記錄預設為不變, 因此不會有現有記錄的更新。 若要建立已更新的記錄, 必須再次指定記錄的所有欄位。 為了簡化這項工作, 可以使用*複製和更新運算式*。 這個運算式會採用現有的記錄, 使用運算式中指定的欄位和運算式所指定的遺漏欄位, 建立相同類型的新。

當您必須複製現有的記錄, 而且可能變更某些域值時, 這會很有用。

針對新建立的記錄取得實例。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

如果您只是在該記錄的欄位上更新, 您可以使用*複製和更新記錄運算式*, 如下所示:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>另請參閱

- [記錄](records.md)
- [匿名記錄](anonymous-records.md)
- [F# 語言參考](index.md)
