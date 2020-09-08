---
title: 功能性轉換的適用性-LINQ to XML
description: 瞭解如何使用功能性轉換。
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: cfba2a32887891cd4b735c76e940ff2400e55bef
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552286"
---
# <a name="applicability-of-functional-transformation-linq-to-xml"></a><span data-ttu-id="b40df-103">功能性轉換 (LINQ to XML) 的適用性</span><span class="sxs-lookup"><span data-stu-id="b40df-103">Applicability of functional transformation (LINQ to XML)</span></span>

<span data-ttu-id="b40df-104">純功能性轉換適用於各種情況。</span><span class="sxs-lookup"><span data-stu-id="b40df-104">Pure functional transformations are applicable in a wide variety of situations.</span></span>

<span data-ttu-id="b40df-105">功能性轉換方法最適合查詢與管理結構化資料；因此，最適合搭配 LINQ 技術使用。</span><span class="sxs-lookup"><span data-stu-id="b40df-105">The functional transformation approach is ideally suited for querying and manipulating structured data; therefore it fits well with LINQ technologies.</span></span> <span data-ttu-id="b40df-106">不過，功能性轉換的適用性比搭配 LINQ 還要廣泛。</span><span class="sxs-lookup"><span data-stu-id="b40df-106">However, functional transformation has a much wider applicability than use with LINQ.</span></span> <span data-ttu-id="b40df-107">主要焦點放在將資料從一個表單轉換到另一個表單的任何處理都可能會被視為功能性轉換的候選。</span><span class="sxs-lookup"><span data-stu-id="b40df-107">Any process where the main focus is on transforming data from one form to another should probably be considered as a candidate for functional transformation.</span></span>

<span data-ttu-id="b40df-108">這個方法適用於許多開始做為候選時可能不會出現的問題。</span><span class="sxs-lookup"><span data-stu-id="b40df-108">This approach is applicable to many problems that might not appear at first glance to be a candidate.</span></span> <span data-ttu-id="b40df-109">搭配 LINQ 使用或與 LINQ 分開使用時，應該針對下列區域考慮功能性轉換：</span><span class="sxs-lookup"><span data-stu-id="b40df-109">Used in conjunction with or separately from LINQ, functional transformation should be considered for the following areas:</span></span>

