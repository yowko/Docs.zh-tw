---
title: 作法：表示主索引鍵
ms.date: 03/30/2017
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
ms.openlocfilehash: 02570176c8aef5cfdc7ba09fd6976f430900e8df
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166231"
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="85255-102">作法：表示主索引鍵</span><span class="sxs-lookup"><span data-stu-id="85255-102">How to: Represent Primary Keys</span></span>

<span data-ttu-id="85255-103">您可以使用屬性（attribute）上的屬性（property） [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> <xref:System.Data.Linq.Mapping.ColumnAttribute> 來指定屬性（property）或欄位（property）來表示資料庫資料行的主鍵。</span><span class="sxs-lookup"><span data-stu-id="85255-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="85255-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="85255-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="85255-105">不支援以計算資料行做為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="85255-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="85255-106">若要指定屬性或欄位做為主索引鍵</span><span class="sxs-lookup"><span data-stu-id="85255-106">To designate a property or field as a primary key</span></span>  
  
1. <span data-ttu-id="85255-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="85255-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="85255-108">將值指定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="85255-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85255-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85255-109">See also</span></span>

- [<span data-ttu-id="85255-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="85255-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="85255-111">作法：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="85255-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
