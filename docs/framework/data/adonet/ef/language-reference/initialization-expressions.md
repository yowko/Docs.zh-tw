---
title: 初始化運算式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 78bafcad0a0f34c74ea58f107621ad145c1b405b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631537"
---
# <a name="initialization-expressions"></a><span data-ttu-id="230e6-102">初始化運算式</span><span class="sxs-lookup"><span data-stu-id="230e6-102">Initialization Expressions</span></span>
<span data-ttu-id="230e6-103">初始化運算式會初始化新的物件。</span><span class="sxs-lookup"><span data-stu-id="230e6-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="230e6-104">大多數的初始化運算式都有支援，包括最新的 C# 3.0 和 Visual Basic 9.0 初始化運算式。</span><span class="sxs-lookup"><span data-stu-id="230e6-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="230e6-105">以下是可由 LINQ to Entities 查詢初始化及傳回的型別：</span><span class="sxs-lookup"><span data-stu-id="230e6-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="230e6-106">零或多個具型別實體物件的集合或是於概念模型中定義之複雜型別的投影。</span><span class="sxs-lookup"><span data-stu-id="230e6-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="230e6-107">[!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] 支援的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="230e6-107">CLR types supported by the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].</span></span>  
  
- <span data-ttu-id="230e6-108">內嵌集合。</span><span class="sxs-lookup"><span data-stu-id="230e6-108">Inline collections.</span></span>  
  
- <span data-ttu-id="230e6-109">匿名型別。</span><span class="sxs-lookup"><span data-stu-id="230e6-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="230e6-110">查詢運算式語法中的下列範例示範匿名型別初始化：</span><span class="sxs-lookup"><span data-stu-id="230e6-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="230e6-111">下列以方法為根據的查詢語法中的範例會顯示匿名型別初始化：</span><span class="sxs-lookup"><span data-stu-id="230e6-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="230e6-112">也有支援使用者定義的類別初始化。</span><span class="sxs-lookup"><span data-stu-id="230e6-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="230e6-113">C# 3.0 和 Visual Basic 9.0 初始化模式有受到支援，而且會假設屬性 getter 和 setter 為對稱。</span><span class="sxs-lookup"><span data-stu-id="230e6-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="230e6-114">下列查詢運算式語法中的範例顯示在查詢中初始化的自訂類別：</span><span class="sxs-lookup"><span data-stu-id="230e6-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="230e6-115">下列以方法為根據之查詢語法中的範例顯示在查詢中初始化的自訂類別：</span><span class="sxs-lookup"><span data-stu-id="230e6-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="230e6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="230e6-116">See also</span></span>

- [<span data-ttu-id="230e6-117">LINQ to Entities 查詢中的運算式</span><span class="sxs-lookup"><span data-stu-id="230e6-117">Expressions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/expressions-in-linq-to-entities-queries.md)
