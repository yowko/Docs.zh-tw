---
title: 匯入宣告：Open 關鍵字
description: 深入了解F#匯入宣告，以及如何指定模組或命名空間不需使用完整限定的名稱，您可以參考其項目。
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59054997"
---
# <a name="import-declarations-the-open-keyword"></a>匯入宣告：`open`關鍵字

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

*匯入宣告*指定的模組或命名空間不需使用完整限定的名稱，您可以參考其項目。

## <a name="syntax"></a>語法

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>備註

使用完整的命名空間或模組路徑來參考程式碼每次可以建立很難寫入、 讀取和維護的程式碼。 相反地，您可以使用`open`關鍵字常用模組及命名空間，因此當您參考該模組或命名空間的成員，您可以使用名稱的簡短形式，而不是完整限定名稱。 這個關鍵字是類似`using`關鍵字，在C#，`using namespace`視覺效果中C++，和`Imports`Visual Basic 中。

模組或命名空間提供必須在相同的專案或參考的專案或組件中。 如果不是，您可以將參考加入專案，或使用`-reference`命令`-`列選項 (或其縮寫， `-r`)。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。

匯入宣告可讓您可在程式碼所示的宣告，封入命名空間、 模組或檔案結尾之前的名稱。

當您使用多個匯入宣告時，它們應該會出現在不同行上。

下列程式碼示範如何使用`open`關鍵字來簡化程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F#編譯器不會發出錯誤或警告時相同的名稱，就會發生多個開啟的模組或命名空間中時，會發生模稜兩可。 發生模稜兩可時，F#提供更多最近開啟的模組或命名空間的喜好設定。 例如，在下列程式碼中，`empty`意味著`Seq.empty`，即使`empty`兩者都位於`List`和`Seq`模組。

```fsharp
open List
open Seq
printfn "%A" empty
```

因此，要特別小心當您開啟模組或命名空間這類`List`或`Seq`，其中包含具有相同的名稱; 相反地，請考慮使用限定的名稱的成員。 您應該避免任何情況下，在其中的程式碼是取決於匯入宣告的順序。

## <a name="namespaces-that-are-open-by-default"></a>開啟預設的命名空間

某些命名空間會因此常常會用於F#程式碼，它們會以隱含方式開啟而不需要明確的匯入宣告。 下表顯示已開啟預設的命名空間。

|命名空間|描述|
|---------|-----------|
|`Microsoft.FSharp.Core`|包含基本F#類型的內建型別定義，例如`int`並`float`。|
|`Microsoft.FSharp.Core.Operators`|包含基本算術運算，例如`+`和`*`。|
|`Microsoft.FSharp.Collections`|包含不可變的集合類別，例如`List`和`Array`。|
|`Microsoft.FSharp.Control`|包含控制項的建構，例如延遲評估和非同步工作流程的型別。|
|`Microsoft.FSharp.Text`|包含函式為格式化的 IO，例如`printf`函式。|

## <a name="autoopen-attribute"></a>AutoOpen 屬性

您可以套用`AutoOpen`屬性至組件，如果您想要在參考的組件時，自動開啟命名空間或模組。 您也可以套用`AutoOpen`屬性加入至父模組或命名空間開啟時自動開啟該模組的模組。 如需詳細資訊，請參閱 < [Core.AutoOpenAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。

## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 屬性

某些模組、 記錄或等位型別可能會指定`RequireQualifiedAccess`屬性。 當您參考的那些模組、 記錄或等位的項目時，您必須使用限定的名稱，不論您是否包含匯入宣告。 如果您使用這個屬性策略性上型別會定義最常使用的名稱，您可以協助避免發生名稱衝突，並藉此讓程式碼更有彈性的程式庫中的變更。 如需詳細資訊，請參閱 < [Core.RequireQualifiedAccessAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [命名空間](namespaces.md)
- [模組](modules.md)
