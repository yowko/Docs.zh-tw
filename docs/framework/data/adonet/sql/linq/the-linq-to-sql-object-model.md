---
title: LINQ to SQL 物件模型
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: 6518e4edeccdd533487f717122ba6832f13436a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947059"
---
# <a name="the-linq-to-sql-object-model"></a><span data-ttu-id="02454-102">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="02454-102">The LINQ to SQL Object Model</span></span>
<span data-ttu-id="02454-103">在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中, 以開發人員的程式設計語言表示的物件模型會對應到關係資料庫的資料模型。</span><span class="sxs-lookup"><span data-stu-id="02454-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model expressed in the programming language of the developer is mapped to the data model of a relational database.</span></span> <span data-ttu-id="02454-104">然後就會根據物件模型對資料執行作業。</span><span class="sxs-lookup"><span data-stu-id="02454-104">Operations on the data are then conducted according to the object model.</span></span>  
  
 <span data-ttu-id="02454-105">在這種情況下，您不會發出資料庫命令 (例如，`INSERT`) 至資料庫。</span><span class="sxs-lookup"><span data-stu-id="02454-105">In this scenario, you do not issue database commands (for example, `INSERT`) to the database.</span></span> <span data-ttu-id="02454-106">而是在您的物件模型中變更值和執行方法。</span><span class="sxs-lookup"><span data-stu-id="02454-106">Instead, you change values and execute methods within your object model.</span></span> <span data-ttu-id="02454-107">當您要查詢資料庫或將變更傳送至資料庫時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會將您的要求轉譯為正確的 SQL 命令，並將這些命令傳送至資料庫。</span><span class="sxs-lookup"><span data-stu-id="02454-107">When you want to query the database or send it changes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your requests into the correct SQL commands and sends those commands to the database.</span></span>  
  
 ![顯示 Linq 物件模型的螢幕擷取畫面。](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="02454-109">下表摘要說明[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]物件模型中最基本的專案, 以及其與關聯式資料模型中專案的關聯性:</span><span class="sxs-lookup"><span data-stu-id="02454-109">The most fundamental elements in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model and their relationship to elements in the relational data model are summarized in the following table:</span></span>  
  
|<span data-ttu-id="02454-110">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="02454-110">LINQ to SQL Object Model</span></span>|<span data-ttu-id="02454-111">關聯式資料模型</span><span class="sxs-lookup"><span data-stu-id="02454-111">Relational Data Model</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="02454-112">實體類別</span><span class="sxs-lookup"><span data-stu-id="02454-112">Entity class</span></span>|<span data-ttu-id="02454-113">資料表</span><span class="sxs-lookup"><span data-stu-id="02454-113">Table</span></span>|  
|<span data-ttu-id="02454-114">類別成員</span><span class="sxs-lookup"><span data-stu-id="02454-114">Class member</span></span>|<span data-ttu-id="02454-115">「資料行」</span><span class="sxs-lookup"><span data-stu-id="02454-115">Column</span></span>|  
|<span data-ttu-id="02454-116">關聯</span><span class="sxs-lookup"><span data-stu-id="02454-116">Association</span></span>|<span data-ttu-id="02454-117">外部索引鍵關聯性</span><span class="sxs-lookup"><span data-stu-id="02454-117">Foreign-key relationship</span></span>|  
|<span data-ttu-id="02454-118">方法</span><span class="sxs-lookup"><span data-stu-id="02454-118">Method</span></span>|<span data-ttu-id="02454-119">預存程序或函式</span><span class="sxs-lookup"><span data-stu-id="02454-119">Stored Procedure or Function</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="02454-120">下列說明假設您對於關聯式資料模型和規則有基本知識。</span><span class="sxs-lookup"><span data-stu-id="02454-120">The following descriptions assume that you have a basic knowledge of the relational data model and rules.</span></span>  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a><span data-ttu-id="02454-121">LINQ to SQL 實體類別和資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="02454-121">LINQ to SQL Entity Classes and Database Tables</span></span>  
 <span data-ttu-id="02454-122">在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中, 資料庫資料表是由*實體類別*表示。</span><span class="sxs-lookup"><span data-stu-id="02454-122">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a database table is represented by an *entity class*.</span></span> <span data-ttu-id="02454-123">實體類別就像您可能建立的任何其他類別，但您會使用能讓類別與資料庫資料表產生關聯的特殊資訊來標註此類別。</span><span class="sxs-lookup"><span data-stu-id="02454-123">An entity class is like any other class you might create except that you annotate the class by using special information that associates the class with a database table.</span></span> <span data-ttu-id="02454-124">您可將自訂屬性 (<xref:System.Data.Linq.Mapping.TableAttribute>) 加入至您的類別宣告，藉以產生此附註，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="02454-124">You make this annotation by adding a custom attribute (<xref:System.Data.Linq.Mapping.TableAttribute>) to your class declaration, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="02454-125">範例</span><span class="sxs-lookup"><span data-stu-id="02454-125">Example</span></span>  
 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 <span data-ttu-id="02454-126">只有宣告為資料表的類別執行個體 (也就是實體類別) 可以儲存至資料庫。</span><span class="sxs-lookup"><span data-stu-id="02454-126">Only instances of classes declared as tables (that is, entity classes) can be saved to the database.</span></span>  
  
 <span data-ttu-id="02454-127">如需詳細資訊, 請參閱以屬性為[基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)的資料表屬性一節。</span><span class="sxs-lookup"><span data-stu-id="02454-127">For more information, see the Table Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a><span data-ttu-id="02454-128">LINQ to SQL 類別成員和資料庫資料行</span><span class="sxs-lookup"><span data-stu-id="02454-128">LINQ to SQL Class Members and Database Columns</span></span>  
 <span data-ttu-id="02454-129">除了使類別和資料表產生關聯以外，您還會指定欄位或屬性，以表示資料庫資料行。</span><span class="sxs-lookup"><span data-stu-id="02454-129">In addition to associating classes with tables, you designate fields or properties to represent database columns.</span></span> <span data-ttu-id="02454-130">基於這個目的，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 會定義 <xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="02454-130">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] defines the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="02454-131">範例</span><span class="sxs-lookup"><span data-stu-id="02454-131">Example</span></span>  
 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 <span data-ttu-id="02454-132">只有對應到資料行的欄位和屬性會保存至資料庫或自資料庫擷取。</span><span class="sxs-lookup"><span data-stu-id="02454-132">Only fields and properties mapped to columns are persisted to or retrieved from the database.</span></span> <span data-ttu-id="02454-133">至於未宣告為資料行者，則會被視為應用程式邏輯的暫時性部分。</span><span class="sxs-lookup"><span data-stu-id="02454-133">Those not declared as columns are considered as transient parts of your application logic.</span></span>  
  
 <span data-ttu-id="02454-134"><xref:System.Data.Linq.Mapping.ColumnAttribute> 屬性 (Attribute) 具有各種屬性 (Property)，您可以用於自訂表示資料行的這些成員 (例如，指定成員以表示主索引鍵資料行)。</span><span class="sxs-lookup"><span data-stu-id="02454-134">The <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute has a variety of properties that you can use to customize these members that represent columns (for example, designating a member as representing a primary key column).</span></span> <span data-ttu-id="02454-135">如需詳細資訊, 請參閱以屬性為[基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)的資料行屬性一節。</span><span class="sxs-lookup"><span data-stu-id="02454-135">For more information, see the Column Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a><span data-ttu-id="02454-136">LINQ to SQL 關聯和資料庫外部索引鍵關聯性</span><span class="sxs-lookup"><span data-stu-id="02454-136">LINQ to SQL Associations and Database Foreign-key Relationships</span></span>  
 <span data-ttu-id="02454-137">在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中, 您可以藉由套用<xref:System.Data.Linq.Mapping.AssociationAttribute>屬性來表示資料庫關聯 (例如外鍵與主鍵的關聯性)。</span><span class="sxs-lookup"><span data-stu-id="02454-137">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you represent database associations (such as foreign-key to primary-key relationships) by applying the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="02454-138">在下列程式碼區段中, `Order`類別`Customer`包含具有<xref:System.Data.Linq.Mapping.AssociationAttribute>屬性 (attribute) 的屬性 (property)。</span><span class="sxs-lookup"><span data-stu-id="02454-138">In the following segment of code, the `Order` class contains a `Customer` property that has an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="02454-139">這個屬性 (Property) 與其屬性 (Attribute) 提供了與 `Order` 類別有關的 `Customer` 類別。</span><span class="sxs-lookup"><span data-stu-id="02454-139">This property and its attribute provide the `Order` class with a relationship to the `Customer` class.</span></span>  
  
 <span data-ttu-id="02454-140">下列程式碼範例顯示 `Customer` 類別中的 `Order` 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="02454-140">The following code example shows the `Customer` property from the `Order` class.</span></span>  
  
