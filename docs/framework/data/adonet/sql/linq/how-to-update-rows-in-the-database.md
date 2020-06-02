---
title: 如何：更新資料庫中的資料列
description: 瞭解如何藉由修改資料表相關集合中 LINQ to SQL 物件，來更新資料庫中的資料列。 LINQ to SQL 會將新增專案轉譯為 SQL UPDATE 命令。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
ms.openlocfilehash: f25efb91fb5a83fb1c7c109bd018c8210edaec8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286335"
---
# <a name="how-to-update-rows-in-the-database"></a>如何：更新資料庫中的資料列

您可以修改與集合相關聯之物件的成員值 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> ，然後將變更提交至資料庫，藉以更新資料庫中的資料列。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]將您的變更轉譯成適當的 SQL `UPDATE` 命令。

> [!NOTE]
> 您可以覆寫 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 預設方法，以執行 `Insert`、`Update` 和 `Delete` 資料庫作業。 如需詳細資訊，請參閱[自訂插入、更新和刪除作業](customizing-insert-update-and-delete-operations.md)。
>
> 使用 Visual Studio 的開發人員可以使用物件關聯式設計工具，針對相同的目的來開發預存程式。

下列步驟假設一個有效的 <xref:System.Data.Linq.DataContext> 會將您連接至 Northwind 資料庫。 如需詳細資訊，請參閱[如何：連接到資料庫](how-to-connect-to-a-database.md)。

### <a name="to-update-a-row-in-the-database"></a>若要更新資料庫中的資料列

1. 查詢資料庫，以找出要更新的資料列。

2. 對結果 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件中的成員值進行所需的變更。

3. 將變更提交至資料庫。

## <a name="example"></a>範例

下列程式碼範例會查詢資料庫中的訂單編號 11000，然後變更結果 `ShipName` 物件中 `ShipVia` 和 `Order` 的值。 最後，這些成員值的變更會提交至資料庫，成為 `ShipName` 和 `ShipVia` 資料行的變更。

[!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
[!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]

## <a name="see-also"></a>另請參閱

- [如何：管理變更衝突](how-to-manage-change-conflicts.md)
- [如何：指派用來執行更新、插入和刪除的預存程序 (O/R 設計工具)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
- [變更資料和提交](making-and-submitting-data-changes.md)
