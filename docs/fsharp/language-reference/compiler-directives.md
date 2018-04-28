---
title: 編譯器指示詞 (F#)
description: '深入了解 F # 語言前置處理器指示詞、 條件式編譯指示詞、 line 指示詞和編譯器指示詞。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 03fe3598f04025cf6dfaf2424b9fcb33ed4b3859
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="compiler-directives"></a>編譯器指示詞

本主題描述處理器指示詞和編譯器指示詞。


## <a name="preprocessor-directives"></a>前置處理器指示詞
前置處理器指示詞的字首會加上 # 符號，且自身會出現在一行中。 它是由前置處理器解譯，會在編譯器本身之前執行。

下表列出 F# 中可用的前置處理器指示詞。


|指示詞|描述|
|---------|-----------|
|`#if` *符號*|支援條件式編譯。 後面的區段中的程式碼`#if`會包括*符號*定義。|
|`#else`|支援條件式編譯。 若未定義與先前的 `#if` 搭配使用的符號，則標記要包含的程式碼區段。|
|`#endif`|支援條件式編譯。 標示程式碼的條件式區段結尾。|
|`#`[線條]*int*，<br/>`#`[線條]*int* *字串*，<br/>`#`[線條]*int* *逐字字串*|表示原始的原始程式碼行和檔案名稱 (適用於偵錯)。 這項功能提供用於產生 F# 原始程式碼的工具。|
|`#nowarn` *warningcode*|停用編譯器警告。 若要停用警告，請從編譯器輸出中找出其號碼並包含在引號中。 略過 "FS" 前置詞。 若要停用同一行的多個警告號碼，請以引號括住每個號碼，並以一個空格分隔每個字串。 例如: 

`#nowarn "9" "40"`


停用警告的效果套用到整個檔案，包括檔案的指示詞前面的部分。 |

## <a name="conditional-compilation-directives"></a>條件式編譯指示詞
已停用其中一個這些指示詞呈現灰色程式碼在 Visual StudioCode 編輯器中。


>[!NOTE] 
條件式編譯指示詞的行為與其在其他語言的行為不同。 例如，您無法使用包含符號的布林運算式，且 `true` 和 `false` 沒有特殊意義。 在 `if` 指示詞中使用的符號必須透過命令列定義，或在專案設定中定義；沒有任何 `define` 前置處理器指示詞。


下列程式碼說明如何使用 `#if`、`#else` 和 `#endif` 指示詞。 在此範例中，程式碼包含兩個版本的 `function1` 定義。 當`VERSION1`定義使用[-define 編譯器選項](https://msdn.microsoft.com/library/434394ae-0d4a-459c-a684-bffede519a04)，之間的程式碼`#if`指示詞和`#else`指示詞會啟動。 否則會啟動 `#else` 與 `#endif` 之間的程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7301.fs)]

F# 中沒有 `#define` 前置處理器指示詞。 您必須使用編譯器選項或專案設定來定義 `#if` 指示詞所使用的符號。

條件式編譯指示詞可以巢狀化。 縮排對於前置處理器指示詞而言不重要。


## <a name="line-directives"></a>行指示詞
建置時，編譯器會參考發生的每個錯誤所在的行號，以報告 F# 程式碼中的錯誤。 這些行號從 1 開始，從檔案的第一行起算。 不過，如果您正在從另一個工具產生 F# 原始程式碼，產生的程式碼中的行號通常不重要，因為產生的 F# 程式碼中的錯誤很可能來自其他來源。 `#line` 指示詞為工具的作者提供一種方式，即產生 F# 原始程式碼，將有關原始行號和來源檔案的相關資訊傳遞給產生的 F# 程式碼。

使用 `#line` 指示詞時，檔案名稱必須括在引號內。 除非逐字語彙基元 (`@`) 會出現在字串前面，否則必須逸出反斜線字元 (使用兩個反斜線字元而非一個)，才能在路徑中使用它們。 下面是有效的行語彙基元。 在這些範例中，假設透過工具執行原始檔案 `Script1` 時，會自動產生 F# 程式碼檔案，並會在 `Script1` 檔的第 25 行，從某些語彙基元中產生這些指示詞位置處的程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7303.fs)]

這些語彙基元指出在這個位置產生的 F# 程式碼，是衍生自 `Script1` 的 `25` 行或附近的某些建構。


## <a name="compiler-directives"></a>編譯器指示詞
編譯器指示詞類似前置處理器指示詞，因為它們會加上 # 符號前置詞，但不是由前置處理器解譯，而是留給編譯器解譯及處理。

下表列出可在 F# 中使用的編譯器指示詞。


|指示詞|描述|
|---------|-----------|
|`#light` ["on"&#124;"off"]|啟用或停用輕量型語法，與其他 ML 版本相容。 根據預設，會啟用輕量型語法。 一律會啟用詳細語法。 因此，您可以使用輕量型語法和詳細語法。 指示詞 `#light` 本身就相當於 `#light "on"`。 如果您指定 `#light "off"`，您必須針對所有語言建構使用詳細語法。 會假設您使用輕量型語法，在文件中顯示 F# 語法。 如需詳細資訊，請參閱[詳細語法](verbose-syntax.md)。|
解譯器 (fsi.exe) 指示詞，請參閱[使用 F # 互動式程式設計](../tutorials/fsharp-interactive/index.md)。


## <a name="see-also"></a>另請參閱
[F# 語言參考](index.md)

[編譯器選項](compiler-options.md)

