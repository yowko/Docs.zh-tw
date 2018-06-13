---
title: 如何：將資料行表示為資料庫產生的資料行
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: f6b127208ae359b43f273f54d7b5c72933c2eba6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353737"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="77cb9-102">如何：將資料行表示為資料庫產生的資料行</span><span class="sxs-lookup"><span data-stu-id="77cb9-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="77cb9-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>屬性<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定欄位或屬性，以表示資料庫產生的資料行。</span><span class="sxs-lookup"><span data-stu-id="77cb9-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="77cb9-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>。</span><span class="sxs-lookup"><span data-stu-id="77cb9-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="77cb9-105">若要指定欄位或屬性以表示資料庫產生的資料行</span><span class="sxs-lookup"><span data-stu-id="77cb9-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="77cb9-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="77cb9-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="77cb9-107">將屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="77cb9-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77cb9-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77cb9-108">See Also</span></span>  
 [<span data-ttu-id="77cb9-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="77cb9-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="77cb9-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="77cb9-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
