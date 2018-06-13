---
title: 如何：在 Visual Basic 或 C# 中產生物件模型
ms.date: 03/30/2017
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
ms.openlocfilehash: ce7f1f30a606c0d0c81a1afbfc2552ece4fc1029
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360389"
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="9b04e-102">如何：在 Visual Basic 或 C# 中產生物件模型</span><span class="sxs-lookup"><span data-stu-id="9b04e-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="9b04e-103">在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中，採用您自己之程式語言的物件模型 (Object Model) 會對應至關聯式資料庫。</span><span class="sxs-lookup"><span data-stu-id="9b04e-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="9b04e-104">兩個工具可供自動產生 從現有資料庫的中繼資料 Visual Basic 或 C# 模型。</span><span class="sxs-lookup"><span data-stu-id="9b04e-104">Two tools are available for automatically generating a Visual Basic or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="9b04e-105">如果您使用 Visual Studio，您可以使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]產生物件模型。</span><span class="sxs-lookup"><span data-stu-id="9b04e-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="9b04e-106">[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]提供豐富的使用者介面，可協助您產生[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]物件模型。</span><span class="sxs-lookup"><span data-stu-id="9b04e-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="9b04e-107">如需詳細資訊，請參閱[Linq to SQL 工具，Visual Studio 中](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)。</span><span class="sxs-lookup"><span data-stu-id="9b04e-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="9b04e-108">SQLMetal 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="9b04e-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="9b04e-109">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="9b04e-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b04e-110">如果您沒有現有的資料庫而想要從物件模型建立一個資料庫，可以使用程式碼編輯器和 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 建立物件模型。</span><span class="sxs-lookup"><span data-stu-id="9b04e-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="9b04e-111">如需詳細資訊，請參閱[How to： 動態建立資料庫](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)。</span><span class="sxs-lookup"><span data-stu-id="9b04e-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="9b04e-112">文件[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]提供有關如何使用產生的 Visual Basic 或 C# 物件模型的範例[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9b04e-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a Visual Basic or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="9b04e-113">下列資訊提供了如何使用 SQLMetal 命令列工具的範例。</span><span class="sxs-lookup"><span data-stu-id="9b04e-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="9b04e-114">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="9b04e-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b04e-115">範例</span><span class="sxs-lookup"><span data-stu-id="9b04e-115">Example</span></span>  
 <span data-ttu-id="9b04e-116">下列範例所示的 SQLMetal 命令列產生 Visual Basic 程式碼，當做 Northwind 範例資料庫之以屬性為基礎的物件模型。</span><span class="sxs-lookup"><span data-stu-id="9b04e-116">The SQLMetal command line shown in the following example produces Visual Basic code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="9b04e-117">預存程序和函式也會呈現。</span><span class="sxs-lookup"><span data-stu-id="9b04e-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="9b04e-118">範例</span><span class="sxs-lookup"><span data-stu-id="9b04e-118">Example</span></span>  
 <span data-ttu-id="9b04e-119">下列範例中所示的 SQLMetal 命令列產生的 C# 程式碼與 Northwind 範例資料庫之以屬性為基礎的物件模型相同。</span><span class="sxs-lookup"><span data-stu-id="9b04e-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="9b04e-120">預存程序和函式也會呈現，而且會自動將資料表名稱複數化。</span><span class="sxs-lookup"><span data-stu-id="9b04e-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b04e-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b04e-121">See Also</span></span>  
 [<span data-ttu-id="9b04e-122">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="9b04e-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="9b04e-123">LINQ to SQL 物件模型</span><span class="sxs-lookup"><span data-stu-id="9b04e-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="9b04e-124">依逐步解說學習</span><span class="sxs-lookup"><span data-stu-id="9b04e-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="9b04e-125">如何：使用程式碼編輯器自訂實體類別</span><span class="sxs-lookup"><span data-stu-id="9b04e-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="9b04e-126">以屬性為基礎的對應</span><span class="sxs-lookup"><span data-stu-id="9b04e-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="9b04e-127">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="9b04e-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="9b04e-128">外部對應</span><span class="sxs-lookup"><span data-stu-id="9b04e-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="9b04e-129">下載範例資料庫</span><span class="sxs-lookup"><span data-stu-id="9b04e-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="9b04e-130">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="9b04e-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
