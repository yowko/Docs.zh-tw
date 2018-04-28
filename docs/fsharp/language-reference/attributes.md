---
title: 屬性 (F#)
description: '了解 F # 屬性如何啟用要套用至程式設計建構的中繼資料。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: b8efc0cdc14e690bbc5c24456d0b1eaa3d55988e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="attributes"></a>屬性

屬性會啟用要套用至程式設計建構的中繼資料。

## <a name="syntax"></a>語法

```fsharp
[<target:attribute-name(arguments)>]
```

## <a name="remarks"></a>備註

在先前的語法，*目標*是選擇性的而且如果有的話，指定程式實體的屬性會套用至類型。 有效值*目標*會出現在本文件稍後的表格所示。

*屬性名稱*（可能是命名空間限定） 名稱的有效屬性類型，或後置詞不參考`Attribute`，通常使用於屬性的型別名稱。 例如，型別`ObsoleteAttribute`可以縮短到`Obsolete`在此內容中。

*引數*屬性型別建構函式的引數。 如果屬性有預設建構函式，可以省略引數清單和括號。 屬性支援位置引數和具名引數。 *位置引數*是以它們出現的順序中使用的引數。 如果屬性有公用屬性，可以使用具名引數。 您可以設定這些引數清單中使用下列語法。

```
*property-name* = *property-value*
```

這類屬性的初始化可以依任何順序，但它們必須遵循下列任何位置的引數。 下列是屬性的範例的使用位置引數和屬性初始設定。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6202.fs)]

在此範例中，屬性是`DllImportAttribute`，這裡用於縮短形式。 第一個引數是位置參數，而且第二個是屬性。

屬性是.NET 程式設計建構，可讓物件稱為*屬性*與類型或其他程式元素相關聯。 屬性所套用的程式項目稱為*屬性目標*。 屬性通常會包含其目標的相關中繼資料。 在此情況下，中繼資料可能會以外的欄位和成員類型有關的任何資料。

F # 中的屬性可以套用至下列程式設計建構： 函式、 方法、 組件、 模組、 類型 （類別、 記錄、 結構、 介面、 委派、 列舉、 等位和等等）、 建構函式、 屬性、 欄位、 參數、型別參數，並傳回值。 屬性不允許在`let`類別、 運算式或工作流程運算式內的繫結。

一般而言，屬性宣告出現之前屬性目標的宣告。 可以使用多個屬性宣告，在一起，如下。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6603.fs)]

您可以使用.NET 反映，在執行階段查詢屬性。

您可以個別宣告多個屬性，如同先前的程式碼範例中，或您可以宣告一組括號中如果您使用分號來分隔個別的屬性和建構函式，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6604.fs)]

通常發生的屬性包括`Obsolete`適用於 COM 支援、 擁有權的程式碼中，與相關的屬性和屬性，指出是否可序列化型別屬性的屬性，屬性的安全性考量。 下列範例示範如何使用`Obsolete`屬性。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6605.fs)]

屬性目標`assembly`和`module`，您將屬性套用至最上層`do`組件中的繫結。 您可以包含單字`assembly`或`module`在屬性宣告中，如下所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6606.fs)]

如果您省略套用至屬性的屬性目標`do`繫結時，F # 編譯器會嘗試判斷適合該屬性的屬性目標。 許多屬性的類別有類型的屬性`System.AttributeUsageAttribute`包含支援該屬性的可能目標的相關資訊。 如果`System.AttributeUsageAttribute`表示屬性支援做為目標的函式，屬性會從要套用至程式的主要進入點。 如果`System.AttributeUsageAttribute`表示屬性支援做為目標的組件，編譯器會採用要套用至組件的屬性。 大部分的屬性不會套用至函式和組件，但在其中執行的情況下，屬性是要套用至程式的 main 函式。 如果明確指定之屬性目標，則屬性會套用至指定的目標。

雖然您通常不需要指定屬性明確地目標的有效值*目標*屬性中會顯示在下列資料表中，以及使用方式的範例。

<table>
  <tr>
    <th>屬性目標</td>
    <th>範例</td> 
  </tr>
  <tr>
    <td>組件</td>
    <td>`[<assembly: AssemblyVersionAttribute("1.0.0.0")>]`</td> 
  </tr>
  <tr>
    <td>return</td>
    <td>' function1 可讓 x: [<return: Obsolete>] int = x + 1'</td> 
  </tr>
  <tr>
    <td>Field - 欄位</td>
    <td>' [<field: DefaultValue>] val mutable x: int'</td> 
  </tr>
  <tr>
    <td>屬性</td>
    <td>' [<property: Obsolete>] 這。MyProperty = x'</td> 
  </tr>
  <tr>
    <td>Param</td>
    <td>' 成員這。MyMethod ([<param: Out>] x: ref<int>) = x: = 10'</td> 
  </tr>
  <tr>
    <td>類型</td>
    <td>
        ```
        [<type: StructLayout(Sequential)>] 輸入 MyStruct = struct x： 位元組 y: int 結束 ```
    </td> 
  </tr>
</table>

## <a name="see-also"></a>另請參閱

[F# 語言參考](index.md)
