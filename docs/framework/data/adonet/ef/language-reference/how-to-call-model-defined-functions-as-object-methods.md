---
title: 如何：將模型定義函式當做物件方法來呼叫
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33bae8a8-4ed8-4a1f-85d1-c62ff288cc61
ms.openlocfilehash: 290c2f58d0259d5a0df52711f63c48521891ae12
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502077"
---
# <a name="how-to-call-model-defined-functions-as-object-methods"></a><span data-ttu-id="ddade-102">如何：將模型定義函式當做物件方法來呼叫</span><span class="sxs-lookup"><span data-stu-id="ddade-102">How to: Call Model-Defined Functions as Object Methods</span></span>
<span data-ttu-id="ddade-103">本主題描述如何呼叫模型定義函式做為 <xref:System.Data.Objects.ObjectContext> 物件上的方法，或做為自訂類別上的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ddade-103">This topic describes how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object or as a static method on a custom class.</span></span> <span data-ttu-id="ddade-104">A*模型定義函式*是概念模型中所定義的函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-104">A *model-defined function* is a function that is defined in the conceptual model.</span></span> <span data-ttu-id="ddade-105">本主題的程序說明如何直接呼叫這些函式，而不是從 LINQ to Entities 查詢呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-105">The procedures in the topic describe how to call these functions directly instead of calling them from LINQ to Entities queries.</span></span> <span data-ttu-id="ddade-106">呼叫 LINQ to Entities 查詢的模型定義的函式的相關資訊，請參閱[如何： 在查詢中的 Call Model-Defined 函式](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="ddade-106">For information about calling model-defined functions in LINQ to Entities queries, see [How to: Call Model-Defined Functions in Queries](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-in-queries.md).</span></span>  
  
 <span data-ttu-id="ddade-107">無論您是呼叫模型定義函式做為 <xref:System.Data.Objects.ObjectContext> 方法，或是做為自訂類別上的靜態方法，您必須先使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 將方法對應至模型定義函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-107">Whether you call a model-defined function as an <xref:System.Data.Objects.ObjectContext> method or as a static method on a custom class, you must first map the method to the model-defined function with an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="ddade-108">不過，當您定義 <xref:System.Data.Objects.ObjectContext> 類別上的方法時，您必須使用 <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> 屬性公開 LINQ 提供者，而當您定義自訂類別上的靜態方法時，您必須使用 <xref:System.Linq.IQueryable.Provider%2A> 屬性公開 LINQ 提供者。</span><span class="sxs-lookup"><span data-stu-id="ddade-108">However, when you define a method on the <xref:System.Data.Objects.ObjectContext> class, you must use the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property to expose the LINQ provider, whereas when you define a static method on a custom class, you must use the <xref:System.Linq.IQueryable.Provider%2A> property to expose the LINQ provider.</span></span> <span data-ttu-id="ddade-109">如需詳細資訊，請參閱下列程序後的範例。</span><span class="sxs-lookup"><span data-stu-id="ddade-109">For more information, see the examples that follow the procedures below.</span></span>  
  
 <span data-ttu-id="ddade-110">以下程序提供的重要概述，是關於呼叫模型定義函式做為 <xref:System.Data.Objects.ObjectContext> 物件上的方法，以及呼叫做為自訂類別上的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ddade-110">The procedures below provide high-level outlines for calling a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object and as a static method on a custom class.</span></span> <span data-ttu-id="ddade-111">下面的範例提供更多關於程序中之步驟的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ddade-111">The examples that follow provide more detail about the steps in the procedures.</span></span> <span data-ttu-id="ddade-112">程序假設您已在概念模型中定義函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-112">The procedures assume that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="ddade-113">如需詳細資訊，請參閱 <<c0> [ 如何： 在概念模型中定義自訂函式](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)。</span><span class="sxs-lookup"><span data-stu-id="ddade-113">For more information, see [How to: Define Custom Functions in the Conceptual Model](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-model-defined-function-as-a-method-on-an-objectcontext-object"></a><span data-ttu-id="ddade-114">呼叫模型定義函式做為 ObjectContext 物件上的方法</span><span class="sxs-lookup"><span data-stu-id="ddade-114">To call a model-defined function as a method on an ObjectContext object</span></span>  
  
