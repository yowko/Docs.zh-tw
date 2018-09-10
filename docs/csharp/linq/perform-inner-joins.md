---
title: 執行內部聯結 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 執行內部聯結。
ms.date: 12/1/2016
ms.assetid: 45bceed6-f549-4114-a9b1-b44feb497742
ms.openlocfilehash: 2f6aad30dc8278ce1bb88bacc19b27deaa0288c7
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44276948"
---
# <a name="perform-inner-joins"></a>執行內部聯結

在關聯式資料庫術語中，*內部聯結*產生的結果集中，第一個集合的每個項目都會為第二個集合中的每個相符項目出現一次。 如果第一個集合中的元素沒有相符的項目，就不會出現在結果集中。 C# 中 `join` 子句呼叫的 <xref:System.Linq.Enumerable.Join%2A> 方法會實作內部聯結。

本文示範如何執行內部聯結的四種變化：

- 簡單內部聯結，根據簡單的索引鍵將兩個資料來源的項目相互關聯。

- 內部聯結，根據「複合」的索引鍵將兩個資料來源的項目相互關聯。 複合索引鍵，也就是由多個值組成的索引鍵，可讓您根據多個屬性將項目相互關聯。

- 「多個聯結」，彼此附加的連續聯結作業。

- 使用群組聯結實作的內部聯結。

## <a name="example---simple-key-join"></a>範例 - 簡單索引鍵聯結

下例會建立兩個集合，包含兩個使用者定義型別的物件 `Person` 和 `Pet`。 查詢會使用 C# 的 `join` 子句來比對 `Person` 物件與其 `Owner` 是 `Person` 的 `Pet` 物件。 C# 的 `select` 子句會定義產生物件的外觀。 本例中，產生的物件是由擁有者名字和寵物名字組成的匿名型別。

[!code-csharp[CsLINQProgJoining#1](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_1.cs)]

請注意，其 `LastName` 是 "Huff" 的 `Person` 物件不會出現在結果集中，因為沒有任何 `Pet` 物件的 `Pet.Owner` 等於 `Person`。

## <a name="example---composite-key-join"></a>範例 - 複合索引鍵聯結

非僅根據一個屬性相互關聯的項目，您可以使用複合索引鍵根據多個屬性來比較項目。 若要這樣做，請為每個集合指定索引鍵選取器函式，以傳回包含要比較屬性的匿名型別。 如果您標示屬性，它們在每個索引鍵的匿名型別中必須有相同的標籤。 屬性也必須以相同的順序出現。

下例會使用 `Employee` 物件清單和 `Student` 物件清單來判斷哪些員工也是學生。 這兩種類型都有 <xref:System.String> 類型的 `FirstName` 和 `LastName` 屬性。 從每個清單的項目建立聯結索引鍵的函式會傳回包含每個項目的 `FirstName` 和 `LastName` 屬性的匿名型別。 聯結作業會比較這些複合索引鍵是否相等，並傳回每份清單中名字和姓氏相符的物件配對。

[!code-csharp[CsLINQProgJoining#2](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_2.cs)]

## <a name="example---multiple-join"></a>範例 - 多個聯結

彼此可以附加任何數目的聯結作業，以執行多個聯結。 C# 中每個 `join` 子句都會相互關聯指定的資料來源與上一個聯結的結果。

下例會建立三個集合︰`Person` 物件清單、`Cat` 物件清單和 `Dog` 物件清單。

C# 的第一個 `join` 子句會根據符合 `Cat.Owner` 的 `Person` 物件比對人員和貓。 它會傳回一系列包含 `Person` 物件和 `Cat.Name` 的匿名型別。

C# 的第二個 `join` 子句會根據以型別 `Person` 的 `Owner` 屬性組成的複合索引鍵和動物名稱的第一個字母，相互關聯第一個聯結傳回的匿名型別與所提供狗清單的 `Dog` 物件。 它會傳回一系列包含每個相符配對的 `Cat.Name` 和 `Dog.Name` 屬性的匿名型別。 因為這是內部聯結，所以只會傳回第一個資料來源中在第二個資料來源中有相符項目的這些物件。

[!code-csharp[CsLINQProgJoining#3](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_3.cs)]

## <a name="example---inner-join-by-using-grouped-join"></a>範例 - 使用群組聯結的內部聯結

下例會示範如何使用群組聯結實作內部聯結。

在 `query1` 中，`Person` 物件清單是根據符合 `Pet.Owner` 屬性的 `Person` 以群組方式聯結至 `Pet` 物件清單。 群組聯結會建立中繼群組的集合，其中每個群組都包含一個 `Person` 物件和一系列的相符 `Pet` 物件。

將第二個 `from` 子句加入查詢中，這個系列的序列就會結合 (或扁平化) 成一個較長的序列。 最終序列的項目型別是由 `select` 子句指定。 本例中的型別是匿名型別，其包含每個相符配對的 `Person.FirstName` 和 `Pet.Name` 屬性。

`query1` 的結果相當於使用不含 `into` 子句的 `join` 子句執行內部聯結所取得的結果集。 `query2` 變數會示範此對等查詢。

[!code-csharp[CsLINQProgJoining#4](~/samples/snippets/csharp/concepts/linq/how-to-perform-inner-joins_4.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [執行群組聯結](perform-grouped-joins.md)  
- [執行左方外部聯結](perform-left-outer-joins.md)  
- [匿名型別](../programming-guide/classes-and-structs/anonymous-types.md)  