---
title: 查詢資料集 (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: bb64abcffdbbcd46dfb11b2564619c565e461436
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634777"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="bcd8e-102">查詢資料集 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="bcd8e-102">Querying DataSets (LINQ to DataSet)</span></span>
<span data-ttu-id="bcd8e-103">當 <xref:System.Data.DataSet> 物件已經填入 (Populate) 資料之後，您就可以開始查詢它。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="bcd8e-104">使用 LINQ to DataSet 來編寫查詢，類似于針對其他啟用 LINQ 的資料來源使用語言整合式查詢（LINQ）。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="bcd8e-105">不過，請記住，當您在 <xref:System.Data.DataSet> 物件上使用 LINQ 查詢時，您正在查詢 <xref:System.Data.DataRow> 物件的列舉，而不是自訂類型的列舉。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="bcd8e-106">這表示您可以在 LINQ 查詢中使用 <xref:System.Data.DataRow> 類別的任何成員。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="bcd8e-107">這可讓您建立豐富複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="bcd8e-108">如同 LINQ 的其他實現，您可以使用兩種不同的形式來建立 LINQ to DataSet 查詢：查詢運算式語法和以方法為基礎的查詢語法。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="bcd8e-109">您可以使用查詢運算式語法或以方法為基礎的查詢語法，針對 <xref:System.Data.DataSet> 中的單一資料表、針對 <xref:System.Data.DataSet> 中的多個資料表，或針對具型別 <xref:System.Data.DataSet> 中的資料表執行查詢。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bcd8e-110">本章節內容</span><span class="sxs-lookup"><span data-stu-id="bcd8e-110">In This Section</span></span>  
 [<span data-ttu-id="bcd8e-111">單一資料表查詢</span><span class="sxs-lookup"><span data-stu-id="bcd8e-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="bcd8e-112">說明如何執行單一資料表查詢。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="bcd8e-113">跨資料表查詢</span><span class="sxs-lookup"><span data-stu-id="bcd8e-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="bcd8e-114">說明如何執行跨資料表查詢。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="bcd8e-115">查詢具類型資料集</span><span class="sxs-lookup"><span data-stu-id="bcd8e-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="bcd8e-116">說明如何查詢具型別 <xref:System.Data.DataSet> 物件。</span><span class="sxs-lookup"><span data-stu-id="bcd8e-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcd8e-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="bcd8e-117">See also</span></span>

- [<span data-ttu-id="bcd8e-118">LINQ to DataSet 範例</span><span class="sxs-lookup"><span data-stu-id="bcd8e-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="bcd8e-119">將資料載入至資料集</span><span class="sxs-lookup"><span data-stu-id="bcd8e-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
