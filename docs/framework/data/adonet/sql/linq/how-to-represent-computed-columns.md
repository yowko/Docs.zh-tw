---
title: 作法：表示計算資料行
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: d952a6c22cd96bbc89aeebfa4b13e9727a363c73
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166320"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="b9cc6-102">作法：表示計算資料行</span><span class="sxs-lookup"><span data-stu-id="b9cc6-102">How to: Represent Computed Columns</span></span>

<span data-ttu-id="b9cc6-103">使用屬性（ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> attribute）上的屬性 <xref:System.Data.Linq.Mapping.ColumnAttribute> （property）來代表其內容為計算結果的資料行。</span><span class="sxs-lookup"><span data-stu-id="b9cc6-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="b9cc6-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>。</span><span class="sxs-lookup"><span data-stu-id="b9cc6-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="b9cc6-105">不支援以計算資料行做為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b9cc6-105">does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="b9cc6-106">若要表示計算資料行</span><span class="sxs-lookup"><span data-stu-id="b9cc6-106">To represent a computed column</span></span>  
  
1. <span data-ttu-id="b9cc6-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="b9cc6-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="b9cc6-108">將公式的字串表示指派至 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="b9cc6-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9cc6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9cc6-109">See also</span></span>

- [<span data-ttu-id="b9cc6-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="b9cc6-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b9cc6-111">作法：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="b9cc6-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
