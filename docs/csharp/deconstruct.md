---
title: "解構元組和其他類型"
description: "了解如何解構 Tuple 和其他類型。"
keywords: .NET,.NET Core,C#
author: rpetrusha
ms-author: ronpet
ms.date: 07/18/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.translationtype: HT
ms.sourcegitcommit: 863940512f33568ee10569da4712e7e646bc3ba7
ms.openlocfilehash: ad0ed6568da073683545727ef47f6a223942c8d6
ms.contentlocale: zh-tw
ms.lasthandoff: 08/12/2017

---
# <a name="deconstructing-tuples-and-other-types"></a>解構元組和其他類型 #

元組可讓您輕鬆地從方法呼叫擷取多個值。 但擷取元組之後，您必須處理其個別項目。 逐項目執行這項作業很麻煩，如下列範例所示。 `QueryCityData` 方法會傳回 3 元組，並以不同作業將其每個項目指派給個別變數。

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

從一個物件擷取多個欄位和屬性值可能一樣麻煩：您必須逐成員將欄位或屬性值指派給個別變數。 

從 C# 7 開始，您可以透過單一 *deconstruct* 作業，從一個元組擷取多個項目，或從一個物件擷取多個欄位、屬性和計算值。 當您解構元組時，您會將其項目指派給個別變數。 當您解構物件時，您會將選取的值指派給個別變數。 

## <a name="deconstructing-a-tuple"></a>解構元組

C# 提供解構元組的內建支援，讓您以單一作業將元組中的所有項目解除封裝。 解構元組的一般語法類似定義元組的語法：您會在指派陳述式的左側，以括弧括住要指派每個項目的變數。 例如，下列陳述式會將 4 元組的項目指派給四個不同的變數：

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

解構元組的方式有兩種：

- 您可以明確地宣告括弧內每個欄位的類型。 下列範例會使用此方法來解構 `QueryCityData` 方法傳回的 3 元組。

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- 您可以使用 `var` 關鍵字，讓 C# 推斷每個變數的類型。 請將 `var` 關鍵字放在括弧外。 下列範例會在解構 `QueryCityData` 方法傳回的 3 元組時，使用型別推斷。
 
    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    您也可以個別使用 `var` 關鍵字搭配括弧內的任何或所有變數宣告。 

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    這樣做很麻煩，因此不建議使用。

請注意，您無法在括弧外指定特定類型，即使元組中的每個欄位都有相同的類型也是一樣。 這會產生編譯器錯誤 CS8136：「解構 'var (...)' 表單不允許特定的 'var' 類型」。

請注意，您也必須將元組的每個項目指派給個別變數。 如果您省略任何項目，編譯器會產生錯誤 CS8132：「無法將 'x' 項目的元組解構為 'y' 變數」。

## <a name="deconstructing-tuple-elements-with-discards"></a>使用 Discard 解構元組項目

解構元組時，您通常只對部分項目的值感興趣。 從 C# 7 開始，您可以利用 C# 的 *discard* 支援，這是您已選擇忽略其值的唯寫變數。 Discard 是由指派中的底線字元 ("\_") 指定。 您可以視需要捨棄許多值，每個值都會以單一 discard `_` 表示。

下列範例說明如何搭配使用元組與 discard。 `QueryCityDataForYears` 方法會傳回 6 元組，其中包含城市名稱、其區碼、年份、該年的城市人口、次年的年份、次年的城市人口。 此範例會顯示這兩年之間的人口變化。 在元組可用的資料中，我們對城市區碼不感興趣，並在設計階段得知城市名稱及兩個日期。 因此，我們只對元組中所儲存的兩個人口值感興趣，而可以將其餘值視為 discard。  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>解構使用者定義型別

非元組類型不會提供 discard 的內建支援。 不過，身為類別、結構或介面的作者，您可以藉由實作一或多個 `Deconstruct` 方法來解構類型的執行個體。 此方法會傳回 void，而且所要解構的每個值會以方法簽章中的 [out](language-reference/keywords/out-parameter-modifier.md) 參數表示。 例如，`Person` 類別的下列 `Deconstruct` 方法會傳回名字、中間名和姓氏：

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

您可以接著使用如下所示的指派，來解構名為 `p` 的 `Person` 類別執行個體：

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

下列範例會多載 `Deconstruct` 方法，以傳回 `Person` 物件屬性的各種組合。 每個多載會傳回：

- 名字和姓氏。
- 名字、姓氏和中間名。
- 名字、姓氏、城市名稱和州/省名稱。

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

因為您可以多載 `Deconstruct` 方法以反映多組經常從物件擷取的資料，所以應該使用獨特且明確的簽章來小心定義 `Deconstruct` 方法。 多個 `Deconstruct` 方法如有相同數目但不同順序的 `out` 參數，或有相同數目和類型但不同順序的 `out` 參數，則會造成混淆。 

下列範例中的多載方法 `Deconstruct` 說明造成混淆的其中一個可能來源。 第一個多載會依序傳回 `Person` 物件的名字、中間名、姓氏和年齡。 第二個多載會傳回名稱資訊和年收入，但名字、中間名和姓氏的順序不同。 解構 `Person` 執行個體時很容易混淆引數的順序。

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>使用 discard 解構使用者定義型別

就像[元組](#deconstructing-tuple-elements-with-discards)一樣，您可以使用 discard 來忽略 `Deconstruct` 方法傳回的選取項目。 每個 discard 是由名為 "\_" 的變數定義，而單一解構作業可包含多個 discard。

下列範例會將 `Person` 物件解構為四個字串 (名字、姓氏、城市和州/省)，但捨棄姓氏和州/省。

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>使用擴充方法解構使用者定義型別

如果您並未撰寫類別、結構或介面，仍然可以解構該類型的物件，方法是實作一或多個 `Deconstruct` [擴充方法](programming-guide/classes-and-structs/extension-methods.md)來傳回您想要的值。 

下列範例為 <xref:System.Reflection.PropertyInfo?displayProperty=fullName> 類別定義兩個 `Deconstruct` 擴充方法。 第一個方法會傳回一組值，指出屬性的特性 (包括其類型)、這是靜態或執行個體、是否為唯讀，以及是否已建立索引。 第二個方法指出屬性的存取範圍。 因為 get 和 set 存取子的存取範圍可能不同，所以布林值會指出屬性是否有不同的 get 和 set 存取子，並在不同時指出其是否具有相同的存取範圍。 如果只有一個存取子，或是 get 和 set 存取子具有相同的存取範圍，則 `access` 變數會指出屬性的整個存取範圍。 否則，get 和 set 存取子的存取範圍是以 `getAccess` 和 `setAccess` 變數表示。

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]
 
## <a name="see-also"></a>請參閱
[Discard](discards.md)   
[元組](tuples.md)  

