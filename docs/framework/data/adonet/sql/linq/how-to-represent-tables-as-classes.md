---
title: HOW TO：將資料表表示為類別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: ff943fbc7ae137128d6c635fd2366ad14cf70d15
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64620024"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="67de6-102">HOW TO：將資料表表示為類別</span><span class="sxs-lookup"><span data-stu-id="67de6-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="67de6-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.TableAttribute>屬性來指定資料庫資料表相關聯的實體類別的類別。</span><span class="sxs-lookup"><span data-stu-id="67de6-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="67de6-104">若要將類別對應至資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="67de6-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="67de6-105">將 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性加入至類別宣告。</span><span class="sxs-lookup"><span data-stu-id="67de6-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67de6-106">範例</span><span class="sxs-lookup"><span data-stu-id="67de6-106">Example</span></span>  
 <span data-ttu-id="67de6-107">下列程式碼所建立的 `Customer` 類別，可做為與 `Customers` 資料庫資料表相關聯的實體類別。</span><span class="sxs-lookup"><span data-stu-id="67de6-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="67de6-108">如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="67de6-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="67de6-109">如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="67de6-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67de6-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67de6-110">See also</span></span>

- [<span data-ttu-id="67de6-111">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="67de6-111">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="67de6-112">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="67de6-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
