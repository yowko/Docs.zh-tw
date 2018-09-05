---
title: 如何：在查詢中呼叫模型定義函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
ms.openlocfilehash: 2a20a2bb524c1ef9135b8b7187b2519088ddb762
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674133"
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="3357f-102">如何：在查詢中呼叫模型定義函式</span><span class="sxs-lookup"><span data-stu-id="3357f-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="3357f-103">本主題描述如何從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫概念模型中所定義的函式。</span><span class="sxs-lookup"><span data-stu-id="3357f-103">This topic describes how to call functions that are defined in the conceptual model from within [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="3357f-104">以下程序提供從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫模型定義函式的高階概述。</span><span class="sxs-lookup"><span data-stu-id="3357f-104">The procedure below provides a high-level outline for calling a model-defined function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="3357f-105">程序後的範例提供程序中之步驟相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="3357f-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="3357f-106">程序假設您已在概念模型中定義函式。</span><span class="sxs-lookup"><span data-stu-id="3357f-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="3357f-107">如需詳細資訊，請參閱 <<c0> [ 如何： 在概念模型中定義自訂函式](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)。</span><span class="sxs-lookup"><span data-stu-id="3357f-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="3357f-108">呼叫概念模型中定義的函式</span><span class="sxs-lookup"><span data-stu-id="3357f-108">To call a function defined in the conceptual model</span></span>  
  
1.  <span data-ttu-id="3357f-109">將 Common Language Runtime (CLR) 方法加入至您的應用程式，該方法會對應至概念模型中所定義之函式。</span><span class="sxs-lookup"><span data-stu-id="3357f-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="3357f-110">若要對應方法，您必須將 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 套用至方法。</span><span class="sxs-lookup"><span data-stu-id="3357f-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="3357f-111">請注意，屬性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 參數分別是概念模型的命名空間名稱和概念模型中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="3357f-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="3357f-112">LINQ 的函式名稱解析是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="3357f-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2.  <span data-ttu-id="3357f-113">在 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢中呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="3357f-113">Call the function in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3357f-114">範例</span><span class="sxs-lookup"><span data-stu-id="3357f-114">Example</span></span>  
 <span data-ttu-id="3357f-115">下列範例示範如何從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫概念模型中所定義的函式。</span><span class="sxs-lookup"><span data-stu-id="3357f-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="3357f-116">範例使用 School 模型。</span><span class="sxs-lookup"><span data-stu-id="3357f-116">The example uses the School model.</span></span> <span data-ttu-id="3357f-117">如需 School 模型的詳細資訊，請參閱[建立 School 範例資料庫](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0)並[產生 School.edmx 檔案](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758)。</span><span class="sxs-lookup"><span data-stu-id="3357f-117">For information about the School model, see [Creating the School Sample Database](https://msdn.microsoft.com/library/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](https://msdn.microsoft.com/library/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="3357f-118">下列概念模型函式會傳回講師受雇之後經過的年份。</span><span class="sxs-lookup"><span data-stu-id="3357f-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="3357f-119">如需加入函式至概念模型資訊，請參閱[如何： 在概念模型中定義自訂函式](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)。)</span><span class="sxs-lookup"><span data-stu-id="3357f-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="3357f-120">範例</span><span class="sxs-lookup"><span data-stu-id="3357f-120">Example</span></span>  
 <span data-ttu-id="3357f-121">接下來，將下列方法加入至您的應用程式並使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 將它對應至概念模型函式：</span><span class="sxs-lookup"><span data-stu-id="3357f-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="3357f-122">範例</span><span class="sxs-lookup"><span data-stu-id="3357f-122">Example</span></span>  
 <span data-ttu-id="3357f-123">現在，您可以從 [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] 查詢內呼叫概念模型函式。</span><span class="sxs-lookup"><span data-stu-id="3357f-123">Now you can call the conceptual model function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="3357f-124">下列程式碼會呼叫該方法，顯示受雇超過十年的所有講師：</span><span class="sxs-lookup"><span data-stu-id="3357f-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="3357f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3357f-125">See Also</span></span>  
 [<span data-ttu-id="3357f-126">.edmx 檔案概觀</span><span class="sxs-lookup"><span data-stu-id="3357f-126">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="3357f-127">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="3357f-127">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="3357f-128">在 LINQ to Entities 查詢中呼叫函式</span><span class="sxs-lookup"><span data-stu-id="3357f-128">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="3357f-129">如何：將模型定義函式當作物件方法來呼叫</span><span class="sxs-lookup"><span data-stu-id="3357f-129">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)
