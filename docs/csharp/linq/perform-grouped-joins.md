---
title: "執行群組聯結"
description: "如何執行群組聯結。"
keywords: ".NET、.NET Core、C#"
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: 9667daf9-a5fd-4b43-a5c4-a9c2b744000e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 0410c5f673e61f91c00a69cb1659e0d72852f128
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="perform-grouped-joins"></a>執行群組聯結

群組聯結適合用來產生階層式資料結構。 它會配對第一個集合中的項目和第二個集合中一組相互關聯的項目。  
  
 例如，名為 `Student` 的類別或關聯式資料庫資料表可能包含兩個欄位︰`Id` 和 `Name`。 名為 `Course` 的第二個類別或關聯式資料庫資料表可能包含兩個欄位︰`StudentId` 和 `CourseTitle`。 這兩個資料來源的群組聯結，以相符的 `Student.Id` 和 `Course.StudentId` 為基礎，會將每個 `Student` 分組到 `Course` 物件集合 (可能是空的)。  
  
> [!NOTE]
>  無論第二個集合中是否找到相互關聯的項目，第一個集合的每個項目都會出現在群組聯結的結果集中。 如果找不到任何相互關聯的項目，該項目之相互關聯項目的序列是空的。 因此，結果選取器可以存取第一個集合的每個項目。 和非群組聯結中的結果選取器不同，它無法存取和第二個集合沒有相符項目的第一個集合項目。  
  
 本主題中的第一個範例會示範如何執行群組聯結。 第二個範例會示範如何使用群組聯結建立 XML 元素。  
  
## <a name="example"></a>範例  
  
### <a name="group-join-example"></a>群組聯結範例  
 下例會根據符合 `Pet.Owner` 屬性的 `Person`，執行型別 `Person` 和 `Pet` 的物件群組聯結。 和非群組聯結不同，它會針對每個相符項目產生項目配對，群組聯結只會針對第一個集合的每個項目產生結果物件，在本例中為 `Person` 物件。 第二個集合的對應項目，在本例中為 `Pet` 物件，會群組成集合。 最後，結果選取器函式會為每個符合項目建立匿名型別，包含 `Person.FirstName` 和 `Pet` 物件集合。  
  
 [!code-cs[CsLINQProgJoining#5](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_1.cs)]  
  
## <a name="example"></a>範例  
  
### <a name="group-join-to-create-xml-example"></a>群組聯結以建立 XML 範例  
 群組聯結最適合使用 LINQ to XML 建立 XML。 下例類似上例，只不過它不是建立匿名型別，而是結果選取器函式會建立表示已加入物件的 XML 元素。  
  
 [!code-cs[CsLINQProgJoining#6](../../../samples/snippets/csharp/concepts/linq/how-to-perform-grouped-joins_2.cs)]  
 
## <a name="see-also"></a>請參閱  
 <xref:System.Linq.Enumerable.Join%2A>   
 <xref:System.Linq.Enumerable.GroupJoin%2A>   
 [執行內部聯結](perform-inner-joins.md)   
 [執行左方外部聯結](perform-left-outer-joins.md)   
 [匿名型別](../programming-guide/classes-and-structs/anonymous-types.md)   
 

