---
title: "如何：將資料行表示為資料庫產生的資料行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b36e7035b885985e70203146957cdfca92148b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="bf4e8-102">如何：將資料行表示為資料庫產生的資料行</span><span class="sxs-lookup"><span data-stu-id="bf4e8-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="bf4e8-103">使用[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>屬性<xref:System.Data.Linq.Mapping.ColumnAttribute>屬性來指定欄位或屬性，以表示資料庫產生的資料行。</span><span class="sxs-lookup"><span data-stu-id="bf4e8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="bf4e8-104">如需程式碼範例，請參閱 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>。</span><span class="sxs-lookup"><span data-stu-id="bf4e8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="bf4e8-105">若要指定欄位或屬性以表示資料庫產生的資料行</span><span class="sxs-lookup"><span data-stu-id="bf4e8-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="bf4e8-106">將 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> 屬性 (Property) 加入至 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute)。</span><span class="sxs-lookup"><span data-stu-id="bf4e8-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="bf4e8-107">將屬性 (Property) 值設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="bf4e8-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf4e8-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf4e8-108">See Also</span></span>  
 [<span data-ttu-id="bf4e8-109">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="bf4e8-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="bf4e8-110">如何： 使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="bf4e8-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
