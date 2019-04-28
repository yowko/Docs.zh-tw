---
title: HOW TO：將資料行表示為資料庫產生的資料行
ms.date: 03/30/2017
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
ms.openlocfilehash: 2803697c668a8e1dbbeb426ea41b64878f70c145
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903483"
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="74051-102">HOW TO：將資料行表示為資料庫產生的資料行</span><span class="sxs-lookup"><span data-stu-id="74051-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="74051-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>屬性上的<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定欄位或屬性，以表示資料庫產生的資料行。</span><span class="sxs-lookup"><span data-stu-id="74051-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="74051-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>。</span><span class="sxs-lookup"><span data-stu-id="74051-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="74051-105">若要指定欄位或屬性以表示資料庫產生的資料行</span><span class="sxs-lookup"><span data-stu-id="74051-105">To designate a field or property as representing a database-generated column</span></span>  
  
1. <span data-ttu-id="74051-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="74051-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="74051-107">將屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="74051-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74051-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74051-108">See also</span></span>

- [<span data-ttu-id="74051-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="74051-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
- [<span data-ttu-id="74051-110">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="74051-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
