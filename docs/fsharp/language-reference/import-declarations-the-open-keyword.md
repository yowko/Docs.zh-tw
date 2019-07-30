---
title: 匯入宣告：Open 關鍵字
description: 瞭解匯F#入宣告, 以及它們如何指定模組或命名空間, 而不需使用完整名稱, 即可參考其元素。
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630570"
---
# <a name="import-declarations-the-open-keyword"></a>匯入宣告：`open` 關鍵字

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

匯*入*宣告會指定模組或命名空間, 而不需使用完整名稱, 即可參考其元素。

## <a name="syntax"></a>語法

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>備註

每次使用完整的命名空間或模組路徑來參考程式碼, 可以建立難以撰寫、讀取和維護的程式碼。 相反地, 您可以對`open`常用的模組和命名空間使用關鍵字, 如此一來, 當您參考該模組或命名空間的成員時, 就可以使用名稱的簡短形式, 而不是完整名稱。 這個關鍵字類似于中的`using`關鍵字C#、 `using namespace` Visual C++中的和`Imports` Visual Basic。

提供的模組或命名空間必須位於相同的專案或參考的專案或元件中。 如果不是, 您可以加入專案的參考, 或使用`-reference`命令`-`行選項`-r`(或其縮寫)。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。

匯入宣告會在宣告後面的程式碼中提供名稱, 最多可在封閉式命名空間、模組或檔案的結尾。

當您使用多個匯入宣告時, 它們應該會出現在不同的行上。

下列程式碼顯示如何使用`open`關鍵字來簡化程式碼。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

當F#一個以上的開啟模組或命名空間中出現相同名稱時, 編譯器不會發出錯誤或警告。 發生歧義時, F#會將喜好設定提供給最近開啟的模組或命名空間。 例如, 在下列`empty` `empty`程式碼中, 即使`Seq.empty`位於`List`和`Seq`模組中, 還是表示。

```fsharp
open List
open Seq
printfn "%A" empty
```

因此, 當您開啟的模組或命名空間 (例如`List`或`Seq` ) 包含具有相同名稱的成員時, 請務必小心, 改為考慮使用限定名稱。 您應該避免程式碼相依于匯入宣告順序的任何情況。

## <a name="namespaces-that-are-open-by-default"></a>預設開啟的命名空間

某些命名空間經常在程式碼F#中使用, 因為它們會以隱含方式開啟, 而不需要明確的匯入宣告。 下表顯示預設開啟的命名空間。

|命名空間|描述|
|---------|-----------|
|`Microsoft.FSharp.Core`|包含內F#建類型 (例如`int`和`float`) 的基本類型定義。|
|`Microsoft.FSharp.Core.Operators`|包含基本的算數運算`+` , 例如和。 `*`|
|`Microsoft.FSharp.Collections`|包含不可變的集合類別`List` , `Array`例如和。|
|`Microsoft.FSharp.Control`|包含控制項結構的類型, 例如延遲評估和非同步工作流程。|
|`Microsoft.FSharp.Text`|包含格式化 IO 的函式, 例如`printf`函數。|

## <a name="autoopen-attribute"></a>AutoOpen 屬性

如果您想要`AutoOpen`在參考元件時自動開啟命名空間或模組, 可以將屬性套用至元件。 您也可以將`AutoOpen`屬性套用至模組, 以便在父模組或命名空間開啟時自動開啟該模組。 如需詳細資訊, 請參閱[AutoOpenAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 屬性

某些模組、記錄或等位類型可能會指定`RequireQualifiedAccess`屬性。 當您參考這些模組、記錄或等位的元素時, 不論您是否包含匯入宣告, 都必須使用限定名稱。 如果您在定義常用名稱的類型上策略性地使用此屬性, 則有助於避免名稱衝突, 進而讓程式碼更有彈性地進行程式庫中的變更。 如需詳細資訊, 請參閱[RequireQualifiedAccessAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [命名空間](namespaces.md)
- [模組](modules.md)
