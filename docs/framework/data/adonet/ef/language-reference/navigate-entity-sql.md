---
title: NAVIGATE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: f107f29d-005f-4e39-a898-17f163abb1d0
ms.openlocfilehash: 2c6c2ae4c593da1d5fe8cdf3015eb0e31e4b12b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249944"
---
# <a name="navigate-entity-sql"></a><span data-ttu-id="21888-102">NAVIGATE (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="21888-102">NAVIGATE (Entity SQL)</span></span>

<span data-ttu-id="21888-103">在建立於實體之間的關聯性上巡覽。</span><span class="sxs-lookup"><span data-stu-id="21888-103">Navigates over the relationship established between entities.</span></span>

## <a name="syntax"></a><span data-ttu-id="21888-104">語法</span><span class="sxs-lookup"><span data-stu-id="21888-104">Syntax</span></span>

```
navigate(instance-expression, [relationship-type], [to-end [, from-end] ])
```

## <a name="arguments"></a><span data-ttu-id="21888-105">引數</span><span class="sxs-lookup"><span data-stu-id="21888-105">Arguments</span></span>

<span data-ttu-id="21888-106">`instance-expression`實體的實例。</span><span class="sxs-lookup"><span data-stu-id="21888-106">`instance-expression` An instance of an entity.</span></span>

<span data-ttu-id="21888-107">`relationship-type`概念結構定義語言 (CSDL) 檔案中關聯性的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="21888-107">`relationship-type` The type name of the relationship, from the conceptual schema definition language (CSDL) file.</span></span> <span data-ttu-id="21888-108">會限定為\<命名空間 >。\< `relationship-type`關聯性類型名稱 >。</span><span class="sxs-lookup"><span data-stu-id="21888-108">The `relationship-type` is qualified as \<namespace>.\<relationship type name>.</span></span>

<span data-ttu-id="21888-109">`to`關聯性的結尾。</span><span class="sxs-lookup"><span data-stu-id="21888-109">`to` The end of the relationship.</span></span>

<span data-ttu-id="21888-110">`from`關聯性的開頭。</span><span class="sxs-lookup"><span data-stu-id="21888-110">`from` The beginning of the relationship.</span></span>

## <a name="return-value"></a><span data-ttu-id="21888-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="21888-111">Return Value</span></span>

<span data-ttu-id="21888-112">如果結束端的基數為 1，傳回值將會是 `Ref<T>`。</span><span class="sxs-lookup"><span data-stu-id="21888-112">If the cardinality of the to end is 1, the return value will be `Ref<T>`.</span></span> <span data-ttu-id="21888-113">如果結束端的基數為 n，傳回值將會是 `Collection<Ref<T>>`。</span><span class="sxs-lookup"><span data-stu-id="21888-113">If the cardinality of the to end is n, the return value will be `Collection<Ref<T>>`.</span></span>

## <a name="remarks"></a><span data-ttu-id="21888-114">備註</span><span class="sxs-lookup"><span data-stu-id="21888-114">Remarks</span></span>

<span data-ttu-id="21888-115">關聯性是實體資料模型 (EDM) 中的第一個類別結構。</span><span class="sxs-lookup"><span data-stu-id="21888-115">Relationships are first-class constructs in the Entity Data Model (EDM).</span></span> <span data-ttu-id="21888-116">您可在兩個以上的實體類型之間建立關聯性，讓使用者能夠巡覽其中一端 (實體) 到另一端的關聯性。</span><span class="sxs-lookup"><span data-stu-id="21888-116">Relationships can be established between two or more entity types, and users can navigate over the relationship from one end (entity) to another.</span></span> <span data-ttu-id="21888-117">關聯性中的名稱解析沒有模稜兩可情況時，可以有條件地選擇`from` 和 `to` 。</span><span class="sxs-lookup"><span data-stu-id="21888-117">`from` and `to` are conditionally optional when there is no ambiguity in name resolution within the relationship.</span></span>

<span data-ttu-id="21888-118">NAVIGATE 在 O 和 C 空間中有效。</span><span class="sxs-lookup"><span data-stu-id="21888-118">NAVIGATE is valid in O and C space.</span></span>

