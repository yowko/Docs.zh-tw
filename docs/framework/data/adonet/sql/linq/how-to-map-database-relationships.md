---
title: 如何：對應資料庫關聯性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: c89fb3e11ae8e0f8ea37727446cdf65db9499a1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148370"
---
# <a name="how-to-map-database-relationships"></a><span data-ttu-id="da4e4-102">如何：對應資料庫關聯性</span><span class="sxs-lookup"><span data-stu-id="da4e4-102">How to: Map Database Relationships</span></span>
<span data-ttu-id="da4e4-103">您可以將任何永遠相同的資料關聯性 (Relationship)，編碼成為實體類別 (Entity Class) 中的屬性參考。</span><span class="sxs-lookup"><span data-stu-id="da4e4-103">You can encode as property references in your entity class any data relationships that will always be the same.</span></span> <span data-ttu-id="da4e4-104">例如，在 Northwind 範例資料庫中，因為客戶往往會下單，所以模型中的客戶與其訂單之間一定有關聯性。</span><span class="sxs-lookup"><span data-stu-id="da4e4-104">In the Northwind sample database, for example, because customers typically place orders, there is always a relationship in the model between customers and their orders.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="da4e4-105">定義屬性<xref:System.Data.Linq.Mapping.AssociationAttribute>以説明表示此類關係。</span><span class="sxs-lookup"><span data-stu-id="da4e4-105">defines an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute to help represent such relationships.</span></span> <span data-ttu-id="da4e4-106">這個屬性會與 <xref:System.Data.Linq.EntitySet%601> 和 <xref:System.Data.Linq.EntityRef%601> 型別一起使用，以表示資料庫中的外部索引鍵關聯性為何。</span><span class="sxs-lookup"><span data-stu-id="da4e4-106">This attribute is used together with the <xref:System.Data.Linq.EntitySet%601> and <xref:System.Data.Linq.EntityRef%601> types to represent what would be a foreign key relationship in a database.</span></span> <span data-ttu-id="da4e4-107">有關詳細資訊，請參閱[基於屬性對應](attribute-based-mapping.md)的關聯屬性部分。</span><span class="sxs-lookup"><span data-stu-id="da4e4-107">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da4e4-108">AssociationAttribute 和 ColumnAttribute Storage 屬性值會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="da4e4-108">AssociationAttribute and ColumnAttribute Storage property values are case sensitive.</span></span> <span data-ttu-id="da4e4-109">例如，請確定用於 AssociationAttribute.Storage 屬性 (Property) 之屬性 (Attribute) 中的值與用於程式碼中其他位置之對應屬性 (Property) 名稱的大小寫相符。</span><span class="sxs-lookup"><span data-stu-id="da4e4-109">For example, ensure that values used in the attribute for the AssociationAttribute.Storage property match the case for the corresponding property names used elsewhere in the code.</span></span> <span data-ttu-id="da4e4-110">這適用于所有 .NET 程式設計語言，即使是那些通常不區分大小寫的語言，包括 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="da4e4-110">This applies to all .NET programming languages, even those which are not typically case sensitive, including Visual Basic.</span></span> <span data-ttu-id="da4e4-111">如需 Storage 屬性的詳細資訊，請參閱 <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="da4e4-111">For more information about the Storage property, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="da4e4-112">如本主題後面的範例所示，大部分關聯性都是一對多關聯性 (One-To-Many Relationship)。</span><span class="sxs-lookup"><span data-stu-id="da4e4-112">Most relationships are one-to-many, as in the example later in this topic.</span></span> <span data-ttu-id="da4e4-113">您也可以表示一對一關聯性 (One-To-One Relationship) 和多對多關聯性 (Many-To-Many Relationship)，如下所示：</span><span class="sxs-lookup"><span data-stu-id="da4e4-113">You can also represent one-to-one and many-to-many relationships as follows:</span></span>  
  
- <span data-ttu-id="da4e4-114">一對一：同時在兩邊包含 <xref:System.Data.Linq.EntitySet%601>，以表示這種關聯性。</span><span class="sxs-lookup"><span data-stu-id="da4e4-114">One-to-one: Represent this kind of relationship by including <xref:System.Data.Linq.EntitySet%601> on both sides.</span></span>  
  
     <span data-ttu-id="da4e4-115">例如，考慮創建的關係`Customer`-`SecurityCode`，以便不會在`Customer`表中找到客戶的安全代碼，並且只能由授權人員訪問。</span><span class="sxs-lookup"><span data-stu-id="da4e4-115">For example, consider a `Customer`-`SecurityCode` relationship, created so that the customer's security code will not be found in the `Customer` table and can be accessed only by authorized persons.</span></span>  
  
