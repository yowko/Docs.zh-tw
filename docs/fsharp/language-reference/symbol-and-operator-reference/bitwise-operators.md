---
title: 位元運算子 (F#)
description: '深入了解 F # 程式語言中可用的位元運算子。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4d5abff564a5d1dcbe52b99edf431ca10e442061
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="bitwise-operators"></a>位元運算子

本主題說明在 F # 語言中可用的位元運算子。

## <a name="summary-of-bitwise-operators"></a>位元運算子的摘要
下表描述支援 F # 語言中的 unboxed 整數類資料類型的位元運算子。

|運算子|注意|
|--------|-----|
|`&&&`|位元 AND 運算子。 如果且只有在兩個來源運算元的對應位元為 1，結果中的位元會有 1 的值。|
|<code>&#124;&#124;&#124;</code>|位元 OR 運算子。 在結果中的位元具有值 1，如果在來源中的對應位元的運算元都是 1。|
|`^^^`|位元互斥 OR 運算子。 如果且只有來源運算元的位元有相等的值，結果中的位元會有 1 的值。|
|`~~~`|位元否定運算子。 這是一元運算子，而且產生的結果，在其中所有來源運算元中的 0 位元都轉換成 1 個位元，而所有的 1 位元會都轉換成 0 位元。|
|`<<<`|位元左移位運算子。 結果會是第一個運算元的位元移位左邊的第二個運算元的位元數。 位元移出的最重要的位置不會旋轉至最不重要的位置。 最小顯著性位元填補零。 第二個引數的型別是`int32`。|
|`>>>`|位元右移位運算子。 結果會是第一個運算元與第二個運算元的位元數向右移位的位元。 位元移出的最小顯著性位置不會旋轉至最重要的位置。 不帶正負號的類型，最大顯著性位元填補零。 帶正負號的類型，最大顯著性位元和填補。 第二個引數的型別是`int32`。|

下列型別可與位元運算子： `byte`， `sbyte`， `int16`， `uint16`， `int32 (int)`， `uint32`， `int64`， `uint64`， `nativeint`，和`unativeint`。

## <a name="see-also"></a>另請參閱
[符號和運算子參考](index.md)

[算術運算子](arithmetic-operators.md)

[布林運算子](boolean-operators.md)

