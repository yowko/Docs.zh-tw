---
title: DataTable 結構描述定義
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 0c14c6012c65039e1e2e7e2d2d8c38c4202b45a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153244"
---
# <a name="datatable-schema-definition"></a><span data-ttu-id="e1efa-102">DataTable 結構描述定義</span><span class="sxs-lookup"><span data-stu-id="e1efa-102">DataTable Schema Definition</span></span>

<span data-ttu-id="e1efa-103">資料表的結構描述 (或結構) 是由資料行或條件約束來表示。</span><span class="sxs-lookup"><span data-stu-id="e1efa-103">The schema, or structure, of a table is represented by columns and constraints.</span></span> <span data-ttu-id="e1efa-104">您可以使用 <xref:System.Data.DataTable> 物件以及 <xref:System.Data.DataColumn> 和 <xref:System.Data.ForeignKeyConstraint> 物件來定義 <xref:System.Data.UniqueConstraint> 的結構描述。</span><span class="sxs-lookup"><span data-stu-id="e1efa-104">You define the schema of a <xref:System.Data.DataTable> using <xref:System.Data.DataColumn> objects as well as <xref:System.Data.ForeignKeyConstraint> and <xref:System.Data.UniqueConstraint> objects.</span></span> <span data-ttu-id="e1efa-105">資料表的資料行可對應到資料來源中的資料行、包含運算式所得的值、自動累加其值或包含主索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="e1efa-105">The columns in a table can map to columns in a data source, contain calculated values from expressions, automatically increment their values, or contain primary key values.</span></span>  
  
 <span data-ttu-id="e1efa-106">依名稱參考資料表的資料行、關聯和條件約束時必須區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="e1efa-106">References by name to columns, relations, and constraints in a table are case-sensitive.</span></span> <span data-ttu-id="e1efa-107">兩個或兩個以上名稱相同的資料行、關聯或條件約束可因此存在於同一個資料表中，但其大小寫必須不同。</span><span class="sxs-lookup"><span data-stu-id="e1efa-107">Two or more columns, relations, or constraints can therefore exist in a table that have the same name, but that differ in case.</span></span> <span data-ttu-id="e1efa-108">例如，您可以有 **col1** 和 **col1**。</span><span class="sxs-lookup"><span data-stu-id="e1efa-108">For example, you can have **Col1** and **col1**.</span></span> <span data-ttu-id="e1efa-109">在這種情況下，依名稱參考其中一個資料行時，必須與資料行名稱的大小寫完全相符，否則將發生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e1efa-109">In such as case, a reference to one of the columns by name must match the case of the column name exactly; otherwise an exception is thrown.</span></span> <span data-ttu-id="e1efa-110">例如，如果資料表 **myTable** 包含資料行 **col1** 和 **col1**，您就會依名稱將 **col1** 參考為 **mytable. columns ["col1"]**，並將 **col1** 視為 **mytable. columns ["col1"]**。</span><span class="sxs-lookup"><span data-stu-id="e1efa-110">For example, if the table **myTable** contains the columns **Col1** and **col1**, you would reference **Col1** by name as **myTable.Columns["Col1"]**, and **col1** as **myTable.Columns["col1"]**.</span></span> <span data-ttu-id="e1efa-111">嘗試以 MyTable 的形式參考其中一個資料行 **。資料行 ["COL1"]** 會產生例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e1efa-111">Attempting to reference either of the columns as **myTable.Columns["COL1"]** would generate an exception.</span></span>  
  
 <span data-ttu-id="e1efa-112">如果只有一個資料行、關聯和條件約束使用特定的名稱，則不適用區分大小寫的規則。</span><span class="sxs-lookup"><span data-stu-id="e1efa-112">The case-sensitivity rule does not apply if only one column, relation, or constraint  with a particular name exists.</span></span> <span data-ttu-id="e1efa-113">也就是說，如果資料表中沒有其他的資料行、關聯和條件約束物件與該特定資料行、關聯或條件約束物件的名稱相符，您在依名稱參考物件時就不需區分大小寫，而且也不會發生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e1efa-113">That is, if no other column, relation, or constraint object in the table matches the name of that particular column, relation, or constraint object, you may reference the object by name using any case, and no exception is thrown.</span></span> <span data-ttu-id="e1efa-114">例如，如果資料表只有 **Col1**，您可以使用 my 來參考它 **。資料行 ["COL1"]**。</span><span class="sxs-lookup"><span data-stu-id="e1efa-114">For example, if the table has only **Col1**, you can reference it using **my.Columns["COL1"]**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1efa-115"><xref:System.Data.DataTable.CaseSensitive%2A> **DataTable**的屬性不會影響此行為。</span><span class="sxs-lookup"><span data-stu-id="e1efa-115">The <xref:System.Data.DataTable.CaseSensitive%2A> property of the **DataTable** does not affect this behavior.</span></span> <span data-ttu-id="e1efa-116">**CaseSensitive**屬性適用于資料表中的資料，並會影響排序、搜尋、篩選、強制執行條件約束等，而不會影響資料行、關聯和條件約束的參考。</span><span class="sxs-lookup"><span data-stu-id="e1efa-116">The **CaseSensitive** property applies to the data in a table and affects sorting, searching, filtering, enforcing constraints, and so on, but not to references to the columns, relations, and constraints.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1efa-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="e1efa-117">In This Section</span></span>  

 [<span data-ttu-id="e1efa-118">將資料行加入至 DataTable</span><span class="sxs-lookup"><span data-stu-id="e1efa-118">Adding Columns to a DataTable</span></span>](adding-columns-to-a-datatable.md)  
 <span data-ttu-id="e1efa-119">描述如何使用 **DataColumn** 物件來定義資料表的資料行。</span><span class="sxs-lookup"><span data-stu-id="e1efa-119">Describes how to define the columns of a table using **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="e1efa-120">建立運算式資料行</span><span class="sxs-lookup"><span data-stu-id="e1efa-120">Creating Expression Columns</span></span>](creating-expression-columns.md)  
 <span data-ttu-id="e1efa-121">說明如何使用資料行的 **Expression** 屬性，根據資料列中的其他資料行值來計算值。</span><span class="sxs-lookup"><span data-stu-id="e1efa-121">Explains how the **Expression** property of a column can be used to calculate values based on the values from other columns in the row.</span></span>  
  
 [<span data-ttu-id="e1efa-122">建立自動遞增資料行</span><span class="sxs-lookup"><span data-stu-id="e1efa-122">Creating AutoIncrement Columns</span></span>](creating-autoincrement-columns.md)  
 <span data-ttu-id="e1efa-123">說明如何將資料行設定為自動累加數值，以確保每個資料列都有唯一的資料行值。</span><span class="sxs-lookup"><span data-stu-id="e1efa-123">Describes how a column can be set to automatically increment numerical values to ensure a unique column value per row.</span></span>  
  
 [<span data-ttu-id="e1efa-124">定義主索引鍵</span><span class="sxs-lookup"><span data-stu-id="e1efa-124">Defining Primary Keys</span></span>](defining-primary-keys.md)  
 <span data-ttu-id="e1efa-125">描述如何從一個或多個 **DataColumn** 物件指定資料表的主鍵。</span><span class="sxs-lookup"><span data-stu-id="e1efa-125">Describes how to specify the primary key of a table from one or more **DataColumn** objects.</span></span>  
  
 [<span data-ttu-id="e1efa-126">DataTable 條件約束</span><span class="sxs-lookup"><span data-stu-id="e1efa-126">DataTable Constraints</span></span>](datatable-constraints.md)  
 <span data-ttu-id="e1efa-127">說明如何在資料表中定義資料行的外部索引鍵條件約束和唯一的條件約束。</span><span class="sxs-lookup"><span data-stu-id="e1efa-127">Describes how to define foreign key and unique constraints for columns in a table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1efa-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1efa-128">See also</span></span>

- [<span data-ttu-id="e1efa-129">DataTables</span><span class="sxs-lookup"><span data-stu-id="e1efa-129">DataTables</span></span>](datatables.md)
- <span data-ttu-id="e1efa-130">[ADO.NET 概觀](../ado-net-overview.md) \(部分機器翻譯\)</span><span class="sxs-lookup"><span data-stu-id="e1efa-130">[ADO.NET Overview](../ado-net-overview.md)</span></span>