- <span data-ttu-id="b40df-110">以 XML 為基礎的文件。</span><span class="sxs-lookup"><span data-stu-id="b40df-110">XML-based documents.</span></span> <span data-ttu-id="b40df-111">格式正確的任何 XML 語言資料都可以透過功能性轉換輕鬆管理。</span><span class="sxs-lookup"><span data-stu-id="b40df-111">Well-formed data of any XML dialect can be easily manipulated through functional transformation.</span></span> <span data-ttu-id="b40df-112">如需詳細資訊，請參閱 [XML 的功能性轉換](functional-transformation-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b40df-112">For more information, see [Functional transformation of XML](functional-transformation-xml.md).</span></span>
- <span data-ttu-id="b40df-113">其他結構化檔案格式。</span><span class="sxs-lookup"><span data-stu-id="b40df-113">Other structured file formats.</span></span> <span data-ttu-id="b40df-114">從 Windows.ini 檔案到純文字文件，大部分的檔案都有借用本身進行分析與轉換的特定結構。</span><span class="sxs-lookup"><span data-stu-id="b40df-114">From Windows.ini files to plain text documents, most files have some structure that lends itself to analysis and transformation.</span></span>
- <span data-ttu-id="b40df-115">資料串流通訊協定。</span><span class="sxs-lookup"><span data-stu-id="b40df-115">Data streaming protocols.</span></span> <span data-ttu-id="b40df-116">將資料編碼到通訊協定，或從通訊協定解碼資料通常都可以透過簡單的功能性轉換表示。</span><span class="sxs-lookup"><span data-stu-id="b40df-116">Encoding data into and decoding data from communication protocols can often be represented by a simple functional transform.</span></span>
- <span data-ttu-id="b40df-117">RDBMS 和 OODBMS 資料。</span><span class="sxs-lookup"><span data-stu-id="b40df-117">RDBMS and OODBMS data.</span></span> <span data-ttu-id="b40df-118">關聯式資料庫與物件導向的資料庫 (例如 XML) 都是廣泛使用的結構化資料來源。</span><span class="sxs-lookup"><span data-stu-id="b40df-118">Relational and object-oriented databases, just like XML, are widely-used structured data sources.</span></span>
- <span data-ttu-id="b40df-119">數學、統計與科學解決方案。</span><span class="sxs-lookup"><span data-stu-id="b40df-119">Mathematic, statistic, and science solutions.</span></span> <span data-ttu-id="b40df-120">這些欄位傾向管理大型資料集來協助使用者視覺化、估計或實際解決非一般的問題。</span><span class="sxs-lookup"><span data-stu-id="b40df-120">These fields tend to manipulate large data sets to assist the user in visualizing, estimating, or actually solving non-trivial problems.</span></span>

<span data-ttu-id="b40df-121">如 [重構為純](refactor-pure-functions.md)虛擬函式中所述，使用純虛擬函式是功能程式設計的範例。</span><span class="sxs-lookup"><span data-stu-id="b40df-121">As described in [Refactor into pure functions](refactor-pure-functions.md), using pure functions is an example of functional programming.</span></span> <span data-ttu-id="b40df-122">除了立即的益處之外，使用純虛擬函式會提供從功能性轉換觀點思考的珍貴經驗。</span><span class="sxs-lookup"><span data-stu-id="b40df-122">In additional to their immediate benefits, using pure functions provides valuable experience in thinking about problems from a functional transformation perspective.</span></span> <span data-ttu-id="b40df-123">這個方法對於程式和類別設計也可能產生重大影響。</span><span class="sxs-lookup"><span data-stu-id="b40df-123">This approach can also have major impact on program and class design.</span></span> <span data-ttu-id="b40df-124">尤其是問題如上述般，將本身借用給資料轉換解決方案時，更是如此。</span><span class="sxs-lookup"><span data-stu-id="b40df-124">This is especially true when a problem lends itself to a data transformation solution as described above.</span></span>

<span data-ttu-id="b40df-125">雖然它們不在本教學課程的討論範圍內，但受功能性轉換觀點影響的設計傾向于在處理常式上，將物件視為動作專案，而產生的解決方案通常會實作為一連串的大規模轉換，而不是個別的物件狀態變更。</span><span class="sxs-lookup"><span data-stu-id="b40df-125">Although they're beyond the scope of this tutorial, designs that are influenced by the functional transformation perspective tend to center on processes more than on objects as actors, and the resulting solution tends to be implemented as a series of large-scale transformations, rather than individual object state changes.</span></span>

 <span data-ttu-id="b40df-126">再次提醒，C# 和 Visual Basic 同時支援命令性與功能性方法，因此，最適合您應用程式的設計可能會納入兩者的項目。</span><span class="sxs-lookup"><span data-stu-id="b40df-126">Again, remember that C# and Visual Basic support both imperative and functional approaches, so the best design for your application might incorporate elements of both.</span></span>

## <a name="see-also"></a><span data-ttu-id="b40df-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b40df-127">See also</span></span>

- [<span data-ttu-id="b40df-128">純功能性轉換簡介</span><span class="sxs-lookup"><span data-stu-id="b40df-128">Introduction to pure functional transformations</span></span>](introduction-pure-functional-transformations.md)
- [<span data-ttu-id="b40df-129">XML 的功能性轉換</span><span class="sxs-lookup"><span data-stu-id="b40df-129">Functional transformation of XML</span></span>](functional-transformation-xml.md)
- [<span data-ttu-id="b40df-130">重構為純虛擬函式</span><span class="sxs-lookup"><span data-stu-id="b40df-130">Refactor into pure functions</span></span>](refactor-pure-functions.md)
