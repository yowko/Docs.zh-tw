---
title: 如何：呼叫自訂資料庫函式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4354e5eb-dd45-469d-97fb-1c495705ee59
ms.openlocfilehash: 9879803c970b7965bf152c216367b216e201af38
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540304"
---
# <a name="how-to-call-custom-database-functions"></a><span data-ttu-id="4f41e-102">如何：呼叫自訂資料庫函式</span><span class="sxs-lookup"><span data-stu-id="4f41e-102">How to: Call Custom Database Functions</span></span>

<span data-ttu-id="4f41e-103">本主題描述如何呼叫資料庫中定義的自訂資料庫函式，而資料庫是來自 LINQ to Entities 查詢。</span><span class="sxs-lookup"><span data-stu-id="4f41e-103">This topic describes how to call custom functions that are defined in the database from within LINQ to Entities queries.</span></span>

<span data-ttu-id="4f41e-104">從 LINQ to Entities 查詢呼叫的資料庫函式會在資料庫中執行。</span><span class="sxs-lookup"><span data-stu-id="4f41e-104">Database functions that are called from LINQ to Entities queries are executed in the database.</span></span> <span data-ttu-id="4f41e-105">在資料庫中執行函式可提升應用程式效能。</span><span class="sxs-lookup"><span data-stu-id="4f41e-105">Executing functions in the database can improve application performance.</span></span>

<span data-ttu-id="4f41e-106">以下程序提供關於呼叫自訂資料庫函式的重要概述。</span><span class="sxs-lookup"><span data-stu-id="4f41e-106">The procedure below provides a high-level outline for calling a custom database function.</span></span> <span data-ttu-id="4f41e-107">程序後的範例提供程序中之步驟相關詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4f41e-107">The example that follows provides more detail about the steps in the procedure.</span></span>

## <a name="to-call-custom-functions-that-are-defined-in-the-database"></a><span data-ttu-id="4f41e-108">呼叫在資料庫中定義的自訂函式</span><span class="sxs-lookup"><span data-stu-id="4f41e-108">To call custom functions that are defined in the database</span></span>

1. <span data-ttu-id="4f41e-109">在您的資料庫中建立自訂函式。</span><span class="sxs-lookup"><span data-stu-id="4f41e-109">Create a custom function in your database.</span></span>

     <span data-ttu-id="4f41e-110">如需在 SQL Server 中建立自訂函數的詳細資訊，請參閱 [CREATE FUNCTION (transact-sql) ](/sql/t-sql/statements/create-function-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4f41e-110">For more information about creating custom functions in SQL Server, see [CREATE FUNCTION (Transact-SQL)](/sql/t-sql/statements/create-function-transact-sql).</span></span>

2. <span data-ttu-id="4f41e-111">在 .edmx 檔案的存放結構定義語言 (SSDL) 中宣告函式。</span><span class="sxs-lookup"><span data-stu-id="4f41e-111">Declare a function in the store schema definition language (SSDL) of your .edmx file.</span></span> <span data-ttu-id="4f41e-112">函式的名稱必須和資料庫中宣告的函式名稱一樣。</span><span class="sxs-lookup"><span data-stu-id="4f41e-112">The name of the function must be the same as the name of the function declared in the database.</span></span>

     <span data-ttu-id="4f41e-113">如需詳細資訊，請參閱 [ (SSDL) 的 Function 元素 ](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl)。</span><span class="sxs-lookup"><span data-stu-id="4f41e-113">For more information, see [Function Element (SSDL)](/ef/ef6/modeling/designer/advanced/edmx/ssdl-spec#function-element-ssdl).</span></span>

3. <span data-ttu-id="4f41e-114">將對應的方法加入至應用程式程式碼的類別中，然後將 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> 套用至方法。請注意，屬性的 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> 和 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> 參數分別是概念模型的命名空間名稱和概念模型中的函式名稱。</span><span class="sxs-lookup"><span data-stu-id="4f41e-114">Add a corresponding method to a class in your application code and apply a <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="4f41e-115">LINQ 的函式名稱解析是區分大小寫的。</span><span class="sxs-lookup"><span data-stu-id="4f41e-115">Function name resolution for LINQ is case sensitive.</span></span>

4. <span data-ttu-id="4f41e-116">呼叫 LINQ to Entities 查詢中的方法。</span><span class="sxs-lookup"><span data-stu-id="4f41e-116">Call the method in a LINQ to Entities query.</span></span>  

## <a name="example"></a><span data-ttu-id="4f41e-117">範例</span><span class="sxs-lookup"><span data-stu-id="4f41e-117">Example</span></span>

<span data-ttu-id="4f41e-118">下列範例示範如何從 LINQ to Entities 查詢中呼叫自訂資料庫函式。</span><span class="sxs-lookup"><span data-stu-id="4f41e-118">The following example demonstrates how to call a custom database function from within a LINQ to Entities query.</span></span> <span data-ttu-id="4f41e-119">範例使用 School 模型。</span><span class="sxs-lookup"><span data-stu-id="4f41e-119">The example uses the School model.</span></span> <span data-ttu-id="4f41e-120">如需 School 模型的相關資訊，請參閱 [建立 School 範例資料庫](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) 和 [產生 school .edmx](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100))檔案。</span><span class="sxs-lookup"><span data-stu-id="4f41e-120">For information about the School model, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)) and [Generating the School .edmx File](/previous-versions/dotnet/netframework-4.0/bb399739(v=vs.100)).</span></span>

