---
title: "功能性轉換的適用性 (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
caps.latest.revision: 4
author: BillWagner
ms.author: wiwagn
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b008bdef820b979e2aabd480e08a3bfa5ee5afa2
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="applicability-of-functional-transformation-c"></a><span data-ttu-id="95d41-102">功能性轉換的適用性 (C#)</span><span class="sxs-lookup"><span data-stu-id="95d41-102">Applicability of Functional Transformation (C#)</span></span>
<span data-ttu-id="95d41-103">純功能性轉換適用於各種情況。</span><span class="sxs-lookup"><span data-stu-id="95d41-103">Pure functional transformations are applicable in a wide variety of situations.</span></span>  
  
 <span data-ttu-id="95d41-104">功能性轉換方法最適合查詢與管理結構化資料；因此，最適合搭配 LINQ 技術使用。</span><span class="sxs-lookup"><span data-stu-id="95d41-104">The functional transformation approach is ideally suited for querying and manipulating structured data; therefore it fits well with LINQ technologies.</span></span> <span data-ttu-id="95d41-105">不過，功能性轉換的適用性比搭配 LINQ 還要廣泛。</span><span class="sxs-lookup"><span data-stu-id="95d41-105">However, functional transformation has a much wider applicability than use with LINQ.</span></span> <span data-ttu-id="95d41-106">主要焦點放在將資料從一個表單轉換到另一個表單的任何處理都可能會被視為功能性轉換的候選。</span><span class="sxs-lookup"><span data-stu-id="95d41-106">Any process where the main focus is on transforming data from one form to another should probably be considered as a candidate for functional transformation.</span></span>  
  
 <span data-ttu-id="95d41-107">這個方法適用於許多開始做為候選時可能不會出現的問題。</span><span class="sxs-lookup"><span data-stu-id="95d41-107">This approach is applicable to many problems that might not appear at first glance to be a candidate.</span></span> <span data-ttu-id="95d41-108">搭配 LINQ 使用或與 LINQ 分開使用時，應該針對下列區域考慮功能性轉換：</span><span class="sxs-lookup"><span data-stu-id="95d41-108">Used in conjunction with or separately from LINQ, functional transformation should be considered for the following areas:</span></span>  
  
-   <span data-ttu-id="95d41-109">以 XML 為基礎的文件。</span><span class="sxs-lookup"><span data-stu-id="95d41-109">XML-based documents.</span></span> <span data-ttu-id="95d41-110">格式正確的任何 XML 語言資料都可以透過功能性轉換輕鬆管理。</span><span class="sxs-lookup"><span data-stu-id="95d41-110">Well-formed data of any XML dialect can be easily manipulated through functional transformation.</span></span> <span data-ttu-id="95d41-111">如需詳細資訊，請參閱 [XML 功能性轉換 (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="95d41-111">For more information, see [Functional Transformation of XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md).</span></span>  
  
-   <span data-ttu-id="95d41-112">其他結構化檔案格式。</span><span class="sxs-lookup"><span data-stu-id="95d41-112">Other structured file formats.</span></span> <span data-ttu-id="95d41-113">從 Windows.ini 檔案到純文字文件，大部分的檔案都有借用本身進行分析與轉換的特定結構。</span><span class="sxs-lookup"><span data-stu-id="95d41-113">From Windows.ini files to plain text documents, most files have some structure that lends itself to analysis and transformation.</span></span>  
  
-   <span data-ttu-id="95d41-114">資料串流通訊協定。</span><span class="sxs-lookup"><span data-stu-id="95d41-114">Data streaming protocols.</span></span> <span data-ttu-id="95d41-115">將資料編碼到通訊協定，或從通訊協定解碼資料通常都可以透過簡單的功能性轉換表示。</span><span class="sxs-lookup"><span data-stu-id="95d41-115">Encoding data into and decoding data from communication protocols can often be represented by a simple functional transform.</span></span>  
  
-   <span data-ttu-id="95d41-116">RDBMS 和 OODBMS 資料。</span><span class="sxs-lookup"><span data-stu-id="95d41-116">RDBMS and OODBMS data.</span></span> <span data-ttu-id="95d41-117">關聯式資料庫與物件導向的資料庫 (例如 XML) 都是廣泛使用的結構化資料來源。</span><span class="sxs-lookup"><span data-stu-id="95d41-117">Relational and object-oriented databases, just like XML, are widely-used structured data sources.</span></span>  
  
-   <span data-ttu-id="95d41-118">數學、統計與科學解決方案。</span><span class="sxs-lookup"><span data-stu-id="95d41-118">Mathematic, statistic, and science solutions.</span></span> <span data-ttu-id="95d41-119">這些欄位傾向管理大型資料集來協助使用者視覺化、估計或實際解決非一般的問題。</span><span class="sxs-lookup"><span data-stu-id="95d41-119">These fields tend to manipulate large data sets to assist the user in visualizing, estimating, or actually solving non-trivial problems.</span></span>  
  
 <span data-ttu-id="95d41-120">如同[重構為純虛擬函式 (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md) 中所述，使用純虛擬函式是函式程式設計的範例。</span><span class="sxs-lookup"><span data-stu-id="95d41-120">As described in [Refactoring Into Pure Functions (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md), using pure functions is an example of functional programming.</span></span> <span data-ttu-id="95d41-121">除了立即的益處之外，使用純虛擬函式會提供從功能性轉換觀點思考的珍貴經驗。</span><span class="sxs-lookup"><span data-stu-id="95d41-121">In additional to their immediate benefits, using pure functions provides valuable experience in thinking about problems from a functional transformation perspective.</span></span> <span data-ttu-id="95d41-122">這個方法對於程式和類別設計也可能產生重大影響。</span><span class="sxs-lookup"><span data-stu-id="95d41-122">This approach can also have major impact on program and class design.</span></span> <span data-ttu-id="95d41-123">尤其是問題如上述般，將本身借用給資料轉換解決方案時，更是如此。</span><span class="sxs-lookup"><span data-stu-id="95d41-123">This is especially true when a problem lends itself to a data transformation solution as described above.</span></span>  
  
 <span data-ttu-id="95d41-124">雖然這些超出此教學課程的範圍，但是受到功能性轉換觀點影響的設計傾向於著重程序而非當做行動的物件，而所產生的解決方案容易當做一系列的大規模轉換 (而非個別物件狀態的變更) 實作。</span><span class="sxs-lookup"><span data-stu-id="95d41-124">Although they are beyond the scope of this tutorial, designs that are influenced by the functional transformation perspective tend to center on processes more than on objects as actors, and the resulting solution tends to be implemented as series of large-scale transformations, rather than individual object state changes.</span></span>  
  
 <span data-ttu-id="95d41-125">再次提醒，C# 支援命令性與功能性方法，因此，最適合您應用程式的設計可能會納入兩者的項目。</span><span class="sxs-lookup"><span data-stu-id="95d41-125">Again, remember that C# supports both imperative and functional approaches, so the best design for your application might incorporate elements of both.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d41-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95d41-126">See Also</span></span>  
 <span data-ttu-id="95d41-127">[純功能性轉換簡介 (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span><span class="sxs-lookup"><span data-stu-id="95d41-127">[Introduction to Pure Functional Transformations (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md) </span></span>  
 <span data-ttu-id="95d41-128">[XML 功能性轉換 (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md) </span><span class="sxs-lookup"><span data-stu-id="95d41-128">[Functional Transformation of XML (C#)](../../../../csharp/programming-guide/concepts/linq/functional-transformation-of-xml.md) </span></span>  
 [<span data-ttu-id="95d41-129">重構為純虛擬函式 (C#)</span><span class="sxs-lookup"><span data-stu-id="95d41-129">Refactoring Into Pure Functions (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

