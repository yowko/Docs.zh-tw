---
title: '複製和更新記錄運算式 （F #）'
description: 了解如何撰寫 '複製和更新記錄運算式'，複製現有的記錄，更新指定的欄位，並傳回更新的記錄。
author: ChrSteinert
ms.date: 06/04/2016
ms.openlocfilehash: d2b089e8a7fc5c7ee26139003e23d2eaa8a3174e
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44494066"
---
# <a name="copy-and-update-record-expressions"></a>複製和更新記錄運算式

A*複製並更新記錄運算式*是複製現有的記錄、 更新指定的欄位，並傳回更新的資料錄的運算式。

## <a name="syntax"></a>語法

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>備註

使其沒有可能不會更新現有的記錄，記錄會依預設，不可變。 若要建立已更新的資料錄的一筆記錄的所有欄位必須指定一次。 若要簡化這項工作*複製並更新記錄運算式*可用。 這個運算式會採用現有的記錄，使用運算式指定的欄位和運算式所指定的遺漏欄位會建立一個新的同一個型別。
當您必須複製現有的記錄，並可能變更的某些欄位值時，這非常有用。

需要執行個體的新建立的記錄。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

如果您只在您可以使用該記錄的欄位更新*複製並更新記錄運算式*如下所示：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>另請參閱

- [記錄](records.md)
- [F# 語言參考](index.md)