1.  <span data-ttu-id="ddade-115">加入來源檔案以擴充衍生自 <xref:System.Data.Objects.ObjectContext> 類別的部分類別，該類別由 Entity Framework 工具自動產生。</span><span class="sxs-lookup"><span data-stu-id="ddade-115">Add a source file to extend the partial class derived from the <xref:System.Data.Objects.ObjectContext> class, auto-generated by the Entity Framework tools.</span></span> <span data-ttu-id="ddade-116">在另外的來源檔案中定義 CLR stub，可在檔案重新產生時，防止遺失變更的問題。</span><span class="sxs-lookup"><span data-stu-id="ddade-116">Defining the CLR stub in a separate source file will prevent the changes from being lost when the file is regenerated.</span></span>  
  
2.  <span data-ttu-id="ddade-117">將 Common Language Runtime (CLR) 方法加入至執行下列工作的 <xref:System.Data.Objects.ObjectContext> 類別：</span><span class="sxs-lookup"><span data-stu-id="ddade-117">Add a common language runtime (CLR) method to your <xref:System.Data.Objects.ObjectContext> class that does the following:</span></span>  
  
    -   <span data-ttu-id="ddade-118">對應至概念模型中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-118">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="ddade-119">若要對應方法，您必須將 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 套用至方法。</span><span class="sxs-lookup"><span data-stu-id="ddade-119">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="ddade-120">請注意，屬性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 參數分別是概念模型的命名空間名稱和概念模型中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="ddade-120">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span> <span data-ttu-id="ddade-121">LINQ 的函式名稱解析是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="ddade-121">Function name resolution for LINQ is case sensitive.</span></span>  
  
    -   <span data-ttu-id="ddade-122">傳回由 <xref:System.Linq.IQueryProvider.Execute%2A> 屬性所傳回的 <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> 方法結果。</span><span class="sxs-lookup"><span data-stu-id="ddade-122">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Data.Objects.ObjectContext.QueryProvider%2A> property.</span></span>  
  
3.  <span data-ttu-id="ddade-123">呼叫方法做為 <xref:System.Data.Objects.ObjectContext> 類別之執行個體上的成員。</span><span class="sxs-lookup"><span data-stu-id="ddade-123">Call the method as a member on an instance of the <xref:System.Data.Objects.ObjectContext> class.</span></span>  
  
### <a name="to-call-a-model-defined-function-as-static-method-on-a-custom-class"></a><span data-ttu-id="ddade-124">呼叫模型定義函式做為自訂類別上的靜態方法</span><span class="sxs-lookup"><span data-stu-id="ddade-124">To call a model-defined function as static method on a custom class</span></span>  
  
1.  <span data-ttu-id="ddade-125">使用執行下列工作的靜態方法，將類別加入至您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="ddade-125">Add a class to your application with a static method that does the following:</span></span>  
  
    -   <span data-ttu-id="ddade-126">對應至概念模型中定義的函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-126">Maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="ddade-127">若要對應方法，您必須將 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 套用至方法。</span><span class="sxs-lookup"><span data-stu-id="ddade-127">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="ddade-128">請注意，屬性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 參數分別是概念模型的命名空間名稱和概念模型中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="ddade-128">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model, respectively.</span></span>  
  
    -   <span data-ttu-id="ddade-129">接受 <xref:System.Linq.IQueryable> 引數。</span><span class="sxs-lookup"><span data-stu-id="ddade-129">Accepts an <xref:System.Linq.IQueryable> argument.</span></span>  
  
    -   <span data-ttu-id="ddade-130">由 <xref:System.Linq.IQueryProvider.Execute%2A> 屬性傳回的方法會傳回 <xref:System.Linq.IQueryable.Provider%2A> 的結果。</span><span class="sxs-lookup"><span data-stu-id="ddade-130">Returns the results of the <xref:System.Linq.IQueryProvider.Execute%2A> method that is returned by the <xref:System.Linq.IQueryable.Provider%2A> property.</span></span>  
  
