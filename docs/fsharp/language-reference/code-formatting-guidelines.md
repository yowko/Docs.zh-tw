---
title: 程式碼格式化方針 (F#)
description: 'F # 程式語言的可讀性、 美學、 標準化及編譯，了解程式碼縮排格式的指導方針。'
ms.date: 05/16/2016
ms.openlocfilehash: 5bb1f9958a21beb795f9174e44f24c7194453fc3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="code-formatting-guidelines"></a>程式碼格式化方針

本主題會摘要 F # 程式碼縮排的指導方針。 因為敏感分行符號和縮排的 F # 語言，不是只可讀性問題、 美觀的問題或若要正確地格式化您的程式碼的程式碼撰寫標準化問題。 您必須正確，才能正確編譯的程式碼的格式。


## <a name="general-rules-for-indentation"></a>縮排的一般規則
需要縮排時，您必須使用空間，而不是索引標籤。 需要至少一個空白字元。 您的組織可以建立以指定要用來縮排; 的空格數目編碼標準通常會發生縮排每個層級的縮排的三或四個空格。 您可以設定 Visual Studio，以變更的選項，以符合您組織的縮排標準`Options`對話方塊中，可從`Tools`功能表。 在`Text Editor` 節點，展開  `F#` ，然後按一下  `Tabs`。 如需可用之選項的說明，請參閱[選項、 文字編輯器、 所有語言、 索引標籤](https://msdn.microsoft.com/library/7sffa753.aspx)。

一般情況下，當編譯器剖析您的程式碼，它會保留內部堆疊，指出目前的巢狀層級。 當程式碼就會縮排時，新的層級的巢狀結構會在建立或推送到這個內部堆疊上。 建構結束時，則會彈出層級。 縮排層級的結尾和 pop 內部堆疊，一種方法，但特定語彙基元也會導致層級即可推出，例如`end`關鍵字，或右大括號或括號。

多行的建構，例如的類型定義中的程式碼函式定義`try...with`建構和迴圈建構，必須縮排相對於建構的開頭行。 首行縮排相同的建構函式建立後續的程式碼的資料行位置。 縮排層級稱為*內容*。 資料行位置設定的最小的資料行，稱為*越位行*，後續的程式碼行的程式碼是在相同的內容。 遇到一行程式碼時較少比這個位置上建立資料行縮排，編譯器會假設已結束內容和，您要現在撰寫程式碼在下一個層級，在先前的內容。 詞彙*越位*用來描述的條件，因為它不會縮排到足以觸發建構結尾的程式碼行。 換句話說，左邊的越位行程式碼是越位。 正確縮排程式碼中，您利用越位規則才能描寫建構結尾。 如果您不當使用縮排，越位狀況會導致編譯器發出警告，或可能會導致您的程式碼不正確解譯。

越位行決定，如下所示。


- `=`與相關聯的語彙基元`let`導入了位於第一個語彙基元之後的資料行越位行`=`符號。


- 在`if...then...else`運算式、 資料行的位置之後的第一個語彙基元`then`關鍵字或`else`關鍵字導入了越位行。


- 在`try...with`運算式、 後的第一個語彙基元`try`介紹越位行。


- 在`match`運算式、 後的第一個語彙基元`with`和第一個語彙基元之後每個,`->`引入越位行。


- 之後的第一個語彙基元`with`類型擴充功能引進了越位行。


- 第一個語彙基元之後的左大括號或括號，或在`begin`關鍵字，導入了越位行。


- 關鍵字的第一個字元`let`， `if`，和`module`引入越位行。


下列程式碼範例說明的縮排規則。 在這裡，print 陳述式會依賴縮排至與適當的內容產生關聯。 每次將縮排，取出內容，並返回先前的內容。 因此，空格會列印結尾的每個反覆項目。「 完成 」 ！ 只列印一次，因為越位縮排會建立不是在迴圈的一部分。 字串 「 最上層內容 」 的列印不是函式的一部分。 因此，它會先列印的靜態初始化期間，會在呼叫函式之前。

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

輸出如下。

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

當您中斷長行時，行接續必須縮排至封入建構。 例如，函式引數必須縮排至第一個字元的函式名稱，如下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

下一節中所述，則需要有這些規則的例外狀況。


## <a name="indentation-in-modules"></a>在模組中的縮排
在本機的模組中的程式碼必須縮排相對於模組，但最上層的模組中的程式碼不一定要縮排。 命名空間元素不具有縮排。

下列程式碼範例將說明這點。

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

如需詳細資訊，請參閱[模組](modules.md)。


## <a name="exceptions-to-the-basic-indentation-rules"></a>基本的縮排規則的例外狀況
一般的規則上, 一節中所述是多行建構中的程式碼必須相對於建構的第一行的縮排會縮排和第一個越位行發生時，由決定建構結尾。 相關內容結束時，某些建構，例如規則的例外狀況`try...with`運算式`if...then...else`運算式，以及使用`and`語法來宣告相互遞迴函式或類型，有多個部分。 您縮排的更新版本的組件，例如`then`和`else`中`if...then...else`運算式，在相同層級做為權杖啟動運算式，但而不是指出內容結束時，它代表相同的內容中的下一個部分。 因此，`if...then...else`可以撰寫運算式，如下列程式碼範例所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

越位規則的例外狀況只會套用到`then`和`else`關鍵字。 因此，雖然這並非要縮排錯誤`then`和`else`進一步，失敗的縮排中的程式碼行`then`區塊會產生警告。 下列程式碼所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

中的程式碼`else`適用於區塊中，有額外的特殊規則。 上述範例中的警告，就會發生在程式碼中`then`區塊中，不是在中的程式碼`else`區塊。 這可讓您撰寫程式碼，而不未強制其餘的函式，這可能是在程式碼會檢查開頭函式的各種狀況`else`區塊，縮排。 因此，您可以撰寫下列不會產生警告。

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

另一個例外狀況時一條線不會縮排就前一行是中置運算子，例如，結束內容的規則`+`和`|>`。 允許中置運算子為開頭的行開始`(1 + oplength)`正常的位置，而不觸發內容結束之前的資料行其中`oplength`會運算子構成的字元數。 這會導致第一個語彙基元來對齊上下行運算子後面。

例如，在下列程式碼，`+`符號可以是小於前一行的縮排的兩個資料行。

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

雖然的巢狀層級更高版本時，通常會增加縮排，有數個建構在其中編譯器可讓您重設為較低的資料行位置的縮排。

允許的資料行位置重設的建構如下所示：


- 匿名函式的主體。 下列程式碼中，列印的運算式會從資料行位置更遠比左側`fun`關鍵字。 不過，在列不能在左邊開始的上一個縮排層級的資料行 (也就是左邊`L`中`List`)。
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- 建構括以括號或`begin`和`end`中`then`或`else`區塊`if...then...else`運算式，提供縮排是不小於的資料行位置`if`關鍵字。 這個例外狀況允許編碼樣式所在左括號或`begin`結尾的後一條線使用`then`或`else`。


- 主體的模組、 類別、 介面和結構，以分隔`begin...end`， `{...}`， `class...end`，或`interface...end`。 這可讓您在其中開啟關鍵字型別定義的型別名稱的同一行不能強制執行是開啟關鍵字至縮排的整個主體樣式。
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)
