---
title: 作法：將資料行表示為可存放 Null 值的資料行
ms.date: 03/30/2017
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
ms.openlocfilehash: 00a837467010c2d8a9f0ca16d6aba2fc5f4c973f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781817"
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="a6198-102">作法：將資料行表示為可存放 Null 值的資料行</span><span class="sxs-lookup"><span data-stu-id="a6198-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="a6198-103">使用屬性（ <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute）上的屬性（property），指定相關聯的資料庫資料行可以保留null值。<xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6198-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="a6198-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>。</span><span class="sxs-lookup"><span data-stu-id="a6198-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="a6198-105">若要指定資料行允許 null 值</span><span class="sxs-lookup"><span data-stu-id="a6198-105">To designate a column as allowing null values</span></span>  
  
1. <span data-ttu-id="a6198-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="a6198-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="a6198-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> 屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a6198-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6198-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6198-108">See also</span></span>

- [<span data-ttu-id="a6198-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="a6198-109">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a6198-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="a6198-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
