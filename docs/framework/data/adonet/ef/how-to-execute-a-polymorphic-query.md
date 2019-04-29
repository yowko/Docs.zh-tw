---
title: HOW TO：執行多型查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 08ae5722267ef781ed6bee59c7895269f63a75e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606186"
---
# <a name="how-to-execute-a-polymorphic-query"></a>HOW TO：執行多型查詢

本主題說明如何執行多型[!INCLUDE[esql](../../../../../includes/esql-md.md)]使用查詢[OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)運算子。

### <a name="to-run-the-code-in-this-example"></a>執行此範例中的程式碼

1. 新增[School 模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))至您的專案，並設定您的專案使用 Entity Framework。 如需詳細資訊，請參閱[如何：使用 Entity Data Model 精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。

2. 在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. 修改概念模型以擁有每個階層的資料表繼承中的步驟[逐步解說：對應每個階層的資料表繼承](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))。

## <a name="example"></a>範例

下列範例會使用 OFTYPE 運算子，從 `OnsiteCourses` 的集合中取得並顯示只有 `Courses` 的集合。

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a>另請參閱

- [Entity Framework 的 EntityClient 提供者](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [Entity SQL 語言](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
