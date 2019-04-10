---
title: HOW TO：將資料行表示為時間戳記或版本資料行
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: db73bf4880d8f5556247f7b037fca24b0ddc56d6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59297885"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="5ebb4-102">HOW TO：將資料行表示為時間戳記或版本資料行</span><span class="sxs-lookup"><span data-stu-id="5ebb4-102">How to: Represent Columns as Timestamp or Version Columns</span></span>
<span data-ttu-id="5ebb4-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>屬性<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定欄位或屬性，以表示資料庫資料行保存資料庫時間戳記或版本號碼。</span><span class="sxs-lookup"><span data-stu-id="5ebb4-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="5ebb4-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="5ebb4-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="5ebb4-105">若要指定欄位或屬性以表示時間戳記或版本資料行</span><span class="sxs-lookup"><span data-stu-id="5ebb4-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="5ebb4-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="5ebb4-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="5ebb4-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="5ebb4-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebb4-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ebb4-108">See also</span></span>

- [<span data-ttu-id="5ebb4-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="5ebb4-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="5ebb4-110">HOW TO：指定用於測試並行衝突的成員</span><span class="sxs-lookup"><span data-stu-id="5ebb4-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="5ebb4-111">HOW TO：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="5ebb4-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
