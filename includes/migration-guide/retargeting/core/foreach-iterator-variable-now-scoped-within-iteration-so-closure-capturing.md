---
ms.openlocfilehash: 1805c26f1eff46719f30de8a14ca6d35f01948a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774316"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Foreach 迭代器變數的範圍現在會設定為在反覆項目內，因此關閉擷取語意不同 (在 C#5 中)

|   |   |
|---|---|
|詳細資料|從 C# 5 (Visual Studio 2012) 開始，<code>foreach</code> 迭代器變數的範圍會設定為在反覆項目內。 如果程式碼之前需要這些變數才不會包含在 <code>foreach</code> 的關閉中，這可能會導致中斷。 這項變更的徵兆是傳遞至委派的迭代器變數會視為建立委派時所具有的值，而不是叫用委派時所具有的值。|
|建議|在理想情況下，您應該更新程式碼，以確保此新的編譯器行為。 如果需要舊版語意，您可以將此迭代器變數取代成明確放在迴圈範圍外的不同變數。|
|範圍|主要|
|版本|4.5|
|類型|正在重定目標|
