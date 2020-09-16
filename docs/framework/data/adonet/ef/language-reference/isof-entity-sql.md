---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: a0294f425552df3329d158d69a6d503b2f008780
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542329"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="39dfe-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="39dfe-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="39dfe-103">判斷運算式的型別是否不屬於所指定的型別或它的其中一個子型別。</span><span class="sxs-lookup"><span data-stu-id="39dfe-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39dfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="39dfe-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="39dfe-105">引數</span><span class="sxs-lookup"><span data-stu-id="39dfe-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="39dfe-106">任何用來判斷屬於何種型別的有效查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="39dfe-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="39dfe-107">NOT</span><span class="sxs-lookup"><span data-stu-id="39dfe-107">NOT</span></span>  
 <span data-ttu-id="39dfe-108">否定 IS OF 的 EDM.Boolean 結果。</span><span class="sxs-lookup"><span data-stu-id="39dfe-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="39dfe-109">ONLY</span><span class="sxs-lookup"><span data-stu-id="39dfe-109">ONLY</span></span>  
 <span data-ttu-id="39dfe-110">指定 IS OF 只在 `true` 為 `expression` 型別而非它的任何子型別時傳回 `type`。</span><span class="sxs-lookup"><span data-stu-id="39dfe-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="39dfe-111">要對它測試 `expression` 的型別。</span><span class="sxs-lookup"><span data-stu-id="39dfe-111">The type to test `expression` against.</span></span> <span data-ttu-id="39dfe-112">此型別必須以命名空間限定。</span><span class="sxs-lookup"><span data-stu-id="39dfe-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="39dfe-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="39dfe-113">Return Value</span></span>  
 <span data-ttu-id="39dfe-114">如果 `true` 為 T 型別，且 T 為基底類型或 `expression` 的衍生型別，則為 `type`；如果 `expression` 在執行階段為 null 則為 null ；否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="39dfe-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39dfe-115">備註</span><span class="sxs-lookup"><span data-stu-id="39dfe-115">Remarks</span></span>  
 <span data-ttu-id="39dfe-116">運算式 `expression IS NOT OF (type)` 和在 `expression IS NOT OF (ONLY type)` 語法上相當於 `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))` 。</span><span class="sxs-lookup"><span data-stu-id="39dfe-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="39dfe-117">下表所示為 `IS OF` 運算子在某些一般及邊角模式中的行為。</span><span class="sxs-lookup"><span data-stu-id="39dfe-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="39dfe-118">所有例外狀況都是在叫用提供者之前從用戶端擲回：</span><span class="sxs-lookup"><span data-stu-id="39dfe-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="39dfe-119">模式</span><span class="sxs-lookup"><span data-stu-id="39dfe-119">Pattern</span></span>|<span data-ttu-id="39dfe-120">行為</span><span class="sxs-lookup"><span data-stu-id="39dfe-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="39dfe-121">null IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="39dfe-122">擲回</span><span class="sxs-lookup"><span data-stu-id="39dfe-122">Throws</span></span>|  
|<span data-ttu-id="39dfe-123">null IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="39dfe-124">擲回</span><span class="sxs-lookup"><span data-stu-id="39dfe-124">Throws</span></span>|  
|<span data-ttu-id="39dfe-125">null IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-125">null IS OF (RowType)</span></span>|<span data-ttu-id="39dfe-126">擲回</span><span class="sxs-lookup"><span data-stu-id="39dfe-126">Throws</span></span>|  
|<span data-ttu-id="39dfe-127">TREAT (null AS EntityType) IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="39dfe-128">傳回 DBNull</span><span class="sxs-lookup"><span data-stu-id="39dfe-128">Returns DBNull</span></span>|  
|<span data-ttu-id="39dfe-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="39dfe-130">擲回</span><span class="sxs-lookup"><span data-stu-id="39dfe-130">Throws</span></span>|  
|<span data-ttu-id="39dfe-131">TREAT (null AS RowType) IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="39dfe-132">擲回</span><span class="sxs-lookup"><span data-stu-id="39dfe-132">Throws</span></span>|  
|<span data-ttu-id="39dfe-133">EntityType IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="39dfe-134">傳回 true/false</span><span class="sxs-lookup"><span data-stu-id="39dfe-134">Returns true/false</span></span>|  
|<span data-ttu-id="39dfe-135">ComplexType IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="39dfe-136">擲回</span><span class="sxs-lookup"><span data-stu-id="39dfe-136">Throws</span></span>|  
|<span data-ttu-id="39dfe-137">RowType IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="39dfe-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="39dfe-138">擲回</span><span class="sxs-lookup"><span data-stu-id="39dfe-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="39dfe-139">範例</span><span class="sxs-lookup"><span data-stu-id="39dfe-139">Example</span></span>  
 <span data-ttu-id="39dfe-140">下列 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 查詢會使用 of 運算子來判斷查詢運算式的型別，然後使用 TREAT 運算子將型別課程的物件轉換成 OnsiteCourse 型別的物件集合。</span><span class="sxs-lookup"><span data-stu-id="39dfe-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="39dfe-141">此查詢是以 [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))為基礎。</span><span class="sxs-lookup"><span data-stu-id="39dfe-141">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="39dfe-142">[！ code-sql [DP EntityServices 概念 # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp EntityServices 概念/tsql/entitysql .sql # treat_isof) ]</span><span class="sxs-lookup"><span data-stu-id="39dfe-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39dfe-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39dfe-143">See also</span></span>

- [<span data-ttu-id="39dfe-144">Entity SQL 參考</span><span class="sxs-lookup"><span data-stu-id="39dfe-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
