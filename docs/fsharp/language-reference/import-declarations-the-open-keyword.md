---
title: 匯入宣告：open 關鍵字
description: 瞭解 F# 匯入聲明及其如何指定模組或命名空間,這些模組或命名空間的元素無需使用完全限定的名稱即可引用。
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021539"
---
# <a name="import-declarations-the-open-keyword"></a>匯入宣告：`open` 關鍵字

> [!NOTE]
> 本文中的 API 參考連結將帶您前往 MSDN。  docs.microsoft.com API 參考不完整。

*匯入聲明*指定一個模組或命名空間,這些模組或命名空間的元素無需使用完全限定的名稱即可引用。

## <a name="syntax"></a>語法

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a>備註

每次使用完全限定的命名空間或模組路徑引用代碼可以創建難以編寫、讀取和維護的代碼。 相反,`open`您可以將關鍵字用於常用的模組和命名空間,以便在引用該模組或命名空間的成員時,可以使用名稱的簡短形式而不是完全限定的名稱。 此關鍵字類似於 C#`using`中的關鍵字、Visual `using namespace` C++ 和`Imports`Visual Basic 中的關鍵字。

提供的模組或命名空間必須位於同一專案或引用的專案或程式集中。 如果不是,則可以添加對專案的引用,或使用`-reference`命令行選項(或其縮寫。 `-r` 如需詳細資訊，請參閱[編譯器選項](compiler-options.md)。

匯入聲明使聲明後面的代碼中的名稱可用,最多到封閉命名空間、模組或檔的結尾。

使用多個導入聲明時,它們應顯示在單獨的行上。

以下代碼顯示了`open`關鍵字用於簡化代碼的使用。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

當多個打開的模組或命名空間中出現相同名稱時,F# 編譯器不會發出錯誤或警告。 當出現模稜兩可時,F# 優先考慮最近打開的模組或命名空間。 例如,在以下代碼中,`empty``Seq.empty`表示`empty`,即使`List``Seq`位於和模組中也是如此。

```fsharp
open List
open Seq
printfn "%A" empty
```

因此,在打開模組或命名空間(如`List``Seq`或包含具有相同名稱的成員)時要小心;相反,請考慮使用限定名稱。 應避免代碼依賴於導入聲明的順序的任何情況。

## <a name="namespaces-that-are-open-by-default"></a>預設視窗開啟的命名空間

某些命名空間在 F# 代碼中非常頻繁,因此無需顯式導入聲明即可隱式打開。 下表顯示了默認情況下打開的命名空間。

|命名空間|描述|
|---------|-----------|
|`Microsoft.FSharp.Core`|包含內建型態(如`int``float`和) 的基本 F# 類型定義。|
|`Microsoft.FSharp.Core.Operators`|包含基本算術運算,如`+``*`和 。|
|`Microsoft.FSharp.Collections`|包含不可變的集合類別,`List`如`Array`與 。|
|`Microsoft.FSharp.Control`|包含控件構造的類型,如惰性評估和異步工作流。|
|`Microsoft.FSharp.Text`|包含格式化 IO 的`printf`功能, 如函數。|

## <a name="autoopen-attribute"></a>自動開啟屬性

如果要在引用程式集`AutoOpen`時自動打開命名空間或模組,則可以將該屬性應用於程式集。 您還可以將`AutoOpen`該屬性應用於模組,以在打開父模組或命名空間時自動打開該模組。 有關詳細資訊,請參閱[Core.AutoOpenattribute 類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d)。

## <a name="requirequalifiedaccess-attribute"></a>需要限定存取屬性

某些模組、記錄或聯合類型可以指定該`RequireQualifiedAccess`屬性。 引用這些模組、記錄或聯合的元素時,無論是否包含導入聲明,都必須使用限定名稱。 如果在定義常用名稱的類型上戰略性地使用此屬性,則有助於避免名稱衝突,從而使代碼對庫中的更改更具彈性。 有關詳細資訊,請參閱[Core.要求限定 Access 屬性類別](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D)。

## <a name="see-also"></a>另請參閱

- [F# 語言參考](index.md)
- [命名空間](namespaces.md)
- [模組](modules.md)
