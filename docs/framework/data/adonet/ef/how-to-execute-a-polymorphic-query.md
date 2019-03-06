---
title: HOW TO：執行多型查詢
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2f05da1e-845b-4f14-83e4-c6353a850553
ms.openlocfilehash: 08ae5722267ef781ed6bee59c7895269f63a75e5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355531"
---
# <a name="how-to-execute-a-polymorphic-query"></a><span data-ttu-id="a0742-102">HOW TO：執行多型查詢</span><span class="sxs-lookup"><span data-stu-id="a0742-102">How to: Execute a Polymorphic Query</span></span>

<span data-ttu-id="a0742-103">本主題說明如何執行多型[!INCLUDE[esql](../../../../../includes/esql-md.md)]使用查詢[OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md)運算子。</span><span class="sxs-lookup"><span data-stu-id="a0742-103">This topic shows how to execute a polymorphic [!INCLUDE[esql](../../../../../includes/esql-md.md)] query using the [OFTYPE](../../../../../docs/framework/data/adonet/ef/language-reference/oftype-entity-sql.md) operator.</span></span>

### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="a0742-104">執行此範例中的程式碼</span><span class="sxs-lookup"><span data-stu-id="a0742-104">To run the code in this example</span></span>

1. <span data-ttu-id="a0742-105">新增[School 模型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))至您的專案，並設定您的專案使用 Entity Framework。</span><span class="sxs-lookup"><span data-stu-id="a0742-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="a0742-106">如需詳細資訊，請參閱[如何：使用 Entity Data Model 精靈](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="a0742-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>

2. <span data-ttu-id="a0742-107">在應用程式的字碼頁中加入下列 `using` 陳述式 (在 Visual Basic 中為 `Imports`)：</span><span class="sxs-lookup"><span data-stu-id="a0742-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>

    [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
    [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]

3. <span data-ttu-id="a0742-108">修改概念模型以擁有每個階層的資料表繼承中的步驟[逐步解說：對應每個階層的資料表繼承](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="a0742-108">Modify the conceptual model to have a table-per-hierarchy inheritance by following the steps in [Walkthrough: Mapping Inheritance - Table-per-Hierarchy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716683(v=vs.100)).</span></span>

## <a name="example"></a><span data-ttu-id="a0742-109">範例</span><span class="sxs-lookup"><span data-stu-id="a0742-109">Example</span></span>

<span data-ttu-id="a0742-110">下列範例會使用 OFTYPE 運算子，從 `OnsiteCourses` 的集合中取得並顯示只有 `Courses` 的集合。</span><span class="sxs-lookup"><span data-stu-id="a0742-110">The following example uses an OFTYPE operator to get and display a collection of only `OnsiteCourses` from a collection of `Courses`.</span></span>

[!code-csharp[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#polymorphicquery)]
[!code-vb[DP EntityServices Concepts#PolymorphicQuery](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#polymorphicquery)]

## <a name="see-also"></a><span data-ttu-id="a0742-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0742-111">See also</span></span>

- [<span data-ttu-id="a0742-112">Entity Framework 的 EntityClient 提供者</span><span class="sxs-lookup"><span data-stu-id="a0742-112">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="a0742-113">Entity SQL 語言</span><span class="sxs-lookup"><span data-stu-id="a0742-113">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