- <span data-ttu-id="da4e4-116">多對多：在多對多關係中，連結表的主鍵（也稱為*交匯點*表）通常由其他兩個表中的外鍵組合組成。</span><span class="sxs-lookup"><span data-stu-id="da4e4-116">Many-to-many: In many-to-many relationships, the primary key of the link table (also named the *junction* table) is often formed by a composite of the foreign keys from the other two tables.</span></span>  
  
     <span data-ttu-id="da4e4-117">例如`Employee`-`Project`，考慮使用連結表`EmployeeProject`形成的多對多關係。</span><span class="sxs-lookup"><span data-stu-id="da4e4-117">For example, consider an `Employee`-`Project` many-to-many relationship formed by using link table `EmployeeProject`.</span></span> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="da4e4-118">要求使用下列三個類別塑造此種關聯性：`Employee`、`Project` 和 `EmployeeProject`。</span><span class="sxs-lookup"><span data-stu-id="da4e4-118">requires that such a relationship be modeled by using three classes: `Employee`, `Project`, and `EmployeeProject`.</span></span> <span data-ttu-id="da4e4-119">在此情況下，變更 `Employee` 和 `Project` 之間的關聯性，似乎需要更新主索引鍵 `EmployeeProject`。</span><span class="sxs-lookup"><span data-stu-id="da4e4-119">In this case, changing the relationship between an `Employee` and a `Project` can appear to require an update of the primary key `EmployeeProject`.</span></span> <span data-ttu-id="da4e4-120">但是，刪除現有的 `EmployeeProject` 再建立新的 `EmployeeProject` 時，其實最能模擬此種情況。</span><span class="sxs-lookup"><span data-stu-id="da4e4-120">However, this situation is best modeled as deleting an existing `EmployeeProject` and the creating a new `EmployeeProject`.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="da4e4-121">關聯式資料庫中的關聯性通常會塑造成需參考其他資料表中主索引鍵的外部索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="da4e4-121">Relationships in relational databases are typically modeled as foreign key values that refer to primary keys in other tables.</span></span> <span data-ttu-id="da4e4-122">要在它們之間導航，請使用關係*聯接*操作顯式關聯兩個表。</span><span class="sxs-lookup"><span data-stu-id="da4e4-122">To navigate between them you explicitly associate the two tables by using a relational *join* operation.</span></span>  
    >
    >  <span data-ttu-id="da4e4-123">另一[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]方面，使用屬性引用或使用*點*標記法導航的引用集合來相互引用。</span><span class="sxs-lookup"><span data-stu-id="da4e4-123">Objects in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], on the other hand, refer to each other by using property references or collections of references that you navigate by using *dot* notation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da4e4-124">範例</span><span class="sxs-lookup"><span data-stu-id="da4e4-124">Example</span></span>  
 <span data-ttu-id="da4e4-125">在下列一對多範例中，`Customer` 類別有個屬性會宣告客戶與其訂單之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="da4e4-125">In the following one-to-many example, the `Customer` class has a property that declares the relationship between customers and their orders.</span></span>  <span data-ttu-id="da4e4-126">`Orders` 屬性是 <xref:System.Data.Linq.EntitySet%601> 型別。</span><span class="sxs-lookup"><span data-stu-id="da4e4-126">The `Orders` property is of type <xref:System.Data.Linq.EntitySet%601>.</span></span> <span data-ttu-id="da4e4-127">這種型別表示這種關聯性為一對多 (一個客戶對多個訂單) 的關聯性。</span><span class="sxs-lookup"><span data-stu-id="da4e4-127">This type signifies that this relationship is one-to-many (one customer to many orders).</span></span> <span data-ttu-id="da4e4-128"><xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> 屬性用於描述如何達成此種關聯，那就是指定相關類別中的屬性名稱與這個屬性名稱進行比較。</span><span class="sxs-lookup"><span data-stu-id="da4e4-128">The <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> property is used to describe how this association is accomplished, namely, by specifying the name of the property in the related class to be compared with this one.</span></span> <span data-ttu-id="da4e4-129">在此示例中，將比較`CustomerID`該屬性，就像資料庫*聯接*將比較該列值一樣。</span><span class="sxs-lookup"><span data-stu-id="da4e4-129">In this example, the `CustomerID` property is compared, just as a database *join* would compare that column value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da4e4-130">如果使用 Visual Studio，則可以使用物件關係設計器在類之間創建關聯。</span><span class="sxs-lookup"><span data-stu-id="da4e4-130">If you are using Visual Studio, you can use the Object Relational Designer to create an association between classes.</span></span>  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="da4e4-131">範例</span><span class="sxs-lookup"><span data-stu-id="da4e4-131">Example</span></span>  
 <span data-ttu-id="da4e4-132">您也可以反轉這種情況。</span><span class="sxs-lookup"><span data-stu-id="da4e4-132">You can also reverse the situation.</span></span> <span data-ttu-id="da4e4-133">您可以使用 `Customer` 類別，而不要使用 `Order` 類別來描述客戶和訂單之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="da4e4-133">Instead of using the `Customer` class to describe the association between customers and orders, you can use the `Order` class.</span></span> <span data-ttu-id="da4e4-134">`Order` 類別會使用 <xref:System.Data.Linq.EntityRef%601> 型別來描述客戶的反向關聯性，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="da4e4-134">The `Order` class uses the <xref:System.Data.Linq.EntityRef%601> type to describe the relationship back to the customer, as in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da4e4-135">類<xref:System.Data.Linq.EntityRef%601>支援*延遲載入*。</span><span class="sxs-lookup"><span data-stu-id="da4e4-135">The <xref:System.Data.Linq.EntityRef%601> class supports *deferred loading*.</span></span> <span data-ttu-id="da4e4-136">有關詳細資訊，*請參閱*[延遲載入與立即載入](deferred-versus-immediate-loading.md)。</span><span class="sxs-lookup"><span data-stu-id="da4e4-136">For more information, *see* [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="da4e4-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da4e4-137">See also</span></span>

- [<span data-ttu-id="da4e4-138">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="da4e4-138">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [<span data-ttu-id="da4e4-139">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="da4e4-139">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
