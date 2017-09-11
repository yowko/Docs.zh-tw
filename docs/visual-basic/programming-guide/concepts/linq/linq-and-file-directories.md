---
title: "LINQ 和檔案目錄 (Visual Basic) |Microsoft 文件"
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
ms.assetid: 159fd5c3-3926-4071-ae78-d8e423287eb7
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
ms.openlocfilehash: b9e814c9e9f8519522f288657d6940b07a0b3094
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-and-file-directories-visual-basic"></a><span data-ttu-id="ce991-102">LINQ 和檔案目錄 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce991-102">LINQ and File Directories (Visual Basic)</span></span>
<span data-ttu-id="ce991-103">許多檔案系統作業基本上是查詢，因此適合的 LINQ 方法。</span><span class="sxs-lookup"><span data-stu-id="ce991-103">Many file system operations are essentially queries and are therefore well-suited to the LINQ approach.</span></span>  
  
 <span data-ttu-id="ce991-104">請注意，本節中的查詢非破壞性。</span><span class="sxs-lookup"><span data-stu-id="ce991-104">Note that the queries in this section are non-destructive.</span></span> <span data-ttu-id="ce991-105">它們不會用來變更原始的檔案或資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="ce991-105">They are not used to change the contents of the original files or folders.</span></span> <span data-ttu-id="ce991-106">這會遵循規則，查詢應該不會造成任何副作用。</span><span class="sxs-lookup"><span data-stu-id="ce991-106">This follows the rule that queries should not cause any side-effects.</span></span> <span data-ttu-id="ce991-107">一般情況下，修改來源資料的任何程式碼 （包括執行的查詢建立 / 更新 / 刪除運算子） 應該是分開的程式碼，只會查詢的資料。</span><span class="sxs-lookup"><span data-stu-id="ce991-107">In general, any code (including queries that perform create / update / delete operators) that modifies source data should be kept separate from the code that just queries the data.</span></span>  
  
 <span data-ttu-id="ce991-108">本節包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="ce991-108">This section contains the following topics:</span></span>  
  
 [<span data-ttu-id="ce991-109">如何︰ 查詢具有指定之的屬性或名稱 (Visual Basic) 的檔案</span><span class="sxs-lookup"><span data-stu-id="ce991-109">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 <span data-ttu-id="ce991-110">示範如何藉由檢查的一個或多個屬性搜尋的檔案其<xref:System.IO.FileInfo>物件。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="ce991-110">Shows how to search for files by examining one or more properties of its <xref:System.IO.FileInfo> object.</span></span>  
  
 [<span data-ttu-id="ce991-111">如何︰ 依副檔名 (LINQ) (Visual Basic) 的檔案群組</span><span class="sxs-lookup"><span data-stu-id="ce991-111">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)  
 <span data-ttu-id="ce991-112">示範如何傳回群組<xref:System.IO.FileInfo>物件會根據其副檔名。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="ce991-112">Shows how to return groups of <xref:System.IO.FileInfo> object based on their file name extension.</span></span>  
  
 [<span data-ttu-id="ce991-113">如何︰ 查詢一組資料夾 (LINQ) (Visual Basic) 中的位元組總數</span><span class="sxs-lookup"><span data-stu-id="ce991-113">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders.md)  
 <span data-ttu-id="ce991-114">示範如何傳回指定的目錄樹狀結構中的所有檔案的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="ce991-114">Shows how to return the total number of bytes in all the files in a specified directory tree.</span></span>  
  
 <span data-ttu-id="ce991-115">[如何︰ 比較兩個資料夾內容 (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span><span class="sxs-lookup"><span data-stu-id="ce991-115">[How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-compare-the-contents-of-two-folders-linq.md)s</span></span>  
 <span data-ttu-id="ce991-116">示範如何傳回有兩個指定的資料夾中的所有檔案以及所有檔案，但未在另一個資料夾中。</span><span class="sxs-lookup"><span data-stu-id="ce991-116">Shows how to return all the files that are present in two specified folders, and also all the files that are present in one folder but not the other.</span></span>  
  
 [<span data-ttu-id="ce991-117">如何︰ 查詢的最大檔案或目錄樹狀結構 (LINQ) (Visual Basic) 中的檔案</span><span class="sxs-lookup"><span data-stu-id="ce991-117">How to: Query for the Largest File or Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-the-largest-file-or-files-in-a-directory-tree.md)  
 <span data-ttu-id="ce991-118">示範如何在目錄樹狀結構中傳回的最大或最小的檔案或指定的檔案數目。</span><span class="sxs-lookup"><span data-stu-id="ce991-118">Shows how to return the largest or smallest file, or a specified number of files, in a directory tree.</span></span>  
  
 [<span data-ttu-id="ce991-119">如何︰ 查詢目錄樹狀結構 (LINQ) (Visual Basic) 中的重複檔案</span><span class="sxs-lookup"><span data-stu-id="ce991-119">How to: Query for Duplicate Files in a Directory Tree (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-duplicate-files-in-a-directory-tree-linq.md)  
 <span data-ttu-id="ce991-120">顯示如何將所有出現在指定的目錄樹狀結構中的多個位置的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="ce991-120">Shows how to group for all file names that occur in more than one location in a specified directory tree.</span></span> <span data-ttu-id="ce991-121">也說明如何執行更複雜的比較為基礎的自訂比較子。</span><span class="sxs-lookup"><span data-stu-id="ce991-121">Also shows how to perform more complex comparisons based on a custom comparer.</span></span>  
  
 [<span data-ttu-id="ce991-122">如何︰ 查詢資料夾 (LINQ) (Visual Basic) 中的檔案的內容</span><span class="sxs-lookup"><span data-stu-id="ce991-122">How to: Query the Contents of Files in a Folder (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-the-contents-of-files-in-a-folder-linq.md)  
 <span data-ttu-id="ce991-123">示範如何逐一查看樹狀結構中的資料夾、 開啟每個檔案，並查詢檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="ce991-123">Shows how to iterate through folders in a tree, open each file, and query the file's contents.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="ce991-124">註解</span><span class="sxs-lookup"><span data-stu-id="ce991-124">Comments</span></span>  
 <span data-ttu-id="ce991-125">建立資料來源正確代表檔案系統的內容，並適當地處理例外狀況是一些複雜性。</span><span class="sxs-lookup"><span data-stu-id="ce991-125">There is some complexity involved in creating a data source that accurately represents the contents of the file system and handles exceptions gracefully.</span></span> <span data-ttu-id="ce991-126">本章節中的範例建立的快照集集合<xref:System.IO.FileInfo>物件，表示指定的根資料夾下的所有檔案和所有子資料夾。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="ce991-126">The examples in this section create a snapshot collection of <xref:System.IO.FileInfo> objects that represents all the files under a specified root folder and all its subfolders.</span></span> <span data-ttu-id="ce991-127">每個的實際狀態<xref:System.IO.FileInfo>中開始和結束執行查詢之間的時間可能會變更。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="ce991-127">The actual state of each <xref:System.IO.FileInfo> may change in the time between when you begin and end executing a query.</span></span> <span data-ttu-id="ce991-128">例如，您可以建立一份<xref:System.IO.FileInfo>物件做為資料來源使用。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="ce991-128">For example, you can create a list of <xref:System.IO.FileInfo> objects to use as a data source.</span></span> <span data-ttu-id="ce991-129">如果您嘗試存取`Length`屬性在查詢中，<xref:System.IO.FileInfo>物件將會嘗試存取檔案系統來更新值`Length`。</xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="ce991-129">If you try to access the `Length` property in a query, the <xref:System.IO.FileInfo> object will try to access the file system to update the value of `Length`.</span></span> <span data-ttu-id="ce991-130">如果檔案不存在，就會<xref:System.IO.FileNotFoundException>在查詢中，即使您不在檔案系統直接查詢。</xref:System.IO.FileNotFoundException></span><span class="sxs-lookup"><span data-stu-id="ce991-130">If the file no longer exists, you will get a <xref:System.IO.FileNotFoundException> in your query, even though you are not querying the file system directly.</span></span> <span data-ttu-id="ce991-131">本章節中的某些查詢會使用不同的方法使用這些特定的例外狀況，在某些情況下。</span><span class="sxs-lookup"><span data-stu-id="ce991-131">Some queries in this section use a separate method that consumes these particular exceptions in certain cases.</span></span> <span data-ttu-id="ce991-132">另一個選擇是讓您使用<xref:System.IO.FileSystemWatcher>.</xref:System.IO.FileSystemWatcher>動態更新的資料來源</span><span class="sxs-lookup"><span data-stu-id="ce991-132">Another option is to keep your data source updated dynamically by using the <xref:System.IO.FileSystemWatcher>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce991-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce991-133">See Also</span></span>  
 [<span data-ttu-id="ce991-134">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce991-134">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
