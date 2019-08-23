---
title: 作法：表示計算資料行
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: 01c3442448285893ebb476ed11889e073065d4d8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943537"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="a7fd8-102">作法：表示計算資料行</span><span class="sxs-lookup"><span data-stu-id="a7fd8-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="a7fd8-103">使用屬性[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ( <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute) 上的<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>屬性 (property), 表示其內容為計算結果的資料行。</span><span class="sxs-lookup"><span data-stu-id="a7fd8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="a7fd8-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>。</span><span class="sxs-lookup"><span data-stu-id="a7fd8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a7fd8-105">不支援以計算資料行做為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a7fd8-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="a7fd8-106">若要表示計算資料行</span><span class="sxs-lookup"><span data-stu-id="a7fd8-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="a7fd8-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="a7fd8-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="a7fd8-108">將公式的字串表示指派至 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="a7fd8-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7fd8-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7fd8-109">See also</span></span>

- [<span data-ttu-id="a7fd8-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="a7fd8-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a7fd8-111">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="a7fd8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
