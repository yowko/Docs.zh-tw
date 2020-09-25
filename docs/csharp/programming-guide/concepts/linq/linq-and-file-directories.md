---
title: 'LINQ 和檔案目錄 (c # ) '
description: '這些適用于檔案系統作業的 c # LINQ 資源不會用來變更檔案或資料夾的內容。'
ms.date: 07/20/2015
ms.assetid: b66c55e4-0f72-44e5-b086-519f9962335c
ms.openlocfilehash: d8ef8ac8a8ff25f0bbac417c07e39f516eee27f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170476"
---
# <a name="linq-and-file-directories-c"></a><span data-ttu-id="e1476-103">LINQ 和檔案目錄 (c # ) </span><span class="sxs-lookup"><span data-stu-id="e1476-103">LINQ and file directories (C#)</span></span>

<span data-ttu-id="e1476-104">許多檔案系統作業基本上都是查詢，因此非常適合 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="e1476-104">Many file system operations are essentially queries and are therefore well suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="e1476-105">此區段中的查詢是非破壞性的。</span><span class="sxs-lookup"><span data-stu-id="e1476-105">The queries in this section are non-destructive.</span></span> <span data-ttu-id="e1476-106">這些查詢不會用來變更原始檔案或資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="e1476-106">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="e1476-107">這是依照查詢不應該造成任何副作用的規則。</span><span class="sxs-lookup"><span data-stu-id="e1476-107">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="e1476-108">一般而言，任何修改來源資料的程式碼 (包括執行 create/update/delete 運算子的查詢)，都應該與單純查詢資料的程式碼分開。</span><span class="sxs-lookup"><span data-stu-id="e1476-108">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="e1476-109">本節包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="e1476-109">This section contains the following topics:</span></span>  
  
 <span data-ttu-id="e1476-110">[如何查詢具有指定屬性或名稱的檔案 (c # ) ](./how-to-query-for-files-with-a-specified-attribute-or-name.md)</span><span class="sxs-lookup"><span data-stu-id="e1476-110">[How to query for files with a specified attribute or name (C#)](./how-to-query-for-files-with-a-specified-attribute-or-name.md)</span></span>\
 <span data-ttu-id="e1476-111">示範如何檢查檔案之 <xref:System.IO.FileInfo> 物件的一或多個屬性來搜尋檔案。</span><span class="sxs-lookup"><span data-stu-id="e1476-111">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 <span data-ttu-id="e1476-112">[如何依擴充功能將檔案分組 (LINQ)  (c # ) ](./how-to-group-files-by-extension-linq.md)</span><span class="sxs-lookup"><span data-stu-id="e1476-112">[How to group files by extension (LINQ) (C#)](./how-to-group-files-by-extension-linq.md)</span></span>\
 <span data-ttu-id="e1476-113">示範如何依據檔案的副檔名來傳回 <xref:System.IO.FileInfo> 物件的群組。</span><span class="sxs-lookup"><span data-stu-id="e1476-113">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 <span data-ttu-id="e1476-114">[如何查詢一組資料夾中的總位元組數 (LINQ)  (c # ) ](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)</span><span class="sxs-lookup"><span data-stu-id="e1476-114">[How to query for the total number of bytes in a set of folders (LINQ) (C#)](./how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq.md)</span></span>\
 <span data-ttu-id="e1476-115">示範如何傳回指定之樹狀目錄中所有檔案的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="e1476-115">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="e1476-116">[如何比較兩個資料夾的內容 (LINQ)  (c # ) ](./how-to-compare-the-contents-of-two-folders-linq.md)s</span><span class="sxs-lookup"><span data-stu-id="e1476-116">[How to compare the contents of two folders (LINQ) (C#)](./how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="e1476-117">示範如何傳回同時出現在兩個指定資料夾中的所有檔案，以及只出現在其中一個資料夾中的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="e1476-117">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 <span data-ttu-id="e1476-118">[如何查詢目錄樹狀結構中的最大檔案 (LINQ)  (c # ) ](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)</span><span class="sxs-lookup"><span data-stu-id="e1476-118">[How to query for the largest file or files in a directory tree (LINQ) (C#)](./how-to-query-for-the-largest-file-or-files-in-a-directory-tree-linq.md)</span></span>\
 <span data-ttu-id="e1476-119">示範如何傳回樹狀目錄中的最大檔案或最小檔案，或是指定數目的檔案。</span><span class="sxs-lookup"><span data-stu-id="e1476-119">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 <span data-ttu-id="e1476-120">[如何查詢目錄樹狀結構中的重複檔案 (LINQ)  (c # ) ](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)</span><span class="sxs-lookup"><span data-stu-id="e1476-120">[How to query for duplicate files in a directory tree (LINQ) (C#)](./how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)</span></span>\
 <span data-ttu-id="e1476-121">示範如何將出現在指定樹狀目錄中多個位置的所有檔案名稱群組在一起。</span><span class="sxs-lookup"><span data-stu-id="e1476-121">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="e1476-122">同時示範如何根據自訂比較子，來執行更複雜的比較。</span><span class="sxs-lookup"><span data-stu-id="e1476-122">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 <span data-ttu-id="e1476-123">[如何查詢資料夾中的檔案內容 (LINQ)  (c # ) ](./how-to-query-the-contents-of-files-in-a-folder-lin.md)</span><span class="sxs-lookup"><span data-stu-id="e1476-123">[How to query the contents of files in a folder (LINQ) (C#)](./how-to-query-the-contents-of-files-in-a-folder-lin.md)</span></span>\
 <span data-ttu-id="e1476-124">示範如何逐一查看樹狀目錄中的資料夾、開啟每個檔案，並查詢檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="e1476-124">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="e1476-125">註解</span><span class="sxs-lookup"><span data-stu-id="e1476-125">Comments</span></span>  

 <span data-ttu-id="e1476-126">要建立能夠精確代表檔案系統內容，同時又能順利處理例外狀況的資料來源，其實是件複雜的工作。</span><span class="sxs-lookup"><span data-stu-id="e1476-126">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="e1476-127">本節中的範例會建立 <xref:System.IO.FileInfo> 物件的快照集合，以代表所指定根資料夾和其所有子資料夾下的所有檔案。</span><span class="sxs-lookup"><span data-stu-id="e1476-127">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="e1476-128">從您開始到結束執行查詢的這段期間，每個 <xref:System.IO.FileInfo> 的實際狀態都可能會變更。</span><span class="sxs-lookup"><span data-stu-id="e1476-128">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="e1476-129">例如，您可以建立 <xref:System.IO.FileInfo> 物件的清單來用作資料來源。</span><span class="sxs-lookup"><span data-stu-id="e1476-129">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="e1476-130">如果您嘗試在查詢中存取 `Length` 屬性，<xref:System.IO.FileInfo> 物件會嘗試存取檔案系統以更新 `Length` 的值。</span><span class="sxs-lookup"><span data-stu-id="e1476-130">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="e1476-131">如果檔案不再存在，即使您未直接查詢檔案系統，也會在查詢中收到 <xref:System.IO.FileNotFoundException>。</span><span class="sxs-lookup"><span data-stu-id="e1476-131">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="e1476-132">本節中的某些查詢會另外使用一個方法，來解決某些情況下的特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e1476-132">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="e1476-133">另一個選項是使用 <xref:System.IO.FileSystemWatcher> 持續動態更新資料來源。</span><span class="sxs-lookup"><span data-stu-id="e1476-133">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1476-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1476-134">See also</span></span>

- [<span data-ttu-id="e1476-135">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="e1476-135">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
