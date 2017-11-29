---
title: "複製並更新記錄運算式 （F #）"
description: "了解如何撰寫 '複製並更新記錄運算式' 複製現有的記錄，更新指定的欄位，並傳回更新的記錄。"
keywords: "Visual F#, F#, 函式程式設計"
author: ChrSteinert
ms.author: phcart
ms.date: 06/04/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: b5fc4ef0-64eb-4272-96a7-bb4dffbb634a
ms.openlocfilehash: 2eb51842b678780a1d6da96e237ebb92d1ea5cec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="copy-and-update-record-expressions"></a>複製和更新記錄運算式

A*複製並更新記錄運算式*是複製現有的記錄，更新指定的欄位，並傳回更新的資料錄的運算式。


## <a name="syntax"></a>語法

```fsharp
{ record-name with
    updated-member-definitions }
```

## <a name="remarks"></a>備註
記錄是根據預設，不變的使得沒有可能不會更新現有的記錄。 若要建立更新的記錄之記錄的所有欄位必須指定一次。 為了簡化這項工作*複製並更新記錄運算式*可用。 這個運算式會採用現有的記錄，使用指定的欄位，從運算式和運算式所指定的遺漏欄位會建立一個新的相同型別。
當您必須複製現有的記錄，並可能變更的某些欄位值，這非常有用。

取得執行個體的新建立的記錄。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

如果您要更新只能在您可以使用該記錄的欄位上*複製並更新記錄運算式*像下面這樣：

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a>另請參閱
[記錄](records.md)

[F# 語言參考](index.md)
