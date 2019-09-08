---
title: 作法：將資料表表示為類別
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 84dda12b-88a2-4cd2-92b3-8db87b28d14c
ms.openlocfilehash: 1169def4e0180b1d14103d4a968ff3ed56f63d0c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781755"
---
# <a name="how-to-represent-tables-as-classes"></a><span data-ttu-id="759ae-102">作法：將資料表表示為類別</span><span class="sxs-lookup"><span data-stu-id="759ae-102">How to: Represent Tables as Classes</span></span>
<span data-ttu-id="759ae-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 使用屬性來指定類別，做為與資料庫資料表相關<xref:System.Data.Linq.Mapping.TableAttribute>聯的實體類別。</span><span class="sxs-lookup"><span data-stu-id="759ae-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.TableAttribute> attribute to designate a class as an entity class associated with a database table.</span></span>  
  
### <a name="to-map-a-class-to-a-database-table"></a><span data-ttu-id="759ae-104">若要將類別對應至資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="759ae-104">To map a class to a database table</span></span>  
  
- <span data-ttu-id="759ae-105">將 <xref:System.Data.Linq.Mapping.TableAttribute> 屬性加入至類別宣告。</span><span class="sxs-lookup"><span data-stu-id="759ae-105">Add the <xref:System.Data.Linq.Mapping.TableAttribute> attribute to the class declaration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="759ae-106">範例</span><span class="sxs-lookup"><span data-stu-id="759ae-106">Example</span></span>  
 <span data-ttu-id="759ae-107">下列程式碼所建立的 `Customer` 類別，可做為與 `Customers` 資料庫資料表相關聯的實體類別。</span><span class="sxs-lookup"><span data-stu-id="759ae-107">The following code establishes the `Customer` class as an entity class that is associated with the `Customers` database table.</span></span>  
  
 [!code-csharp[DLinqCustomize#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#1)]
 [!code-vb[DLinqCustomize#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#1)]  
  
 <span data-ttu-id="759ae-108">如果可以推斷名稱，您就不必指定 <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="759ae-108">You do not have to specify the <xref:System.Data.Linq.Mapping.TableAttribute.Name%2A> property if the name can be inferred.</span></span> <span data-ttu-id="759ae-109">如果您未指定名稱，則會假設名稱就是與屬性或欄位名稱相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="759ae-109">If you do not specify a name, the name is presumed to be the same name as that of the property or field.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759ae-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="759ae-110">See also</span></span>

- [<span data-ttu-id="759ae-111">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="759ae-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="759ae-112">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="759ae-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
