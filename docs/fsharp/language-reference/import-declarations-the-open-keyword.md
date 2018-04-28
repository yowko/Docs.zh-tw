---
title: 匯入宣告：open 關鍵字 (F#)
description: '了解 F # 匯入宣告，以及如何指定模組或命名空間而不需要使用完整限定的名稱，您可以參考其項目。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: ddbc1086e2adbe8dae408f4d39fd5af888d7fd5e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="import-declarations-the-open-keyword"></a>匯入宣告：`open`關鍵字

> [!NOTE]
本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

*匯入宣告*指定的模組或命名空間而不需要使用完整限定的名稱，您可以參考其項目。


## <a name="syntax"></a>語法

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>備註
每次使用命名空間或模組的完整的路徑來參考程式碼可以建立，因而難以撰寫、 讀取和維護的程式碼。 相反地，您可以使用`open`關鍵字經常使用的模組和命名空間，因此當您參考該模組或命名空間的成員，您可以使用名稱的簡短形式，而不是完整限定名稱。 這個關鍵字是類似於`using`關鍵字在 C# 中， `using namespace` Visual c + + 和`Imports`在 Visual Basic 中。

模組或命名空間提供必須在相同的專案或參考的專案或組件中。 如果不是，您可以將參考加入專案，或使用`-reference`命令`-`列選項 (或其縮寫， `-r`)。 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。

匯入宣告，讓程式碼所示的宣告，封入命名空間、 模組或檔案結尾之前，您可以使用的名稱。

當您使用多個匯入宣告時，它們應該會出現在不同行。

下列程式碼將示範如何使用`open`關鍵字來簡化程式碼。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

F # 編譯器不會發出錯誤或警告，當多個開啟的模組或命名空間中相同名稱時，就會發生模稜兩可。 發生模稜兩可時，F # 提供更最近開啟的模組或命名空間的喜好設定。 例如，在下列程式碼，`empty`表示`Seq.empty`，即使`empty`兩者都位於`List`和`Seq`模組。

```fsharp
open List
open Seq
printfn "%A" empty
```

因此，要特別小心當您開啟模組或命名空間這類`List`或`Seq`包含具有相同名稱; 相反地，請考慮使用限定的名稱的成員。 您應該避免任何的情況下所在的程式碼是依存於匯入宣告的順序。


## <a name="namespaces-that-are-open-by-default"></a>開啟預設的命名空間
F # 它們會以隱含方式開啟而不需要明確匯入宣告的程式碼經常會使用某些命名空間。 下表顯示開啟的預設命名空間。

|命名空間|描述|
|---------|-----------|
|`Microsoft.FSharp.Core`|包含基本 F # 型別定義的內建類型，例如`int`和`float`。|
|`Microsoft.FSharp.Core.Operators`|包含基本的算術運算，例如`+`和`*`。|
|`Microsoft.FSharp.Collections`|包含不可變的集合類別，例如`List`和`Array`。|
|`Microsoft.FSharp.Control`|包含型別，例如延遲評估和非同步工作流程的控制建構。|
|`Microsoft.FSharp.Text`|包含函式為格式化的 IO，例如`printf`函式。|

## <a name="autoopen-attribute"></a>AutoOpen 屬性
您可以套用`AutoOpen`屬性的組件，如果您想要在參考的組件時，自動開啟命名空間或模組。 您也可以套用`AutoOpen`屬性設定為要開啟 父模組或命名空間時，自動開啟該模組的模組。 如需詳細資訊，請參閱[Core.AutoOpenAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。


## <a name="requirequalifiedaccess-attribute"></a>RequireQualifiedAccess 屬性
某些模組、 記錄或等位型別可能會指定`RequireQualifiedAccess`屬性。 當您參考的那些模組、 記錄或等位的項目時，您必須使用限定的名稱，不論您是否包含匯入宣告。 如果您使用這個屬性策略性上類型會定義最常使用的名稱，有助於避免發生名稱衝突，因而使程式碼更有彈性的程式庫中的變更。 如需詳細資訊，請參閱[Core.RequireQualifiedAccessAttribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。


## <a name="see-also"></a>另請參閱
[# 語言參考](index.md)

[命名空間](namespaces.md)

[模組](modules.md)