2.  <span data-ttu-id="ddade-131">呼叫方法做為自訂類別上之靜態方法的成員</span><span class="sxs-lookup"><span data-stu-id="ddade-131">Call the method as a member a static method on the custom class</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddade-132">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-132">Example</span></span>  
 <span data-ttu-id="ddade-133">**做為 ObjectContext 物件上的方法中呼叫模型定義函式**</span><span class="sxs-lookup"><span data-stu-id="ddade-133">**Calling a Model-Defined Function as a Method on an ObjectContext Object**</span></span>  
  
 <span data-ttu-id="ddade-134">下列範例示範如何呼叫模型定義函式做為 <xref:System.Data.Objects.ObjectContext> 物件上的方法。</span><span class="sxs-lookup"><span data-stu-id="ddade-134">The following example demonstrates how to call a model-defined function as a method on an <xref:System.Data.Objects.ObjectContext> object.</span></span> <span data-ttu-id="ddade-135">此範例會使用[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)。</span><span class="sxs-lookup"><span data-stu-id="ddade-135">The example uses the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
 <span data-ttu-id="ddade-136">考慮以下傳回特定產品之產品營收的概念模型函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-136">Consider the conceptual model function below that returns product revenue for a specified product.</span></span> <span data-ttu-id="ddade-137">(如需加入函式至概念模型資訊，請參閱[如何： 在概念模型中定義自訂函式](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)。)</span><span class="sxs-lookup"><span data-stu-id="ddade-137">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#4](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#4)]  

