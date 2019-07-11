---
title: 程式設計手冊
ms.date: 03/30/2017
ms.assetid: ed1012d4-3ff2-4877-af27-93125c4180ea
ms.openlocfilehash: c63fbedc1cf7484943614c50e7dd7554a2ddea0e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742934"
---
# <a name="programming-guide"></a><span data-ttu-id="861aa-102">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="861aa-102">Programming Guide</span></span>
<span data-ttu-id="861aa-103">本節包含如何建立和使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型 (Object Model) 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="861aa-103">This section contains information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="861aa-104">如果您使用 Visual Studio，您也可以使用物件關聯式設計工具來執行許多相同的工作。</span><span class="sxs-lookup"><span data-stu-id="861aa-104">If you are using Visual Studio, you can also use the Object Relational Designer to perform many of these same tasks.</span></span>  
  
 <span data-ttu-id="861aa-105">您也可以搜尋 Microsoft Docs 特定問題，並可以參與[LINQ 論壇](https://go.microsoft.com/fwlink/?LinkId=76488)，您可以與專家討論更複雜的主題的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="861aa-105">You can also search Microsoft Docs for specific issues, and you can participate in the [LINQ Forum](https://go.microsoft.com/fwlink/?LinkId=76488), where you can discuss more complex topics in detail with experts.</span></span> <span data-ttu-id="861aa-106">最後， [LINQ to SQL： 關聯式資料的.net language-integrated Query](https://go.microsoft.com/fwlink/?LinkId=93205)白皮書詳細說明[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]技術，其中包含 Visual Basic 和 C# 程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="861aa-106">Finally, the [LINQ to SQL: .NET Language-Integrated Query for Relational Data](https://go.microsoft.com/fwlink/?LinkId=93205) white paper details [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology, complete with Visual Basic and C# code examples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="861aa-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="861aa-107">In This Section</span></span>  
 [<span data-ttu-id="861aa-108">建立物件模型</span><span class="sxs-lookup"><span data-stu-id="861aa-108">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 <span data-ttu-id="861aa-109">描述如何產生物件模型。</span><span class="sxs-lookup"><span data-stu-id="861aa-109">Describes how to generate an object model.</span></span>  
  
 [<span data-ttu-id="861aa-110">與資料庫通訊</span><span class="sxs-lookup"><span data-stu-id="861aa-110">Communicating with the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/communicating-with-the-database.md)  
 <span data-ttu-id="861aa-111">描述如何使用 <xref:System.Data.Linq.DataContext> 物件做為連接資料庫的管道。</span><span class="sxs-lookup"><span data-stu-id="861aa-111">Describes how to use a <xref:System.Data.Linq.DataContext> object as a conduit to the database.</span></span>  
  
 [<span data-ttu-id="861aa-112">查詢資料庫</span><span class="sxs-lookup"><span data-stu-id="861aa-112">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 <span data-ttu-id="861aa-113">描述如何在 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中執行查詢，以及提供許多範例。</span><span class="sxs-lookup"><span data-stu-id="861aa-113">Describes how to execute queries in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], and provides many examples.</span></span>  
  
 [<span data-ttu-id="861aa-114">變更和提交資料</span><span class="sxs-lookup"><span data-stu-id="861aa-114">Making and Submitting Data Changes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)  
 <span data-ttu-id="861aa-115">描述如何變更資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="861aa-115">Describes how change data in the database.</span></span>  
  
 [<span data-ttu-id="861aa-116">偵錯支援</span><span class="sxs-lookup"><span data-stu-id="861aa-116">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)  
 <span data-ttu-id="861aa-117">描述可用來偵錯 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 專案的支援。</span><span class="sxs-lookup"><span data-stu-id="861aa-117">Describes the support available for debugging [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projects.</span></span>  
  
 [<span data-ttu-id="861aa-118">背景資訊</span><span class="sxs-lookup"><span data-stu-id="861aa-118">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 <span data-ttu-id="861aa-119">包括更進階使用者適用的額外項目，例如並行存取衝突解決、建立新資料庫等。</span><span class="sxs-lookup"><span data-stu-id="861aa-119">Includes additional items, such as concurrency conflict resolution, creating new databases, and more, for more advanced users.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="861aa-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="861aa-120">Related Sections</span></span>  
 [<span data-ttu-id="861aa-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="861aa-121">LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="861aa-122">提供說明 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 技術以及示範功能的主題連結。</span><span class="sxs-lookup"><span data-stu-id="861aa-122">Provides links to topics that explain the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] technology and demonstrate features.</span></span>  
  
 [<span data-ttu-id="861aa-123">預存程序</span><span class="sxs-lookup"><span data-stu-id="861aa-123">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)  
 <span data-ttu-id="861aa-124">包括說明如何使用預存程序 (Stored Procedure) 的主題連結。</span><span class="sxs-lookup"><span data-stu-id="861aa-124">Includes links to topics that illustrate how to use stored procedures.</span></span>  
  
 [<span data-ttu-id="861aa-125">LINQ 簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="861aa-125">Introduction to LINQ (C#)</span></span>](../../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="861aa-126">提供的資源可協助您開始學習 LINQ，若要使用 SQL C#。</span><span class="sxs-lookup"><span data-stu-id="861aa-126">Provides resources to help you begin to learn about LINQ to SQL using C#.</span></span>

 [<span data-ttu-id="861aa-127">LINQ 簡介 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="861aa-127">Introduction to LINQ (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/concepts/linq/introduction-to-linq.md)  
 <span data-ttu-id="861aa-128">提供可協助您開始了解 LINQ to SQL，使用 Visual Basic 資源。</span><span class="sxs-lookup"><span data-stu-id="861aa-128">Provides resources to help you begin to learn about LINQ to SQL using Visual Basic.</span></span>
