---
title: 作法：將資料行表示為時間戳記或版本資料行
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: cc8538ab7b2ecf5183cfb97995c04648493a369f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191745"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a><span data-ttu-id="37f59-102">作法：將資料行表示為時間戳記或版本資料行</span><span class="sxs-lookup"><span data-stu-id="37f59-102">How to: Represent Columns as Timestamp or Version Columns</span></span>

<span data-ttu-id="37f59-103">您 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 可以使用屬性（ <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute）屬性（attribute）來指定欄位或屬性（property），以代表保存資料庫時間戳記或版本號碼的資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="37f59-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property of the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database column that holds database timestamps or version numbers.</span></span>  
  
 <span data-ttu-id="37f59-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="37f59-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a><span data-ttu-id="37f59-105">若要指定欄位或屬性以表示時間戳記或版本資料行</span><span class="sxs-lookup"><span data-stu-id="37f59-105">To designate a field or property as representing a timestamp or version column</span></span>  
  
1. <span data-ttu-id="37f59-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="37f59-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="37f59-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="37f59-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37f59-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37f59-108">See also</span></span>

- [<span data-ttu-id="37f59-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="37f59-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="37f59-110">作法：指定用於測試並行衝突的成員</span><span class="sxs-lookup"><span data-stu-id="37f59-110">How to: Specify Which Members are Tested for Concurrency Conflicts</span></span>](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [<span data-ttu-id="37f59-111">作法：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="37f59-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
