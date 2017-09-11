---
title: "LINQ to ADO.NET (入口網站頁面) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: df23be4b87860afcde03328d0fe47e305860f5f7
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="33cae-102">LINQ to ADO.NET (入口網站頁面)</span><span class="sxs-lookup"><span data-stu-id="33cae-102">LINQ to ADO.NET (Portal Page)</span></span>
[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]<span data-ttu-id="33cae-103">可讓您查詢中任何可列舉物件上方[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]使用[!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="33cae-103"> enables you to query over any enumerable object in [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] by using the [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] programming model.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33cae-104">[!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)]文件位於.NET Framework SDK 的 ADO.NET 區段︰ [LINQ 和 ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)。</span><span class="sxs-lookup"><span data-stu-id="33cae-104">The [!INCLUDE[linq_adonet](../../../../csharp/programming-guide/concepts/linq/includes/linq_adonet_md.md)] documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).</span></span>  
  
 <span data-ttu-id="33cae-105">有三種不同的 ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] 技術：[!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]、[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] 和 [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33cae-105">There are three separate ADO.NET [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] technologies: [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)], [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], and [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)].</span></span> [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]<span data-ttu-id="33cae-106">提供更豐富且最佳化查詢<xref:System.Data.DataSet>，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]可讓您直接查詢[!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)]資料庫結構描述，以及[!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]可讓您查詢[!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]。</xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="33cae-106"> provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] enables you to directly query [!INCLUDE[ssNoVersion](../../../../csharp/programming-guide/concepts/linq/includes/ssnoversion_md.md)] database schemas, and [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)] allows you to query an [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)].</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="33cae-107">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="33cae-107">LINQ to DataSet</span></span>  
 <span data-ttu-id="33cae-108"><xref:System.Data.DataSet>是最廣泛使用的元件中的其中一個[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]，為索引鍵之中斷連接程式設計模型的項目和[!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]為建置基礎。</xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="33cae-108">The <xref:System.Data.DataSet> is one of the most widely used components in [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)], and is a key element of the disconnected programming model that [!INCLUDE[vstecado](../../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)] is built on.</span></span> <span data-ttu-id="33cae-109">這個優點，不過，儘管<xref:System.Data.DataSet>具有有限的查詢功能。</xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="33cae-109">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 [!INCLUDE[linq_dataset](../../../../csharp/programming-guide/concepts/linq/includes/linq_dataset_md.md)]<span data-ttu-id="33cae-110">可讓您建置更豐富的查詢功能<xref:System.Data.DataSet>使用相同的查詢功能可用於許多其他資料來源。</xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="33cae-110"> enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="33cae-111">如需詳細資訊，請參閱[LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)。</span><span class="sxs-lookup"><span data-stu-id="33cae-111">For more information, see [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="33cae-112">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="33cae-112">LINQ to SQL</span></span>  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]<span data-ttu-id="33cae-113"> 提供的執行階段基礎結構可以將關聯式資料當成物件來管理。</span><span class="sxs-lookup"><span data-stu-id="33cae-113"> provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="33cae-114">在[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]，關聯式資料庫的資料模型會對應至以開發人員的程式語言表示的物件模型。</span><span class="sxs-lookup"><span data-stu-id="33cae-114">In [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="33cae-115">當您執行應用程式，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]物件模型中的 language-integrated query 轉譯成 SQL 並將它們傳送到資料庫中執行。</span><span class="sxs-lookup"><span data-stu-id="33cae-115">When you execute the application, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="33cae-116">當資料庫傳回結果，[!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]轉譯回您可以管理的物件。</span><span class="sxs-lookup"><span data-stu-id="33cae-116">When the database returns the results, [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../csharp/includes/vbtecdlinq_md.md)]<span data-ttu-id="33cae-117">物件模型中包含預存程序和使用者定義函式，在資料庫中，以及繼承的支援。</span><span class="sxs-lookup"><span data-stu-id="33cae-117"> includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="33cae-118">如需詳細資訊，請參閱[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)。</span><span class="sxs-lookup"><span data-stu-id="33cae-118">For more information, see [LINQ to SQL](https://msdn.microsoft.com/library/bb386976).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="33cae-119">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="33cae-119">LINQ to Entities</span></span>  
 <span data-ttu-id="33cae-120">透過 [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)]，關聯式資料會公開為 .NET 環境內的物件。</span><span class="sxs-lookup"><span data-stu-id="33cae-120">Through the [!INCLUDE[adonet_edm](../../../../csharp/programming-guide/concepts/linq/includes/adonet_edm_md.md)], relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="33cae-121">如此一來，物件層就成為理想的 [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] 支援目標，讓程式開發人員可以根據用於建置商務邏輯的語言，針對資料庫編寫查詢。</span><span class="sxs-lookup"><span data-stu-id="33cae-121">This makes the object layer an ideal target for [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="33cae-122">這項功能稱為 [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="33cae-122">This capability is known as [!INCLUDE[linq_entities](../../../../csharp/programming-guide/concepts/linq/includes/linq_entities_md.md)].</span></span> <span data-ttu-id="33cae-123">請參閱[LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="33cae-123">See [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33cae-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33cae-124">See Also</span></span>  
 <span data-ttu-id="33cae-125">[LINQ 和 ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec) </span><span class="sxs-lookup"><span data-stu-id="33cae-125">[LINQ and ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec) </span></span>  
<span data-ttu-id="33cae-126"> [語言整合查詢 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="33cae-126"> [Language-Integrated Query (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)</span></span>
