---
title: 程式設計手冊
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: 542567cf07e86b642a23a879fa6e5476253005b8
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78848934"
---
# <a name="programming-guide"></a><span data-ttu-id="1ea46-102">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="1ea46-102">Programming Guide</span></span>
<span data-ttu-id="1ea46-103">本節包含如何建立和使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型 (Object Model) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1ea46-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="1ea46-104">如果使用 Visual Studio，也可以使用物件關係設計器執行許多相同的任務。</span><span class="sxs-lookup"><span data-stu-id="1ea46-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="1ea46-105">您還可以搜索 Microsoft 文檔以查找特定問題，還可以參加[LINQ 論壇](https://social.msdn.microsoft.com/forums/home?forum=linqtosql)，與專家詳細討論更複雜的主題。</span><span class="sxs-lookup"><span data-stu-id="1ea46-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://social.msdn.microsoft.com/forums/home?forum=linqtosql), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="1ea46-106">最後[，LINQ 到 SQL：.NET 語言集成查詢關係資料](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10))白皮書詳細介紹了[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]技術，並附有視覺化基本和 C# 代碼示例。</span><span class="sxs-lookup"><span data-stu-id="1ea46-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://docs.microsoft.com/previous-versions/dotnet/articles/bb425822(v=msdn.10)) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ea46-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="1ea46-107">In This Section</span></span>  
 [<span data-ttu-id="1ea46-108">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="1ea46-108">Creating the Object Model</span></span>](creating-the-object-model.md)  
 <span data-ttu-id="1ea46-109">描述如何產生物件模型。</span><span class="sxs-lookup"><span data-stu-id="1ea46-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="1ea46-110">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="1ea46-110">Communicating with the Database</span></span>](communicating-with-the-database.md)  
 <span data-ttu-id="1ea46-111">描述如何使用 <xref:System.Data.Linq.DataContext> 物件做為連接資料庫的管道。</span><span class="sxs-lookup"><span data-stu-id="1ea46-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="1ea46-112">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="1ea46-112">Querying the Database</span></span>](querying-the-database.md)  
 <span data-ttu-id="1ea46-113">描述如何在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中執行查詢，以及提供許多範例。</span><span class="sxs-lookup"><span data-stu-id="1ea46-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="1ea46-114">變更資料和提交</span><span class="sxs-lookup"><span data-stu-id="1ea46-114">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)  
 <span data-ttu-id="1ea46-115">描述如何變更資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="1ea46-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="1ea46-116">調試支援</span><span class="sxs-lookup"><span data-stu-id="1ea46-116">Debugging Support</span></span>](debugging-support.md)  
 <span data-ttu-id="1ea46-117">描述可用來偵錯 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案的支援。</span><span class="sxs-lookup"><span data-stu-id="1ea46-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="1ea46-118">背景資訊</span><span class="sxs-lookup"><span data-stu-id="1ea46-118">Background Information</span></span>](background-information.md)  
 <span data-ttu-id="1ea46-119">包括更進階使用者適用的額外項目，例如並行存取衝突解決、建立新資料庫等。</span><span class="sxs-lookup"><span data-stu-id="1ea46-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1ea46-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="1ea46-120">Related Sections</span></span>  
 [<span data-ttu-id="1ea46-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1ea46-121">LINQ to SQL</span></span>](index.md)  
 <span data-ttu-id="1ea46-122">提供說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術以及示範功能的主題連結。</span><span class="sxs-lookup"><span data-stu-id="1ea46-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="1ea46-123">預存程序</span><span class="sxs-lookup"><span data-stu-id="1ea46-123">Stored Procedures</span></span>](stored-procedures.md)  
 <span data-ttu-id="1ea46-124">包括說明如何使用預存程序 (Stored Procedure) 的主題連結。</span><span class="sxs-lookup"><span data-stu-id="1ea46-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="1ea46-125">LINQ 簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="1ea46-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="1ea46-126">提供資源，説明您開始瞭解使用 C# 的 LINQ 到 SQL。</span><span class="sxs-lookup"><span data-stu-id="1ea46-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="1ea46-127">LINQ 簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ea46-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="1ea46-128">提供資源，説明您開始瞭解使用視覺化基礎的 LINQ 到 SQL。</span><span class="sxs-lookup"><span data-stu-id="1ea46-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
