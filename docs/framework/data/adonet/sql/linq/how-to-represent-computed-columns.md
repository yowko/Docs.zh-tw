---
title: 如何：表示計算資料行
ms.date: 03/30/2017
ms.assetid: 4025f1fd-9dfa-46c0-b04f-34e8bc7957a2
ms.openlocfilehash: c53c781e8d4ec6836e032120816c3ef55de2ae0d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353097"
---
# <a name="how-to-represent-computed-columns"></a><span data-ttu-id="ee18f-102">如何：表示計算資料行</span><span class="sxs-lookup"><span data-stu-id="ee18f-102">How to: Represent Computed Columns</span></span>
<span data-ttu-id="ee18f-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>屬性<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性以表示其內容為計算結果的資料行。</span><span class="sxs-lookup"><span data-stu-id="ee18f-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to represent a column whose contents are the result of calculation.</span></span>  
  
 <span data-ttu-id="ee18f-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>。</span><span class="sxs-lookup"><span data-stu-id="ee18f-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="ee18f-105"> 不支援以計算資料行做為主索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ee18f-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-represent-a-computed-column"></a><span data-ttu-id="ee18f-106">若要表示計算資料行</span><span class="sxs-lookup"><span data-stu-id="ee18f-106">To represent a computed column</span></span>  
  
1.  <span data-ttu-id="ee18f-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="ee18f-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="ee18f-108">將公式的字串表示指派至 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="ee18f-108">Assign a string representation of the formula to the <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee18f-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee18f-109">See Also</span></span>  
 [<span data-ttu-id="ee18f-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="ee18f-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="ee18f-111">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="ee18f-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
