---
title: HOW TO：指定資料庫名稱
ms.date: 03/30/2017
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
ms.openlocfilehash: 1c694678dc3a60cf91dea62f2a17973b396e2b19
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184518"
---
# <a name="how-to-specify-database-names"></a><span data-ttu-id="b1794-102">HOW TO：指定資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="b1794-102">How to: Specify Database Names</span></span>
<span data-ttu-id="b1794-103">在 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Attribute) 上使用 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 屬性 (Property)，可在連接未提供名稱時指定資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="b1794-103">Use the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property on a <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to specify the name of a database when a name is not supplied by the connection.</span></span>  
  
 <span data-ttu-id="b1794-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>。</span><span class="sxs-lookup"><span data-stu-id="b1794-104">For code samples, see <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-the-database"></a><span data-ttu-id="b1794-105">若要指定資料庫的名稱</span><span class="sxs-lookup"><span data-stu-id="b1794-105">To specify the name of the database</span></span>  
  
1.  <span data-ttu-id="b1794-106">將 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 屬性 (Attribute) 加入至資料庫的類別宣告。</span><span class="sxs-lookup"><span data-stu-id="b1794-106">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute to the class declaration for the database.</span></span>  
  
2.  <span data-ttu-id="b1794-107">將 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.DatabaseAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="b1794-107">Add the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property to the <xref:System.Data.Linq.Mapping.DatabaseAttribute> attribute.</span></span>  
  
3.  <span data-ttu-id="b1794-108">將 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> 屬性 (Property) 值設定為想要指定的名稱。</span><span class="sxs-lookup"><span data-stu-id="b1794-108">Set the <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> property value to the name that you want to specify.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1794-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1794-109">See also</span></span>

- [<span data-ttu-id="b1794-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="b1794-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="b1794-111">HOW TO：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="b1794-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
