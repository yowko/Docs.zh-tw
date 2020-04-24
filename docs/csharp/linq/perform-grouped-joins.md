---
title: 執行群組聯結 (C# 中的 LINQ)
description: 了解如何使用 C# 中的 LINQ 執行群組聯結。
ms.date: 04/22/2020
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.openlocfilehash: 740a861da7dfb9653a874d5baf67eeb2030555b4
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135746"
---
# <a name="perform-grouped-joins"></a>執行群組聯結

群組聯結適合用來產生階層式資料結構。 它會配對第一個集合中的項目和第二個集合中一組相互關聯的項目。

例如，名為 `Student` 的類別或關聯式資料庫資料表可能包含兩個欄位︰`Id` 和 `Name`。 名為 `Course` 的第二個類別或關聯式資料庫資料表可能包含兩個欄位︰`StudentId` 和 `CourseTitle`。 這兩個資料來源的群組聯結，以相符的 `Student.Id` 和 `Course.StudentId` 為基礎，會將每個 `Student` 分組到 `Course` 物件集合 (可能是空的)。

> [!NOTE]
> 無論第二個集合中是否找到相互關聯的項目，第一個集合的每個項目都會出現在群組聯結的結果集中。 如果找不到任何相互關聯的項目，該項目之相互關聯項目的序列是空的。 因此，結果選取器可以存取第一個集合的每個項目。 和非群組聯結中的結果選取器不同，它無法存取和第二個集合沒有相符項目的第一個集合項目。

> [!WARNING]
> <xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType>在傳統關係資料庫詞彙中沒有直接的對等用法。 不過，這個方法會執行內部聯結和左方外部聯結的超集合。 這兩種作業都可以根據群組聯結來撰寫。 如需詳細資訊，請參閱[Join 作業](../programming-guide/concepts/linq/join-operations.md)和[Entity Framework Core，GroupJoin](https://docs.microsoft.com/ef/core/querying/complex-query-operators#groupjoin)。

本文中的第一個範例示範如何執行群組聯結。 第二個範例會示範如何使用群組聯結建立 XML 元素。

## <a name="example---group-join"></a>範例 - 群組聯結

下例會根據符合 `Pet.Owner` 屬性的 `Person`，執行型別 `Person` 和 `Pet` 的物件群組聯結。 和非群組聯結不同，它會針對每個相符項目產生項目配對，群組聯結只會針對第一個集合的每個項目產生結果物件，在本例中為 `Person` 物件。 第二個集合的對應項目，在本例中為 `Pet` 物件，會群組成集合。 最後，結果選取器函式會為每個符合項目建立匿名型別，包含 `Person.FirstName` 和 `Pet` 物件集合。

[!code-csharp[CsLINQProgJoining#5](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]

## <a name="example---group-join-to-create-xml"></a>範例 - 群組聯結以建立 XML

群組聯結最適合使用 LINQ to XML 建立 XML。 下例類似上例，只不過它不是建立匿名型別，而是結果選取器函式會建立表示已加入物件的 XML 元素。

[!code-csharp[CsLINQProgJoining#6](~/samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Linq.Enumerable.Join%2A>
- <xref:System.Linq.Enumerable.GroupJoin%2A>
- [執行內部聯結](perform-inner-joins.md)
- [執行左方外部聯結](perform-left-outer-joins.md)
- [匿名型別](../programming-guide/classes-and-structs/anonymous-types.md)