<span data-ttu-id="21888-119">導覽建構的一般形式如下：</span><span class="sxs-lookup"><span data-stu-id="21888-119">The general form of a navigation construct is the following:</span></span>

<span data-ttu-id="21888-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span><span class="sxs-lookup"><span data-stu-id="21888-120">navigate(`instance-expression`, `relationship-type`, [ `to-end` [, `from-end` ] ] )</span></span>

<span data-ttu-id="21888-121">例如：</span><span class="sxs-lookup"><span data-stu-id="21888-121">For example:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer, Customer, Order)
From LOB.Orders as o
```

<span data-ttu-id="21888-122">其中 OrderCustomer 是 `relationship`，而 Customer 和 Order 則是關聯性的 `to-end` (客戶) 和 `from-end` (訂單)。</span><span class="sxs-lookup"><span data-stu-id="21888-122">Where OrderCustomer is the `relationship`, and Customer and Order are the `to-end` (customer) and `from-end` (order) of the relationship.</span></span> <span data-ttu-id="21888-123">如果 OrderCustomer 是 n:1 關聯性, 則導覽運算式的結果類型會是 Ref\<Customer >。</span><span class="sxs-lookup"><span data-stu-id="21888-123">If OrderCustomer was a n:1 relationship, then the result type of the navigate expression is Ref\<Customer>.</span></span>

<span data-ttu-id="21888-124">這個運算式更簡單的形式如下：</span><span class="sxs-lookup"><span data-stu-id="21888-124">The simpler form of this expression is the following:</span></span>

```sql
Select o.Id, navigate(o, OrderCustomer)
From LOB.Orders as o
```

<span data-ttu-id="21888-125">同樣地, 在下列表單的查詢中, 導覽運算式會產生 < Ref\<Order > > 的集合。</span><span class="sxs-lookup"><span data-stu-id="21888-125">Similarly, in a query of the following form, The navigate expression would produce a Collection<Ref\<Order>>.</span></span>

```sql
Select c.Id, navigate(c, OrderCustomer, Order, Customer)
From LOB.Customers as c
```

<span data-ttu-id="21888-126">此執行個體運算式必須是實體/參考型別。</span><span class="sxs-lookup"><span data-stu-id="21888-126">The instance-expression must be an entity/ref type.</span></span>

## <a name="example"></a><span data-ttu-id="21888-127">範例</span><span class="sxs-lookup"><span data-stu-id="21888-127">Example</span></span>

<span data-ttu-id="21888-128">以下 Entity SQL 查詢使用 NAVIGATE 運算子在建立於 Address 和 SalesOrderHeader 實體類型之間的關聯性上巡覽。</span><span class="sxs-lookup"><span data-stu-id="21888-128">The following Entity SQL query uses the NAVIGATE operator to navigate over the relationship established between Address and SalesOrderHeader entity types.</span></span> <span data-ttu-id="21888-129">此查詢是根據 AdventureWorks Sales Model。</span><span class="sxs-lookup"><span data-stu-id="21888-129">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="21888-130">若要編譯及執行此查詢，請遵循以下步驟：</span><span class="sxs-lookup"><span data-stu-id="21888-130">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="21888-131">[遵循 how to:執行可傳回 StructuralType 結果](../how-to-execute-a-query-that-returns-structuraltype-results.md)的查詢。</span><span class="sxs-lookup"><span data-stu-id="21888-131">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="21888-132">將下列查詢當成引數，傳遞至 `ExecuteStructuralTypeQuery` 方法：</span><span class="sxs-lookup"><span data-stu-id="21888-132">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

 [!code-csharp[DP EntityServices Concepts 2#NAVIGATE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#navigate)]

## <a name="see-also"></a><span data-ttu-id="21888-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21888-133">See also</span></span>

- [<span data-ttu-id="21888-134">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="21888-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="21888-135">如何：使用導覽運算子導覽關聯性</span><span class="sxs-lookup"><span data-stu-id="21888-135">How to: Navigate Relationships with Navigate Operator</span></span>](navigate-entity-sql.md)
