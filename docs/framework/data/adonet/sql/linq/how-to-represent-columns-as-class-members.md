---
title: HOW TO：將資料行表示為類別成員
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7ab28021-4d15-4d9c-bf2e-6ccc0daa7d1a
ms.openlocfilehash: 74966dd1661faa43df334987b2e3b0e84eff3446
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037853"
---
# <a name="how-to-represent-columns-as-class-members"></a><span data-ttu-id="63ad0-102">HOW TO：將資料行表示為類別成員</span><span class="sxs-lookup"><span data-stu-id="63ad0-102">How to: Represent Columns as Class Members</span></span>
<span data-ttu-id="63ad0-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute>欄位或屬性相關聯的資料庫資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="63ad0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to associate a field or property with a database column.</span></span>  
  
### <a name="to-map-a-field-or-property-to-a-database-column"></a><span data-ttu-id="63ad0-104">若要將欄位或屬性 (Property) 對應至資料庫資料行</span><span class="sxs-lookup"><span data-stu-id="63ad0-104">To map a field or property to a database column</span></span>  
  
- <span data-ttu-id="63ad0-105">將 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute) 加入至屬性 (Property) 或欄位宣告。</span><span class="sxs-lookup"><span data-stu-id="63ad0-105">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to the property or field declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63ad0-106">範例</span><span class="sxs-lookup"><span data-stu-id="63ad0-106">Example</span></span>  
 <span data-ttu-id="63ad0-107">下列程式碼會將 `CustomerID` 類別中的 `Customer` 欄位對應至 `CustomerID` 資料庫資料表中的 `Customers` 資料行。</span><span class="sxs-lookup"><span data-stu-id="63ad0-107">The following code maps the `CustomerID` field in the `Customer` class to the `CustomerID` column in the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#2)]
 [!code-vb[DLinqCustomize#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#2)]  
  
 <span data-ttu-id="63ad0-108">如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="63ad0-108">You do not have to specify the <xref:System.Data.Linq.Mapping.DataAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="63ad0-109">如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="63ad0-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63ad0-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63ad0-110">See also</span></span>

- [<span data-ttu-id="63ad0-111">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="63ad0-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="63ad0-112">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="63ad0-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
