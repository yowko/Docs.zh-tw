---
title: 匯入宣告：open 關鍵字
description: '瞭解 F # 匯入宣告，以及它們如何指定模組或命名空間，而您可以參考其元素，而不需使用完整名稱。'
ms.date: 08/15/2020
ms.openlocfilehash: 6420df071f86159c44606c2710331d5f587023cc
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557603"
---
# <a name="import-declarations-the-open-keyword"></a>匯入宣告： `open` 關鍵字

匯 *入* 宣告會指定模組或命名空間，而您可以參考其元素，而不需使用完整名稱。

## <a name="syntax"></a>語法

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>備註

每次使用完整命名空間或模組路徑來參考程式碼，可以建立難以撰寫、讀取和維護的程式碼。 相反地，您可以將 `open` 關鍵字用於常用的模組和命名空間，如此一來，當您參考該模組或命名空間的成員時，就可以使用名稱的簡短形式，而不是完整名稱。 這個關鍵字類似于 `using` c # 中的關鍵字、 `using namespace` Visual C++ 中和 `Imports` Visual Basic。

提供的模組或命名空間必須位於相同的專案或參考的專案或元件中。 如果不是，您可以加入專案的參考，或使用 `-reference` 命令列選項 (或其縮寫 `-r`) 。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。

匯入宣告會讓宣告後面的程式碼中的名稱可供使用，最多可包含在封入命名空間、模組或檔案的結尾。

當您使用多個匯入宣告時，它們應該會出現在不同的行上。

下列程式碼顯示 `open` 如何使用關鍵字來簡化程式碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

當有多個開啟的模組或命名空間中發生不明確的名稱時，F # 編譯器不會發出錯誤或警告。 發生多義性時，F # 會優先偏好最近開啟的模組或命名空間。 例如，在下列程式碼中， `empty` `Seq.empty` 即使 `empty` 位於和模組中，也是一樣 `List` `Seq` 。

```fsharp
open List
open Seq
printfn "%A" empty
```

因此，當您開啟包含具有相同名稱之成員的模組或命名空間時，請小心， `List` `Seq` 改為考慮使用限定名稱。 您應該避免程式碼相依于匯入宣告順序的任何情況。

## <a name="namespaces-that-are-open-by-default"></a>預設會開啟的命名空間

有些命名空間在 F # 程式碼中經常會用到，因此會隱含地開啟，而不需要明確的匯入宣告。 下表顯示預設開啟的命名空間。

|命名空間|描述|
|---------|-----------|
|`FSharp.Core`|包含內建類型（例如和）的基本 F # 型別定義 `int` `float` 。|
|`FSharp.Core.Operators`|包含基本的算數運算 `+` ，例如和 `*` 。|
|`FSharp.Collections`|包含不可變的集合類別 `List` ，例如和 `Array` 。|
|`FSharp.Control`|包含控制項結構的類型，例如延遲評估和非同步工作流程。|
|`FSharp.Text`|包含格式化 IO 的函式，例如 `printf` 函數。|

## <a name="autoopen-attribute"></a>AutoOpen 屬性

`AutoOpen`如果您想要在參考元件時自動開啟命名空間或模組，您可以將屬性套用至元件。 您也可以將 `AutoOpen` 屬性套用至模組，以在父模組或命名空間開啟時自動開啟該模組。 如需詳細資訊，請參閱 [AutoOpenAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-autoopenattribute.html)。

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 屬性

某些模組、記錄或等位類型可能會指定 `RequireQualifiedAccess` 屬性。 當您參考這些模組、記錄或等位的專案時，您必須使用限定名稱，不論是否包含匯入宣告。 如果您策略性地在定義常用名稱的類型上使用此屬性，則有助於避免名稱衝突，進而使程式碼在程式庫中的變更時更具彈性。 如需詳細資訊，請參閱 [RequireQualifiedAccessAttribute](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html)。

## <a name="see-also"></a>另請參閱

- [F # 語言參考](index.md)
- [命名空間](namespaces.md)
- [單元](modules.md)