<span data-ttu-id="4f41e-121">下列程式碼會將 `AvgStudentGrade` 函式加入至 School 範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="4f41e-121">The following code adds the `AvgStudentGrade` function to the School sample database.</span></span>

> [!NOTE]
> <span data-ttu-id="4f41e-122">無論資料庫伺服器為何，呼叫自訂資料庫函式的步驟都一樣。</span><span class="sxs-lookup"><span data-stu-id="4f41e-122">The steps for calling a custom database function are the same regardless of the database server.</span></span> <span data-ttu-id="4f41e-123">不過，下列程式碼是專門在 SQL Server 資料庫中建立函式。</span><span class="sxs-lookup"><span data-stu-id="4f41e-123">However, the code below is specific to creating a function in a SQL Server database.</span></span> <span data-ttu-id="4f41e-124">在其他資料庫中建立自訂函式的程式碼應該會不同。</span><span class="sxs-lookup"><span data-stu-id="4f41e-124">The code for creating a custom function in other database servers might differ.</span></span>

[!code-sql[DP L2E MapToDBFunction#1](~/samples/snippets/tsql/VS_Snippets_Data/dp l2e maptodbfunction/tsql/create_avgstudentgrade.sql#1)]

## <a name="example"></a><span data-ttu-id="4f41e-125">範例</span><span class="sxs-lookup"><span data-stu-id="4f41e-125">Example</span></span>

<span data-ttu-id="4f41e-126">接下來，在您 *.edmx* 檔案的存放結構定義語言 (SSDL) 中宣告函數。</span><span class="sxs-lookup"><span data-stu-id="4f41e-126">Next, declare a function in the store schema definition language (SSDL) of your *.edmx* file.</span></span> <span data-ttu-id="4f41e-127">下列程式碼會 `AvgStudentGrade` 在 SSDL 中宣告函數：</span><span class="sxs-lookup"><span data-stu-id="4f41e-127">The following code declares the `AvgStudentGrade` function in SSDL:</span></span>

[!code-xml[DP L2E MapToDBFunction#2](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/school.edmx#2)]

## <a name="example"></a><span data-ttu-id="4f41e-128">範例</span><span class="sxs-lookup"><span data-stu-id="4f41e-128">Example</span></span>

<span data-ttu-id="4f41e-129">現在，建立方法，並將它對應至 SSDL 中宣告的函式。</span><span class="sxs-lookup"><span data-stu-id="4f41e-129">Now, create a method and map it to the function declared in the SSDL.</span></span> <span data-ttu-id="4f41e-130">使用 <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>，將下列類別中的方法對應至 SSDL 中宣告的函式 (如上所述)。</span><span class="sxs-lookup"><span data-stu-id="4f41e-130">The method in the following class is mapped to the function defined in the SSDL (above) by using an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span></span> <span data-ttu-id="4f41e-131">呼叫此方法時，會執行資料庫中對應的函式。</span><span class="sxs-lookup"><span data-stu-id="4f41e-131">When this method is called, the corresponding function in the database is executed.</span></span>

[!code-csharp[DP L2E MapToDBFunction#3](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#3)]
[!code-vb[DP L2E MapToDBFunction#3](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#3)]

## <a name="example"></a><span data-ttu-id="4f41e-132">範例</span><span class="sxs-lookup"><span data-stu-id="4f41e-132">Example</span></span>

<span data-ttu-id="4f41e-133">最後，呼叫 LINQ to Entities 查詢中的方法。</span><span class="sxs-lookup"><span data-stu-id="4f41e-133">Finally, call the method in a LINQ to Entities query.</span></span> <span data-ttu-id="4f41e-134">下列程式碼會將學生的姓氏和平均分數顯示在主控台上：</span><span class="sxs-lookup"><span data-stu-id="4f41e-134">The following code displays students' last names and average grades to the console:</span></span>

[!code-csharp[DP L2E MapToDBFunction#4](~/samples/snippets/csharp/VS_Snippets_Data/dp l2e maptodbfunction/cs/program.cs#4)]
[!code-vb[DP L2E MapToDBFunction#4](~/samples/snippets/visualbasic/VS_Snippets_Data/dp l2e maptodbfunction/vb/module1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="4f41e-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f41e-135">See also</span></span>

- <span data-ttu-id="4f41e-136">[.edmx 檔概觀](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4f41e-136">[.edmx File Overview](/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100))</span></span>
- [<span data-ttu-id="4f41e-137">LINQ to Entities 中的查詢</span><span class="sxs-lookup"><span data-stu-id="4f41e-137">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
