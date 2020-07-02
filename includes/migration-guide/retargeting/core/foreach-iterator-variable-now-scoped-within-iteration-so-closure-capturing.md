---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617139"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Foreach 迭代器變數的範圍現在會設定為在反覆項目內，因此關閉擷取語意不同 (在 C#5 中)

#### <a name="details"></a>詳細資料

從 C# 5 (Visual Studio 2012) 開始，`foreach` 迭代器變數的範圍會設定為在反覆項目內。 如果程式碼之前需要這些變數才不會包含在 `foreach` 的關閉中，這可能會導致中斷。 這項變更的徵兆是傳遞至委派的迭代器變數會視為建立委派時所具有的值，而不是叫用委派時所具有的值。

#### <a name="suggestion"></a>建議

在理想情況下，您應該更新程式碼，以確保此新的編譯器行為。 如果需要舊版語意，您可以將此迭代器變數取代成明確放在迴圈範圍外的不同變數。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | 主要       |
| 版本 | 4.5         |
| 類型    | 正在重定目標 |
