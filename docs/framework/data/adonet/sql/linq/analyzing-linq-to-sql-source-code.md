---
title: 分析 LINQ to SQL 原始程式碼
ms.date: 03/30/2017
ms.assetid: cba3eef8-e108-4478-b588-ad59580e133e
ms.openlocfilehash: 1110e64d16a6c2790939cc695ecd67e37ec109e4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203284"
---
# <a name="analyzing-linq-to-sql-source-code"></a><span data-ttu-id="e2c51-102">分析 LINQ to SQL 原始程式碼</span><span class="sxs-lookup"><span data-stu-id="e2c51-102">Analyzing LINQ to SQL Source Code</span></span>
<span data-ttu-id="e2c51-103">使用下列步驟，您就可以從 Northwind 範例資料庫產生 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2c51-103">By using the following steps, you can produce [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] source code from the Northwind sample database.</span></span> <span data-ttu-id="e2c51-104">您可以比較物件模型的項目與資料庫的項目，進一步了解不同項目的對應方式。</span><span class="sxs-lookup"><span data-stu-id="e2c51-104">You can compare elements of the object model with elements of the database to better see how different items are mapped.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2c51-105">使用 Visual Studio 的開發人員可以使用[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]來產生此程式碼。</span><span class="sxs-lookup"><span data-stu-id="e2c51-105">Developers using Visual Studio can use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to produce this code.</span></span>  
  
1.  <span data-ttu-id="e2c51-106">如果您的開發電腦上還沒有 Northwind 範例資料庫，則可以免費進行下載。</span><span class="sxs-lookup"><span data-stu-id="e2c51-106">If you do not already have the Northwind sample database on your development computer, you can download it free of charge.</span></span> <span data-ttu-id="e2c51-107">如需詳細資訊，請參閱 <<c0> [ 下載範例資料庫](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c51-107">For more information, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
2.  <span data-ttu-id="e2c51-108">使用 SqlMetal 命令列工具產生 Visual Basic 或 C# 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="e2c51-108">Use the SqlMetal command-line tool to generate a Visual Basic or C# source file.</span></span> <span data-ttu-id="e2c51-109">如需詳細資訊，請參閱 [SqlMetal.exe (程式碼產生工具)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)。</span><span class="sxs-lookup"><span data-stu-id="e2c51-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span> <span data-ttu-id="e2c51-110">在命令提示字元中輸入下列命令，就可以產生內含預存程序 (Stored Procedure) 和函式的 Visual Basic 和 C# 原始程式檔：</span><span class="sxs-lookup"><span data-stu-id="e2c51-110">By typing the following commands at a command prompt, you can generate Visual Basic and C# source files that include stored procedures and functions:</span></span>  
  
    -   `sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
    -   `sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize`  
  
## <a name="see-also"></a><span data-ttu-id="e2c51-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2c51-111">See also</span></span>

- [<span data-ttu-id="e2c51-112">參考資料</span><span class="sxs-lookup"><span data-stu-id="e2c51-112">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="e2c51-113">背景資訊</span><span class="sxs-lookup"><span data-stu-id="e2c51-113">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
