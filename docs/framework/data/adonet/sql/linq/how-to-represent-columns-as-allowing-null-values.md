---
title: HOW TO：將資料行表示為可存放 Null 值的資料行
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: ef8fa87963b91ef7140fbaefb657fc7904604b5b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902911"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="91a2f-102">HOW TO：將資料行表示為可存放 Null 值的資料行</span><span class="sxs-lookup"><span data-stu-id="91a2f-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="91a2f-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>屬性上的<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定相關聯的資料庫資料行可以保存 null 值。</span><span class="sxs-lookup"><span data-stu-id="91a2f-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="91a2f-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>。</span><span class="sxs-lookup"><span data-stu-id="91a2f-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="91a2f-105">若要指定資料行允許 null 值</span><span class="sxs-lookup"><span data-stu-id="91a2f-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="91a2f-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="91a2f-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="91a2f-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="91a2f-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a2f-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91a2f-108">See also</span></span>

- [<span data-ttu-id="91a2f-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="91a2f-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="91a2f-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="91a2f-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
