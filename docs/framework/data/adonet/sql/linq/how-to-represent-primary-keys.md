---
title: HOW TO：表示主索引鍵
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: dcb8929c9cd9a7b88f19d760b70117a1092760f9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59295584"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="84afd-102">HOW TO：表示主索引鍵</span><span class="sxs-lookup"><span data-stu-id="84afd-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="84afd-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>屬性上的<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定屬性或欄位來表示資料庫資料行的主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="84afd-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="84afd-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="84afd-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="84afd-105">不支援計算資料行作為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="84afd-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="84afd-106">若要指定屬性或欄位做為主索引鍵</span><span class="sxs-lookup"><span data-stu-id="84afd-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="84afd-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="84afd-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="84afd-108">將值指定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="84afd-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84afd-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84afd-109">See also</span></span>

- [<span data-ttu-id="84afd-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="84afd-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="84afd-111">HOW TO：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="84afd-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
