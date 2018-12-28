---
title: Boolean 運算子
description: 深入了解可用於布林運算子F#程式設計語言。
ms.date: 05/16/2016
ms.openlocfilehash: 5353b6ec6a0bd610f3446761a1d28f01f0403302
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612734"
---
# <a name="boolean-operators"></a>Boolean 運算子

本主題說明中的布林運算子的支援F#語言。

## <a name="summary-of-boolean-operators"></a>布林運算子的摘要

下表摘要說明可用於布林運算子F#語言。 唯一支援這些運算子的類型是`bool`型別。

|運算子|描述|
|--------|-----------|
|`not`|布林值的否定運算|
|<code>&#124;&#124;</code>|布林值 OR|
|`&&`|布林值 AND|

布林值 AND 和 OR 運算子執行*最少運算評估*，也就是它們評估運算式運算子的右側時才需要判斷整體運算式的結果。 第二個運算式`&&`運算子會評估第一個運算式評估為時，才`true`; 的第二個運算式`||`運算子會評估，只有第一個運算式評估為`false`。

## <a name="see-also"></a>另請參閱

- [位元運算子](bitwise-operators.md)
- [算術運算子](arithmetic-operators.md)
- [符號和運算子參考](index.md)