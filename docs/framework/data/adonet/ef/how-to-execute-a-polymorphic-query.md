---
title: 作法：執行多型查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 49e0a6b44af0729959fabf6278cc6d8ecf37a16b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251504"
---
# <a name="how-to-execute-a-polymorphic-query"></a>作法：執行多型查詢

本主題說明如何使用[OFTYPE](./language-reference/oftype-entity-sql.md)運算子執行[!INCLUDE[esql](../../../../../includes/esql-md.md)]多型查詢。

### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼

1. 將[School 模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))新增至您的專案, 並將專案設定為使用 Entity Framework。 如需詳細資訊，請參閱[如何：使用實體資料模型 Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。

2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. 遵循逐步解說: 下列步驟[, 修改概念模型, 使其具有每個階層的資料表繼承。對應繼承-每個](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))階層的資料表。

## <a name="example"></a>範例

下列範例會使用 OFTYPE 運算子，從 `OnsiteCourses` 的集合中取得並顯示只有 `Courses` 的集合。

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>另請參閱

- [Entity Framework 的 EntityClient 提供者](entityclient-provider-for-the-entity-framework.md)
- [Entity SQL 語言](./language-reference/entity-sql-language.md)
