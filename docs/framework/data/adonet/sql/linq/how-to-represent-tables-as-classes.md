---
title: HOW TO：將資料表表示為類別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 49e7d6768d8739bba94c9e8d38bcc582c8bd6e4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902898"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="fb798-102">HOW TO：將資料表表示為類別</span><span class="sxs-lookup"><span data-stu-id="fb798-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="fb798-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.TableAttribute>屬性來指定資料庫資料表相關聯的實體類別的類別。</span><span class="sxs-lookup"><span data-stu-id="fb798-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="fb798-104">若要將類別對應至資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="fb798-104">To map a class to a database table</span></span>  
  
-   <span data-ttu-id="fb798-105">將 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性加入至類別宣告。</span><span class="sxs-lookup"><span data-stu-id="fb798-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb798-106">範例</span><span class="sxs-lookup"><span data-stu-id="fb798-106">Example</span></span>  
 <span data-ttu-id="fb798-107">下列程式碼所建立的 `Customer` 類別，可做為與 `Customers` 資料庫資料表相關聯的實體類別。</span><span class="sxs-lookup"><span data-stu-id="fb798-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="fb798-108">如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fb798-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="fb798-109">如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb798-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb798-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb798-110">See also</span></span>

- [<span data-ttu-id="fb798-111">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="fb798-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="fb798-112">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="fb798-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
