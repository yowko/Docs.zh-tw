---
title: "如何：指定資料庫的資料類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 60f07a629c981eb0ad72f7c3e2d8537d5ca77515
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="22c00-102">如何：指定資料庫的資料類型</span><span class="sxs-lookup"><span data-stu-id="22c00-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="22c00-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>屬性<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定 T-SQL 資料表宣告中定義的資料行的確切文字。</span><span class="sxs-lookup"><span data-stu-id="22c00-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="22c00-104">只有在計劃使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 建立資料庫執行個體時，才必須指定 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="22c00-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="22c00-105">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>。</span><span class="sxs-lookup"><span data-stu-id="22c00-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="22c00-106">若要指定文字以定義 T-SQL 資料表中的資料型別</span><span class="sxs-lookup"><span data-stu-id="22c00-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="22c00-107">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="22c00-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="22c00-108">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 屬性的值設定為 T-SQL 使用的確切文字。</span><span class="sxs-lookup"><span data-stu-id="22c00-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c00-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="22c00-109">See Also</span></span>  
 [<span data-ttu-id="22c00-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="22c00-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="22c00-111">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="22c00-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
