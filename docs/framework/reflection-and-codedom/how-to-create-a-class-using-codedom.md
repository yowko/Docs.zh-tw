---
title: "如何：使用 CodeDOM 建立類別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Code Document Object Model, graphs
- Code Document Object Model, creating classes
- graphing with CodeDOM
- CodeDOM, creating classes
- CodeDOM, graphs
ms.assetid: 0ceb70fe-36e1-49bb-922b-e9f615c20a14
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3876ed881d98b4ee0bdb66f43de3de939111d45d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-class-using-codedom"></a><span data-ttu-id="16249-102">如何：使用 CodeDOM 建立類別</span><span class="sxs-lookup"><span data-stu-id="16249-102">How to: Create a Class Using CodeDOM</span></span>
<span data-ttu-id="16249-103">下列程序示範如何建立及編譯 CodeDOM 圖表，其可產生包含兩個欄位、三種屬性、一種方法、一個建構函式和一個進入點的類別。</span><span class="sxs-lookup"><span data-stu-id="16249-103">The following procedures illustrate how to create and compile a CodeDOM graph that generates a class containing two fields, three properties, a method, a constructor, and an entry point.</span></span>  
  
1.  <span data-ttu-id="16249-104">建立主控台應用程式，使用 CodeDOM 程式碼產生類別的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="16249-104">Create a console application that will use CodeDOM code to generate the source code for a class.</span></span>  
  
     <span data-ttu-id="16249-105">在此範例中，則產生的類別命名為 `Sample`，而產生的程式碼類別名為 `CodeDOMCreatedClass`，其位於 SampleCode 檔案中。</span><span class="sxs-lookup"><span data-stu-id="16249-105">In this example, the generating class is named `Sample`, and the generated code is a class named `CodeDOMCreatedClass` in a file named SampleCode.</span></span>  
  
2.  <span data-ttu-id="16249-106">在產生的類別中，初始化 CodeDOM 圖表並使用 CodeDOM 方法來定義所產生類別的成員、建構函式及進入點 (`Main` 方法)。</span><span class="sxs-lookup"><span data-stu-id="16249-106">In the generating class, initialize the CodeDOM graph and use CodeDOM methods to define the members, constructor, and entry point (`Main` method) of the generated class.</span></span>  
  
     <span data-ttu-id="16249-107">在此範例中，產生的類別有兩個欄位、 三個屬性、 建構函式、 方法和 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="16249-107">In this example, the generated class has two fields, three properties, a constructor, a method, and a `Main` method.</span></span>  
  
3.  <span data-ttu-id="16249-108">在產生之類別中，建立特定語言的程式碼提供者並呼叫其 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 圖表產生程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="16249-108">In the generating class, create a language-specific code provider and call its <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method to generate the code from the graph.</span></span>  
  
4.  <span data-ttu-id="16249-109">編譯並執行應用程式產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="16249-109">Compile and execute the application to generate the code.</span></span>  
  
     <span data-ttu-id="16249-110">在此範例中，產生的程式碼是在名為 SampleCode 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="16249-110">In this example, the generated code is in a file named SampleCode.</span></span> <span data-ttu-id="16249-111">編譯並執行此程式碼，請參閱範例輸出。</span><span class="sxs-lookup"><span data-stu-id="16249-111">Compile and execute that code to see the sample output.</span></span>  
  
### <a name="to-create-the-application-that-will-execute-the-codedom-code"></a><span data-ttu-id="16249-112">若要建立會執行 CodeDOM 程式碼的應用程式</span><span class="sxs-lookup"><span data-stu-id="16249-112">To create the application that will execute the CodeDOM code</span></span>  
  
