---
title: HOW TO：藉由修改 DBML 檔案產生自訂程式碼
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: c3fa4d9db4076309ab7d6066cc7072797eaead54
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338419"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="93623-102">HOW TO：藉由修改 DBML 檔案產生自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="93623-102">How to: Generate Customized Code by Modifying a DBML File</span></span>
<span data-ttu-id="93623-103">您可以產生 Visual Basic 或C#從資料庫標記語言 (.dbml) 中繼資料檔案的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="93623-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="93623-104">這種方法讓您有機會在產生應用程式對應程式碼之前，先自訂預設 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="93623-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="93623-105">這是一項進階功能。</span><span class="sxs-lookup"><span data-stu-id="93623-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="93623-106">這項處理的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="93623-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="93623-107">產生 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="93623-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="93623-108">使用編輯器修改 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="93623-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="93623-109">請注意，針對的結構描述定義 (.xsd) 檔驗證.dbml 檔案，必須[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].dbml 檔案。</span><span class="sxs-lookup"><span data-stu-id="93623-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="93623-110">如需詳細資訊，請參閱 < [LINQ to SQL 中的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="93623-110">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="93623-111">產生 Visual Basic 或C#原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="93623-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="93623-112">下列範例會使用 SQLMetal 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="93623-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="93623-113">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="93623-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="93623-114">範例</span><span class="sxs-lookup"><span data-stu-id="93623-114">Example</span></span>  
 <span data-ttu-id="93623-115">下列程式碼會從 Northwind 範例資料庫產生 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="93623-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="93623-116">若為資料庫中繼資料的來源，您可以使用資料庫的名稱或 .mdf 檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="93623-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="93623-117">範例</span><span class="sxs-lookup"><span data-stu-id="93623-117">Example</span></span>  
 <span data-ttu-id="93623-118">下列程式碼會產生 Visual Basic 或C#從.dbml 檔的原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="93623-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```  
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="93623-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93623-119">See also</span></span>

- [<span data-ttu-id="93623-120">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="93623-120">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="93623-121">SqlMetal.exe (程式碼產生工具)</span><span class="sxs-lookup"><span data-stu-id="93623-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="93623-122">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="93623-122">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
