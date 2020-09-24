---
title: 作法：將資料行表示為類別成員
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: e73b017b5a500a8c48b3fe22557f6c6619f3b227
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166348"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="a24e0-102">作法：將資料行表示為類別成員</span><span class="sxs-lookup"><span data-stu-id="a24e0-102">How to: Represent Columns as Class Members</span></span>

<span data-ttu-id="a24e0-103">您 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> 可以使用屬性，將欄位或屬性與資料庫資料行產生關聯。</span><span class="sxs-lookup"><span data-stu-id="a24e0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="a24e0-104">若要將欄位或屬性 (Property) 對應至資料庫資料行</span><span class="sxs-lookup"><span data-stu-id="a24e0-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="a24e0-105">將 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute) 加入至屬性 (Property) 或欄位宣告。</span><span class="sxs-lookup"><span data-stu-id="a24e0-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a24e0-106">範例</span><span class="sxs-lookup"><span data-stu-id="a24e0-106">Example</span></span>  

 <span data-ttu-id="a24e0-107">下列程式碼會將 `CustomerID` 類別中的 `Customer` 欄位對應至 `CustomerID` 資料庫資料表中的 `Customers` 資料行。</span><span class="sxs-lookup"><span data-stu-id="a24e0-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="a24e0-108">如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a24e0-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="a24e0-109">如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="a24e0-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a24e0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a24e0-110">See also</span></span>

- [<span data-ttu-id="a24e0-111">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="a24e0-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="a24e0-112">作法：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="a24e0-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