-   <span data-ttu-id="16249-113">建立主控台應用程式類別以包含 CodeDOM 程式碼。</span><span class="sxs-lookup"><span data-stu-id="16249-113">Create a console application class to contain the CodeDOM code.</span></span> <span data-ttu-id="16249-114">定義在類別中用以參考組件 (<xref:System.CodeDom.CodeCompileUnit>) 和類別 (<xref:System.CodeDom.CodeTypeDeclaration>) 的全域欄位，指定產生的來源檔案名稱，並宣告 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="16249-114">Define the global fields that are to be used in the class to reference the assembly (<xref:System.CodeDom.CodeCompileUnit>) and class (<xref:System.CodeDom.CodeTypeDeclaration>), specify the name of the generated source file, and declare the `Main` method.</span></span>  
  
     <span data-ttu-id="16249-115">[!code-csharp[CodeDOM 類別範例主要 #1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)][!code-vb[CodeDOM 類別範例主要 #1  ](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="16249-115">[!code-csharp[CodeDOM Class Sample Main#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample Main/CS/program.cs#1)]  [!code-vb[CodeDOM Class Sample Main#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample Main/VB/program.vb#1)]</span></span>  
  
### <a name="to-initialize-the-codedom-graph"></a><span data-ttu-id="16249-116">初始化 CodeDOM 圖表</span><span class="sxs-lookup"><span data-stu-id="16249-116">To initialize the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="16249-117">在主控台應用程式類別的建構函式中，初始化組件和類別，並將適當的宣告新增至 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="16249-117">In the constructor for the console application class, initialize the assembly and class, and add the appropriate declarations to the CodeDOM graph.</span></span>  
  
     <span data-ttu-id="16249-118">[!code-csharp[CodeDOM 類別範例#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)][!code-vb[CodeDOM 類別範例#2 ](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="16249-118">[!code-csharp[CodeDOM Class Sample#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#2)]  [!code-vb[CodeDOM Class Sample#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#2)]</span></span>  
  
### <a name="to-add-members-to-the-codedom-graph"></a><span data-ttu-id="16249-119">將成員新增至 CodeDOM 圖表</span><span class="sxs-lookup"><span data-stu-id="16249-119">To add members to the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="16249-120">將 <xref:System.CodeDom.CodeMemberField> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將欄位新增至 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="16249-120">Add fields to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberField> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     <span data-ttu-id="16249-121">[!code-csharp[CodeDOM 類別範例#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)][!code-vb[CodeDOM 類別範例#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="16249-121">[!code-csharp[CodeDOM Class Sample#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#3)]  [!code-vb[CodeDOM Class Sample#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#3)]</span></span>  
  
-   <span data-ttu-id="16249-122">將 <xref:System.CodeDom.CodeMemberProperty> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將屬性新增至 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="16249-122">Add properties to the CodeDOM graph by adding <xref:System.CodeDom.CodeMemberProperty> objects to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     <span data-ttu-id="16249-123">[!code-csharp[CodeDOM 類別範例#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)][!code-vb[CodeDOM 類別範例#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="16249-123">[!code-csharp[CodeDOM Class Sample#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#4)]  [!code-vb[CodeDOM Class Sample#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#4)]</span></span>  
  
-   <span data-ttu-id="16249-124">將 <xref:System.CodeDom.CodeMemberMethod> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將方法新增至 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="16249-124">Add a method to the CodeDOM graph by adding a <xref:System.CodeDom.CodeMemberMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     <span data-ttu-id="16249-125">[!code-csharp[CodeDOM 類別範例#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)][!code-vb[CodeDOM 類別範例#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]</span><span class="sxs-lookup"><span data-stu-id="16249-125">[!code-csharp[CodeDOM Class Sample#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#5)]  [!code-vb[CodeDOM Class Sample#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#5)]</span></span>  
  
-   <span data-ttu-id="16249-126">將 <xref:System.CodeDom.CodeConstructor> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，將以建構函式新增至 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="16249-126">Add a constructor to the CodeDOM graph by adding a <xref:System.CodeDom.CodeConstructor> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     <span data-ttu-id="16249-127">[!code-csharp[CodeDOM 類別範例#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)][!code-vb[CodeDOM 類別範例#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]</span><span class="sxs-lookup"><span data-stu-id="16249-127">[!code-csharp[CodeDOM Class Sample#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#6)]  [!code-vb[CodeDOM Class Sample#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#6)]</span></span>  
  
-   <span data-ttu-id="16249-128">將 <xref:System.CodeDom.CodeEntryPointMethod> 物件新增至類別的 <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> 屬性，以將進入點新增至 CodeDOM 圖表。</span><span class="sxs-lookup"><span data-stu-id="16249-128">Add an entry point to the CodeDOM graph by adding a <xref:System.CodeDom.CodeEntryPointMethod> object to the <xref:System.CodeDom.CodeTypeDeclaration.Members%2A> property of the class.</span></span>  
  
     <span data-ttu-id="16249-129">[!code-csharp[CodeDOM 類別範例#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)][!code-vb[CodeDOM 類別範例#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]</span><span class="sxs-lookup"><span data-stu-id="16249-129">[!code-csharp[CodeDOM Class Sample#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#7)]  [!code-vb[CodeDOM Class Sample#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#7)]</span></span>  
  
### <a name="to-generate-the-code-from-the-codedom-graph"></a><span data-ttu-id="16249-130">從 CodeDOM 圖表產生程式碼</span><span class="sxs-lookup"><span data-stu-id="16249-130">To generate the code from the CodeDOM graph</span></span>  
  
-   <span data-ttu-id="16249-131">呼叫 <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> 方法，從 CodeDOM 圖表產生原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="16249-131">Generate source code from the CodeDOM graph by calling the <xref:System.CodeDom.Compiler.CodeDomProvider.GenerateCodeFromCompileUnit%2A> method.</span></span>  
  
     <span data-ttu-id="16249-132">[!code-csharp[CodeDOM 類別範例#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)][!code-vb[CodeDOM 類別範例#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]</span><span class="sxs-lookup"><span data-stu-id="16249-132">[!code-csharp[CodeDOM Class Sample#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#8)]  [!code-vb[CodeDOM Class Sample#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#8)]</span></span>  
  
### <a name="to-create-the-graph-and-generate-the-code"></a><span data-ttu-id="16249-133">建立圖形並產生程式碼</span><span class="sxs-lookup"><span data-stu-id="16249-133">To create the graph and generate the code</span></span>  
  
1.  <span data-ttu-id="16249-134">將前面步驟建立的方法新增至步驟 1 定義的 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="16249-134">Add the methods created in the preceding steps to the `Main` method defined in the first step.</span></span>  
  
     <span data-ttu-id="16249-135">[!code-csharp[CodeDOM 類別範例#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)][!code-vb[CodeDOM 類類別範例#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]</span><span class="sxs-lookup"><span data-stu-id="16249-135">[!code-csharp[CodeDOM Class Sample#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#9)]  [!code-vb[CodeDOM Class Sample#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#9)]</span></span>  
  
2.  <span data-ttu-id="16249-136">編譯並執行產生的類別。</span><span class="sxs-lookup"><span data-stu-id="16249-136">Compile and execute the generating class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16249-137">範例</span><span class="sxs-lookup"><span data-stu-id="16249-137">Example</span></span>  
 <span data-ttu-id="16249-138">下列程式碼範例會顯示前幾個步驟的程式碼。</span><span class="sxs-lookup"><span data-stu-id="16249-138">The following code example shows the code from the preceding steps.</span></span>  
  
 <span data-ttu-id="16249-139">[!code-csharp[CodeDOM 類別範例#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)][!code-vb[CodeDOM 類別範例#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="16249-139">[!code-csharp[CodeDOM Class Sample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/program.cs#1)] [!code-vb[CodeDOM Class Sample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/program.vb#1)]</span></span>  
  
 <span data-ttu-id="16249-140">前例編譯並執行後，即會產生下列原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="16249-140">When the preceding example is compiled and executed, it produces the following source code.</span></span>  
  
 <span data-ttu-id="16249-141">[!code-csharp[CodeDOM 類別範例#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)][!code-vb[CodeDOM 類別範例#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]</span><span class="sxs-lookup"><span data-stu-id="16249-141">[!code-csharp[CodeDOM Class Sample#99](../../../samples/snippets/csharp/VS_Snippets_CLR/CodeDOM Class Sample/CS/SampleCode.cs#99)] [!code-vb[CodeDOM Class Sample#99](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CodeDOM Class Sample/VB/SampleCode.vb#99)]</span></span>  
  
 <span data-ttu-id="16249-142">編譯並執行後，產生的原始程式碼會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="16249-142">The generated source code produces the following output when compiled and executed.</span></span>  
  
```  
The object:  
 width = 5.3,  
 height = 6.9,  
 area = 36.57  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="16249-143">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="16249-143">Compiling the Code</span></span>  
  
-   <span data-ttu-id="16249-144">此程式碼範例需要設定 `FullTrust` 權限，才能順利執行。</span><span class="sxs-lookup"><span data-stu-id="16249-144">This code example requires the `FullTrust` permission set to execute successfully.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16249-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16249-145">See Also</span></span>  
 <span data-ttu-id="16249-146">[使用 CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md) </span><span class="sxs-lookup"><span data-stu-id="16249-146">[Using the CodeDOM](../../../docs/framework/reflection-and-codedom/using-the-codedom.md) </span></span>  
 [<span data-ttu-id="16249-147">從 CodeDOM 圖表產生和編譯原始程式碼</span><span class="sxs-lookup"><span data-stu-id="16249-147">Generating and Compiling Source Code from a CodeDOM Graph</span></span>](../../../docs/framework/reflection-and-codedom/generating-and-compiling-source-code-from-a-codedom-graph.md)