## <a name="example"></a><span data-ttu-id="ddade-138">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-138">Example</span></span>  
 <span data-ttu-id="ddade-139">下列程式碼會將方法加入至 `AdventureWorksEntities` 類別，該類別會對應至前述概念模型函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-139">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#2)]
 [!code-vb[DP L2E Methods on ObjectContext#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="ddade-140">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-140">Example</span></span>  
 <span data-ttu-id="ddade-141">下列程式碼會呼叫上述方法，顯示特定產品的產品營收：</span><span class="sxs-lookup"><span data-stu-id="ddade-141">The following code calls the method above to display the product revenue for a specified product:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#3)]
 [!code-vb[DP L2E Methods on ObjectContext#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="ddade-142">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-142">Example</span></span>  
 <span data-ttu-id="ddade-143">下列範例示範如何呼叫傳回集合的模型定義函式 (做為 <xref:System.Linq.IQueryable%601> 物件)。</span><span class="sxs-lookup"><span data-stu-id="ddade-143">The following example demonstrates how to call a model-defined function that returns a collection (as an <xref:System.Linq.IQueryable%601> object).</span></span> <span data-ttu-id="ddade-144">考慮以下傳回指定產品 ID 之所有 `SalesOrderDetails` 的概念模型函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-144">Consider the conceptual model function below that returns all the `SalesOrderDetails` for a given product ID.</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#7](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#7)]  
  
## <a name="example"></a><span data-ttu-id="ddade-145">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-145">Example</span></span>  
 <span data-ttu-id="ddade-146">下列程式碼會將方法加入至 `AdventureWorksEntities` 類別，該類別會對應至前述概念模型函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-146">The following code adds a method to the `AdventureWorksEntities` class that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#8)]
 [!code-vb[DP L2E Methods on ObjectContext#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="ddade-147">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-147">Example</span></span>  
 <span data-ttu-id="ddade-148">下列程式碼會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="ddade-148">The following code calls the method.</span></span> <span data-ttu-id="ddade-149">請注意，傳回的 <xref:System.Linq.IQueryable%601> 查詢會進一步定義，以傳回每一個 `SalesOrderDetail` 的小計總和。</span><span class="sxs-lookup"><span data-stu-id="ddade-149">Note that the returned <xref:System.Linq.IQueryable%601> query is further refined to return line totals for each `SalesOrderDetail`.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#9)]
 [!code-vb[DP L2E Methods on ObjectContext#9](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="ddade-150">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-150">Example</span></span>  
 <span data-ttu-id="ddade-151">**做為自訂類別上的靜態方法呼叫模型定義函式**</span><span class="sxs-lookup"><span data-stu-id="ddade-151">**Calling a Model-Defined Function as a Static Method on a Custom Class**</span></span>  
  
 <span data-ttu-id="ddade-152">下一個範例示範如何呼叫模型定義函式做為自訂類別上的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="ddade-152">The next example demonstrates how to call a model-defined function as a static method on a custom class.</span></span> <span data-ttu-id="ddade-153">此範例會使用[AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832)。</span><span class="sxs-lookup"><span data-stu-id="ddade-153">The example uses the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddade-154">當您呼叫模型定義函式做為自訂類別上的靜態方法時，模型定義函式必須接受集合，並傳回集合中之值的彙總。</span><span class="sxs-lookup"><span data-stu-id="ddade-154">When you call a model-defined function as a static method on a custom class, the model-defined function must accept a collection and return an aggregation of values in the collection.</span></span>  
  
 <span data-ttu-id="ddade-155">考慮以下傳回 SalesOrderDetail 集合之產品營收的概念模型函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-155">Consider the conceptual model function below that returns product revenue for a SalesOrderDetail collection.</span></span> <span data-ttu-id="ddade-156">(如需加入函式至概念模型資訊，請參閱[如何： 在概念模型中定義自訂函式](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f)。)。</span><span class="sxs-lookup"><span data-stu-id="ddade-156">(For information about adding the function to your conceptual model, see [How to: Define Custom Functions in the Conceptual Model](https://msdn.microsoft.com/library/0dad7b8b-58f6-4271-b238-f34810d68e5f).).</span></span>  
  
 [!code-xml[DP L2E Methods on ObjectContext#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp l2e methods on objectcontext/xml/adventureworks.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="ddade-157">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-157">Example</span></span>  
 <span data-ttu-id="ddade-158">下列程式碼會將類別加入至包含靜態方法的應用程式，該靜態方法會對應至前述的概念模型函式。</span><span class="sxs-lookup"><span data-stu-id="ddade-158">The following code adds a class to your application that contains a static method that maps to the conceptual model function above.</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#5)]
 [!code-vb[DP L2E Methods on ObjectContext#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/class1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ddade-159">範例</span><span class="sxs-lookup"><span data-stu-id="ddade-159">Example</span></span>  
 <span data-ttu-id="ddade-160">下列程式碼會呼叫上述方法，顯示 SalesOrderDetail 集合的產品營收：</span><span class="sxs-lookup"><span data-stu-id="ddade-160">The following code calls the method above to display the product revenue for a SalesOrderDetail collection:</span></span>  
  
 [!code-csharp[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e methods on objectcontext/cs/program.cs#6)]
 [!code-vb[DP L2E Methods on ObjectContext#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e methods on objectcontext/vb/module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="ddade-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ddade-161">See Also</span></span>  
 [<span data-ttu-id="ddade-162">.edmx 檔案概觀</span><span class="sxs-lookup"><span data-stu-id="ddade-162">.edmx File Overview</span></span>](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="ddade-163">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="ddade-163">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="ddade-164">在 LINQ to Entities 查詢中呼叫函式</span><span class="sxs-lookup"><span data-stu-id="ddade-164">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)
