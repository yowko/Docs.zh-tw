---
title: 如何：使用程式碼編輯器自訂實體類別
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec28332f-9f3c-4e0a-baca-60f9141a68c0
caps.latest.revision: 3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 3e518a18787a7faa1d3e501d5941fae70daf8b9d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-entity-classes-by-using-the-code-editor"></a><span data-ttu-id="6c7a5-102">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="6c7a5-102">How to: Customize Entity Classes by Using the Code Editor</span></span>
<span data-ttu-id="6c7a5-103">使用 Visual Studio 的開發人員可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]來建立或自訂他們的實體類別。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-103">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create or customize their entity classes.</span></span>  
  
 <span data-ttu-id="6c7a5-104">您也可以使用 [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] 程式碼編輯器來撰寫您自己的對應程式碼，或是自訂已產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-104">You can also use the [!INCLUDE[vsprvs](../../../../../../includes/vsprvs-md.md)] code editor to write your own mapping code or to customize code that has already been generated.</span></span> <span data-ttu-id="6c7a5-105">如需詳細資訊，請參閱[屬性架構對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-105">For more information, see [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
 <span data-ttu-id="6c7a5-106">本章的主題描述如何自訂物件模型。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-106">The topics in this section describe how to customize your object model.</span></span>  
  
 [<span data-ttu-id="6c7a5-107">如何：指定資料庫名稱</span><span class="sxs-lookup"><span data-stu-id="6c7a5-107">How to: Specify Database Names</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-names.md)  
 <span data-ttu-id="6c7a5-108">說明如何使用 <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-108">Describes how to use <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-109">如何：將資料表表示為類別</span><span class="sxs-lookup"><span data-stu-id="6c7a5-109">How to: Represent Tables as Classes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-tables-as-classes.md)  
 <span data-ttu-id="6c7a5-110">說明如何使用 <xref:System.Data.Linq.Mapping.TableAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-110">Describes how to use <xref:System.Data.Linq.Mapping.TableAttribute>.</span></span>  
  
 [<span data-ttu-id="6c7a5-111">如何：將資料行表示為類別成員</span><span class="sxs-lookup"><span data-stu-id="6c7a5-111">How to: Represent Columns as Class Members</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-class-members.md)  
 <span data-ttu-id="6c7a5-112">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-112">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span></span>  
  
 [<span data-ttu-id="6c7a5-113">如何：表示主索引鍵</span><span class="sxs-lookup"><span data-stu-id="6c7a5-113">How to: Represent Primary Keys</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-primary-keys.md)  
 <span data-ttu-id="6c7a5-114">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-114">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-115">如何：對應資料庫關聯性</span><span class="sxs-lookup"><span data-stu-id="6c7a5-115">How to: Map Database Relationships</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-database-relationships.md)  
 <span data-ttu-id="6c7a5-116">提供 <xref:System.Data.Linq.Mapping.AssociationAttribute> 屬性的使用範例。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-116">Provides examples of using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span>  
  
 [<span data-ttu-id="6c7a5-117">如何：將資料行表示為資料庫產生的資料行</span><span class="sxs-lookup"><span data-stu-id="6c7a5-117">How to: Represent Columns as Database-Generated</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-database-generated.md)  
 <span data-ttu-id="6c7a5-118">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-118">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-119">如何：將資料行表示為時間戳記或版本資料行</span><span class="sxs-lookup"><span data-stu-id="6c7a5-119">How to: Represent Columns as Timestamp or Version Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-timestamp-or-version-columns.md)  
 <span data-ttu-id="6c7a5-120">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-120">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-121">如何：指定資料庫的資料類型</span><span class="sxs-lookup"><span data-stu-id="6c7a5-121">How to: Specify Database Data Types</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-database-data-types.md)  
 <span data-ttu-id="6c7a5-122">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-122">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-123">如何：表示計算資料行</span><span class="sxs-lookup"><span data-stu-id="6c7a5-123">How to: Represent Computed Columns</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-computed-columns.md)  
 <span data-ttu-id="6c7a5-124">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-124">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.Expression%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-125">如何：指定私用儲存欄位</span><span class="sxs-lookup"><span data-stu-id="6c7a5-125">How to: Specify Private Storage Fields</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-private-storage-fields.md)  
 <span data-ttu-id="6c7a5-126">說明如何使用 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-126">Describes how to use <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-127">如何：將資料行表示為允許 Null 值</span><span class="sxs-lookup"><span data-stu-id="6c7a5-127">How to: Represent Columns as Allowing Null Values</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-represent-columns-as-allowing-null-values.md)  
 <span data-ttu-id="6c7a5-128">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-128">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
 [<span data-ttu-id="6c7a5-129">如何：對應繼承階層</span><span class="sxs-lookup"><span data-stu-id="6c7a5-129">How to: Map Inheritance Hierarchies</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-map-inheritance-hierarchies.md)  
 <span data-ttu-id="6c7a5-130">描述指定繼承階層架構 (Inheritance Hierarchy) 所需要的對應。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-130">Describes the mappings required to specify an inheritance hierarchy.</span></span>  
  
 [<span data-ttu-id="6c7a5-131">如何：指定並行衝突檢查</span><span class="sxs-lookup"><span data-stu-id="6c7a5-131">How to: Specify Concurrency-Conflict Checking</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-specify-concurrency-conflict-checking.md)  
 <span data-ttu-id="6c7a5-132">說明如何使用 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c7a5-132">Describes how to use <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c7a5-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c7a5-133">See Also</span></span>  
 [<span data-ttu-id="6c7a5-134">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="6c7a5-134">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
