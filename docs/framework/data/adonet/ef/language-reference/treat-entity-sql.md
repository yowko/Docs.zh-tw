---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 566ac875aec17e4d0aa22ec1962053aeb6ae2a2e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558845"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="c7497-102">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c7497-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="c7497-103">將特定基底類型的物件視為所指定之衍生型別的物件。</span><span class="sxs-lookup"><span data-stu-id="c7497-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7497-104">語法</span><span class="sxs-lookup"><span data-stu-id="c7497-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7497-105">引數</span><span class="sxs-lookup"><span data-stu-id="c7497-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="c7497-106">任何傳回實體的有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="c7497-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7497-107">所指定運算式的型別必須是所指定資料型別的子型別，或者此資料型別必須是運算式之型別的子型別。</span><span class="sxs-lookup"><span data-stu-id="c7497-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="c7497-108">任何實體類型。</span><span class="sxs-lookup"><span data-stu-id="c7497-108">An entity type.</span></span> <span data-ttu-id="c7497-109">此型別必須以命名空間 (Namespace) 限定。</span><span class="sxs-lookup"><span data-stu-id="c7497-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7497-110">所指定的運算式必須是所指定資料型別的子型別，或者此資料型別必須是此運算式的子型別。</span><span class="sxs-lookup"><span data-stu-id="c7497-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7497-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="c7497-111">Return Value</span></span>  
 <span data-ttu-id="c7497-112">屬於所指定資料型別的值。</span><span class="sxs-lookup"><span data-stu-id="c7497-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7497-113">備註</span><span class="sxs-lookup"><span data-stu-id="c7497-113">Remarks</span></span>  
 <span data-ttu-id="c7497-114">TREAT 是用來在兩個相關類別之間執行向上轉型。</span><span class="sxs-lookup"><span data-stu-id="c7497-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="c7497-115">舉例來講，假設 `Employee` 是衍生自 `Person` 而 p 是 `Person`型別，則 `TREAT(p AS NamespaceName.Employee)` 會將泛型 `Person` 執行個體向上轉型成為 `Employee`；換言之，它可以讓您將 p 視為 `Employee`。</span><span class="sxs-lookup"><span data-stu-id="c7497-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="c7497-116">TREAT 是使用於繼承的情況下，在這種情況下您可以執行類似下列的查詢：</span><span class="sxs-lookup"><span data-stu-id="c7497-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="c7497-117">這個查詢將 `Person` 實體向上轉型成為 `Employee` 型別。</span><span class="sxs-lookup"><span data-stu-id="c7497-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="c7497-118">如果 p 的值實際上不是 `Employee`型別，此運算式將會產生值 `null`。</span><span class="sxs-lookup"><span data-stu-id="c7497-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c7497-119">指定的運算式 `Employee` 必須是指定之資料類型的子類型 `Person` ，或是資料類型必須是運算式的子類型。</span><span class="sxs-lookup"><span data-stu-id="c7497-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="c7497-120">否則此運算式將會造成編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7497-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="c7497-121">下表所示為 TREAT 在某些一般模式及一些較不常見的模式中的行為。</span><span class="sxs-lookup"><span data-stu-id="c7497-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="c7497-122">所有例外狀況都是在叫用提供者之前從用戶端擲回：</span><span class="sxs-lookup"><span data-stu-id="c7497-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="c7497-123">模式</span><span class="sxs-lookup"><span data-stu-id="c7497-123">Pattern</span></span>|<span data-ttu-id="c7497-124">行為</span><span class="sxs-lookup"><span data-stu-id="c7497-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="c7497-125">傳回 `DbNull`。</span><span class="sxs-lookup"><span data-stu-id="c7497-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="c7497-126">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c7497-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="c7497-127">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c7497-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="c7497-128">傳回 `EntityType` 或 `null`。</span><span class="sxs-lookup"><span data-stu-id="c7497-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="c7497-129">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c7497-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="c7497-130">擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c7497-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c7497-131">範例</span><span class="sxs-lookup"><span data-stu-id="c7497-131">Example</span></span>  
 <span data-ttu-id="c7497-132">下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢使用 TREAT 運算子將 Course 型別的物件轉換成 OnsiteCourse 型別的物件集合。</span><span class="sxs-lookup"><span data-stu-id="c7497-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="c7497-133">此查詢是以 [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))為基礎。</span><span class="sxs-lookup"><span data-stu-id="c7497-133">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="c7497-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7497-134">See also</span></span>

- [<span data-ttu-id="c7497-135">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="c7497-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="c7497-136">可為 Null 的結構類型</span><span class="sxs-lookup"><span data-stu-id="c7497-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
