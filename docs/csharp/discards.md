---
title: "Discard - C# 指南 | Microsoft Docs"
description: "說明 C# 的 discard 支援，這是未指派且可捨棄的變數，並說明 discard 的使用方式。"
keywords: .NET, .NET Core
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.translationtype: HT
ms.sourcegitcommit: 4582cb0ee091526423cce3fc1d8243029f34f59c
ms.openlocfilehash: eca5febd448a135eb7ec52e4243ae341563190df
ms.contentlocale: zh-tw
ms.lasthandoff: 08/16/2017

---
# <a name="discards---c-guide"></a>Discard - C# 指南

從 C# 7 開始，C# 支援 discard，這是應用程式程式碼中刻意未使用的暫存虛擬變數。 Discard 相當於未指派的變數，不具有任何值。 因為只有一個 discard 變數，而且該變數可能甚至未配置儲存空間，所以 discard 可減少記憶體配置。 這些變數讓您的程式碼意圖更清楚，因而提高其可讀性和可維護性。

指定變數為 discard 的方式是在其名稱中指派底線 (`_`)。 例如，下列方法呼叫會傳回 3 元組，其中的第一個和第二個值為 discard：

```csharp
(var _, _, area) = city.GetCityInformation(cityName);
```

在 C# 7 中，下列內容中的指派支援 discard：

- 元組和物件[解構](deconstruct.md)。
- 以 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 進行的模式比對。
- 以 `out` 參數進行的方法呼叫。
- 範圍內沒有 `_` 時的獨立 `_`。

當 `_` 是有效的 discard 時，嘗試擷取其值或用於指派作業會產生編譯器錯誤 CS0301：「目前內容中不存在名稱 '_'」。 這是因為 `_` 未指派值，可能甚至未指派儲存位置。 如果它原本是實際變數，可能無法像上述範例一樣捨棄多個值。

## <a name="tuple-and-object-deconstruction"></a>元組和物件解構

當您的應用程式程式碼使用一些元組項目但忽略其他項目時，discard 特別適合用來處理元組。 例如，下列 `QueryCityDataForYears` 方法會傳回 6 元組，其中包含城市名稱、其區碼、年份、該年的城市人口、次年的年份、次年的城市人口。 此範例會顯示這兩年之間的人口變化。 在元組可用的資料中，我們對城市區碼不感興趣，並在設計階段得知城市名稱及兩個日期。 因此，我們只對元組中所儲存的兩個人口值感興趣，而可以將其餘值視為 discard。  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

如需使用 discard 解構元組的詳細資訊，請參閱[解構元組和其他類型](deconstruct.md#deconstructing-tuple-elements-with-discards)。

類別、結構或介面的 `Deconstruct` 方法也可讓您從一個物件擷取及解構一組特定的資料。 如果您只想使用部分已解構的值，可以使用 discard。 下列範例會將 `Person` 物件解構為四個字串 (名字、姓氏、城市和州/省)，但捨棄姓氏和州/省。

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

如需使用 discard 解構使用者定義型別的詳細資訊，請參閱[解構元組和其他類型](deconstruct.md#deconstructing-a-user-defined-type-with-discards)。

## <a name="pattern-matching-with-switch-and-is"></a>以 `switch` 和 `is` 進行的模式比對

「捨棄模式」可用於以 [is](language-reference/keywords/is.md) 和 [switch](language-reference/keywords/switch.md) 關鍵字進行的模式比對。 每個運算式一律會比對捨棄模式。

下列範例會定義 `ProvidesFormatInfo` 方法，該方法使用 [is](language-reference/keywords/is.md) 陳述式來判斷物件是否提供 <xref:System.IFormatProvider> 實作，並測試物件是否為 `null`。 它也會使用捨棄模式來處理任何其他類型的非 Null 物件。

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>以 out 參數進行的方法呼叫

當呼叫 `Deconstruct` 方法解構使用者定義型別 (類別、結構或介面的執行個體) 時，您可以捨棄個別 `out` 引數的值。 但當使用 out 參數呼叫任何方法時，您也可以捨棄 `out` 引數的值。 

下列範例會呼叫 [DateTime.TryParse(String, out DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) 方法，以判斷日期的字串表示在目前的文化特性 (culture) 中是否有效。 因為此範例只需要驗證日期字串，而不需要將它剖析以擷取日期，所以該方法的 `out` 引數為 discard。

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>獨立 discard

您可以使用獨立 discard，指出您選擇忽略的任何變數。 下列範例會使用獨立 discard 來忽略非同步作業傳回的 <xref:System.Threading.Tasks.Task> 物件。 這會造成在作業即將完成時，隱藏作業所擲回的例外狀況。

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

請注意，`_` 也是有效的識別項。 在支援的內容之外使用時，`_` 會視為有效的變數，而不是 discard。 如果範圍內已有名為 `_` 的識別項，使用 `_` 作為獨立 discard 可能會導致：

- 將預定的 dscard 值指派給範圍內的 `_` 變數，而意外修改變數的值。 例如: 

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- 違反型別安全的編譯器錯誤。 例如: 

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- 編譯器錯誤 CS0136：「無法在此範圍宣告名為 '_' 的區域變數或參數，因為該名稱已用於封入區域變數範圍，以定義區域變數或參數」。 例如: 

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>請參閱
[解構元組和其他類型](deconstruct.md)   
[`is` 關鍵字](language-reference/keywords/is.md)   
[`switch` 關鍵字](language-reference/keywords/switch.md)   

