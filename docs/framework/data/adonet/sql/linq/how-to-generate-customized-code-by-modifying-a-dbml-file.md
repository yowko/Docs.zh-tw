---
title: 作法：藉由修改 DBML 檔案產生自訂程式碼
ms.date: 03/30/2017
ms.assetid: 50ad597a-8598-42d3-82dd-fc7d702ebc37
ms.openlocfilehash: ab49f76a0d5e7338a93e21ae9a8d1d9d74a21e82
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173435"
---
# <a name="how-to-generate-customized-code-by-modifying-a-dbml-file"></a><span data-ttu-id="e6420-102">作法：藉由修改 DBML 檔案產生自訂程式碼</span><span class="sxs-lookup"><span data-stu-id="e6420-102">How to: Generate Customized Code by Modifying a DBML File</span></span>

<span data-ttu-id="e6420-103">您可以從資料庫標記語言產生 Visual Basic 或 c # 原始程式碼， ( .dbml) 中繼資料檔案。</span><span class="sxs-lookup"><span data-stu-id="e6420-103">You can generate Visual Basic or C# source code from a database markup language (.dbml) metadata file.</span></span> <span data-ttu-id="e6420-104">這種方法讓您有機會在產生應用程式對應程式碼之前，先自訂預設 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="e6420-104">This approach provides an opportunity to customize the default .dbml file before you generate the application mapping code.</span></span> <span data-ttu-id="e6420-105">這是一項進階功能。</span><span class="sxs-lookup"><span data-stu-id="e6420-105">This is an advanced feature.</span></span>  
  
 <span data-ttu-id="e6420-106">這項處理的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="e6420-106">The steps in this process are as follows:</span></span>  
  
1. <span data-ttu-id="e6420-107">產生 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="e6420-107">Generate a .dbml file.</span></span>  
  
2. <span data-ttu-id="e6420-108">使用編輯器修改 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="e6420-108">Use an editor to modify the .dbml file.</span></span> <span data-ttu-id="e6420-109">請注意，.dbml 檔必須針對 .dbml 檔案，針對 () .xsd 檔案的架構定義進行驗證。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6420-109">Note that the .dbml file must validate against the schema definition (.xsd) file for [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .dbml files.</span></span> <span data-ttu-id="e6420-110">如需詳細資訊，請參閱 [LINQ to SQL 中的程式碼產生](code-generation-in-linq-to-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="e6420-110">For more information, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
3. <span data-ttu-id="e6420-111">產生 Visual Basic 或 c # 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6420-111">Generate the Visual Basic or C# source code.</span></span>  
  
 <span data-ttu-id="e6420-112">下列範例會使用 SQLMetal 命令列工具。</span><span class="sxs-lookup"><span data-stu-id="e6420-112">The following examples use the SQLMetal command-line tool.</span></span> <span data-ttu-id="e6420-113">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="e6420-113">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6420-114">範例</span><span class="sxs-lookup"><span data-stu-id="e6420-114">Example</span></span>  

 <span data-ttu-id="e6420-115">下列程式碼會從 Northwind 範例資料庫產生 .dbml 檔。</span><span class="sxs-lookup"><span data-stu-id="e6420-115">The following code generates a .dbml file from the Northwind sample database.</span></span> <span data-ttu-id="e6420-116">若為資料庫中繼資料的來源，您可以使用資料庫的名稱或 .mdf 檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6420-116">As source for the database metadata, you can use either the name of the database or the name of the .mdf file.</span></span>  
  
```console  
sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml  
sqlmetal /dbml:mymeta.dbml mydbfile.mdf  
```  
  
## <a name="example"></a><span data-ttu-id="e6420-117">範例</span><span class="sxs-lookup"><span data-stu-id="e6420-117">Example</span></span>  

 <span data-ttu-id="e6420-118">下列程式碼會從 .dbml 檔產生 Visual Basic 或 c # 原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="e6420-118">The following code generates Visual Basic or C# source code file from a .dbml file.</span></span>  
  
```console
sqlmetal /namespace:nwind /code:nwind.vb /language:vb DBMLFile.dbml  
sqlmetal /namespace:nwind /code:nwind.cs /language:csharp DBMLFile.dbml  
```  
  
## <a name="see-also"></a><span data-ttu-id="e6420-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6420-119">See also</span></span>

- [<span data-ttu-id="e6420-120">LINQ to SQL 中的程式碼產生</span><span class="sxs-lookup"><span data-stu-id="e6420-120">Code Generation in LINQ to SQL</span></span>](code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="e6420-121">SqlMetal.exe (程式碼產生工具) </span><span class="sxs-lookup"><span data-stu-id="e6420-121">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
- [<span data-ttu-id="e6420-122">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="e6420-122">Creating the Object Model</span></span>](creating-the-object-model.md)
