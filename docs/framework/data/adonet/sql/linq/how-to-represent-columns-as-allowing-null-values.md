---
title: HOW TO：資料行表示為允許 Null 值
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ba362e45c8694dbb30e977b3d9f25702ee9dea48
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715526"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="c99f2-102">HOW TO：資料行表示為允許 Null 值</span><span class="sxs-lookup"><span data-stu-id="c99f2-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="c99f2-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>屬性上的<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定相關聯的資料庫資料行可以保存 null 值。</span><span class="sxs-lookup"><span data-stu-id="c99f2-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="c99f2-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>。</span><span class="sxs-lookup"><span data-stu-id="c99f2-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="c99f2-105">若要指定資料行允許 null 值</span><span class="sxs-lookup"><span data-stu-id="c99f2-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="c99f2-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="c99f2-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="c99f2-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="c99f2-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c99f2-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c99f2-108">See also</span></span>
- [<span data-ttu-id="c99f2-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="c99f2-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="c99f2-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="c99f2-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