### <a name="example"></a><span data-ttu-id="02454-141">範例</span><span class="sxs-lookup"><span data-stu-id="02454-141">Example</span></span>  
 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 <span data-ttu-id="02454-142">如需詳細資訊, 請參閱以屬性為[基礎的對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)的關聯屬性一節。</span><span class="sxs-lookup"><span data-stu-id="02454-142">For more information, see the Association Attribute section of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a><span data-ttu-id="02454-143">LINQ to SQL 方法和資料庫預存程序</span><span class="sxs-lookup"><span data-stu-id="02454-143">LINQ to SQL Methods and Database Stored Procedures</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="02454-144">支援預存程序和使用者定義函式。</span><span class="sxs-lookup"><span data-stu-id="02454-144">supports stored procedures and user-defined functions.</span></span> <span data-ttu-id="02454-145">在[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]中, 您可以將這些資料庫定義的抽象對應至用戶端物件, 以便從用戶端程式代碼以強型別的方式存取它們。</span><span class="sxs-lookup"><span data-stu-id="02454-145">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you map these database-defined abstractions to client objects so that you can access them in a strongly typed manner from client code.</span></span> <span data-ttu-id="02454-146">方法簽章與資料庫中定義的程序和函式簽章十分相似。</span><span class="sxs-lookup"><span data-stu-id="02454-146">The method signatures resemble as closely as possible the signatures of the procedures and functions defined in the database.</span></span> <span data-ttu-id="02454-147">您可以使用 IntelliSense 來探索這些方法。</span><span class="sxs-lookup"><span data-stu-id="02454-147">You can use IntelliSense to discover these methods.</span></span>  
  
 <span data-ttu-id="02454-148">呼叫對應程序所傳回的結果集是強型別集合。</span><span class="sxs-lookup"><span data-stu-id="02454-148">A result set that is returned by a call to a mapped procedure is a strongly typed collection.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="02454-149">會使用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 和 <xref:System.Data.Linq.Mapping.ParameterAttribute> 屬性，將預存程序和函式對應至方法。</span><span class="sxs-lookup"><span data-stu-id="02454-149">maps stored procedures and functions to methods by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> and <xref:System.Data.Linq.Mapping.ParameterAttribute> attributes.</span></span> <span data-ttu-id="02454-150"><xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> 屬性可以區分表示預存程序的方法和表示使用者定義函式的方法。</span><span class="sxs-lookup"><span data-stu-id="02454-150">Methods representing stored procedures are distinguished from those representing user-defined functions by the <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> property.</span></span> <span data-ttu-id="02454-151">如果此屬性設為 `false` (預設值)，則此方法表示預存程序。</span><span class="sxs-lookup"><span data-stu-id="02454-151">If this property is set to `false` (the default), the method represents a stored procedure.</span></span> <span data-ttu-id="02454-152">如果設為 `true`，則此方法表示資料庫函式。</span><span class="sxs-lookup"><span data-stu-id="02454-152">If it is set to `true`, the method represents a database function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02454-153">如果您使用 Visual Studio, 您可以使用物件關聯式設計工具來建立對應至預存程式和使用者定義函數的方法。</span><span class="sxs-lookup"><span data-stu-id="02454-153">If you are using Visual Studio, you can use the Object Relational Designer to create methods mapped to stored procedures and user-defined functions.</span></span>  
  
### <a name="example"></a><span data-ttu-id="02454-154">範例</span><span class="sxs-lookup"><span data-stu-id="02454-154">Example</span></span>  
 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 <span data-ttu-id="02454-155">如需詳細資訊, 請參閱函數屬性、預存程式屬性和以[屬性為基礎之對應](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)和[預存程式](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)的參數屬性區段。</span><span class="sxs-lookup"><span data-stu-id="02454-155">For more information, see the Function Attribute, Stored Procedure Attribute, and Parameter Attribute sections of [Attribute-Based Mapping](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md) and [Stored Procedures](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02454-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02454-156">See also</span></span>

- [<span data-ttu-id="02454-157">以屬性為基礎的對應</span><span class="sxs-lookup"><span data-stu-id="02454-157">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)
- [<span data-ttu-id="02454-158">背景資訊</span><span class="sxs-lookup"><span data-stu-id="02454-158">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
