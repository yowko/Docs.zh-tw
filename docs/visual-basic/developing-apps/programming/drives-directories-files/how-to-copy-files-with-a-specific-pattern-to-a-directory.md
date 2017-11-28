---
title: "如何：在 Visual Basic 中將具有特定模式的檔案複製到目錄"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ead158a95d7f3ef4d0cd650b3b1a1db7042ccb29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a><span data-ttu-id="6f9ba-102">如何：在 Visual Basic 中將具有特定模式的檔案複製到目錄</span><span class="sxs-lookup"><span data-stu-id="6f9ba-102">How to: Copy Files with a Specific Pattern to a Directory in Visual Basic</span></span>
<span data-ttu-id="6f9ba-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> 方法會傳回代表檔案路徑名稱的唯讀字串集合。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="6f9ba-104">您可以使用 `wildCards` 參數指定特定模式。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span>  
  
 <span data-ttu-id="6f9ba-105">如果找不到相符的檔案，則會傳回空集合。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-105">An empty collection is returned if no matching files are found.</span></span>  
  
 <span data-ttu-id="6f9ba-106">您可以使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> 方法，將檔案複製至目錄。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-106">You can use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> method to copy the files to a directory.</span></span>  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a><span data-ttu-id="6f9ba-107">將具有特定模式的檔案複製至目錄</span><span class="sxs-lookup"><span data-stu-id="6f9ba-107">To copy files with a specific pattern to a directory</span></span>  
  
1.  <span data-ttu-id="6f9ba-108">使用 `GetFiles` 方法來傳回檔案清單。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-108">Use the `GetFiles` method to return the list of files.</span></span> <span data-ttu-id="6f9ba-109">這個範例會傳回所指定目錄中的所有 .rtf 檔案。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-109">This example returns all .rtf files in the specified directory.</span></span>  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  <span data-ttu-id="6f9ba-110">使用 `CopyFile` 方法來複製檔案。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-110">Use the `CopyFile` method to copy the files.</span></span> <span data-ttu-id="6f9ba-111">這個範例會將檔案複製至名稱為 `testdirectory`的目錄中。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-111">This example copies the files to the directory named `testdirectory`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  <span data-ttu-id="6f9ba-112">使用 `For` 陳述式來關閉 `Next` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-112">Close the `For` statement with a `Next` statement.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="6f9ba-113">範例</span><span class="sxs-lookup"><span data-stu-id="6f9ba-113">Example</span></span>  
 <span data-ttu-id="6f9ba-114">下列範例 (以完整形式呈現上述程式碼片段) 會將所指定目錄中的所有 .rtf 檔案複製至名稱為 `testdirectory`的目錄中。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-114">The following example, which presents the above snippets in complete form, copies all .rtf files in the specified directory to the directory named `testdirectory`.</span></span>  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="6f9ba-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="6f9ba-115">.NET Framework Security</span></span>  
 <span data-ttu-id="6f9ba-116">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="6f9ba-116">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6f9ba-117">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-117">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="6f9ba-118">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-118">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="6f9ba-119">目錄不存在 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-119">The directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="6f9ba-120">目錄指向現有檔案 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-120">The directory points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="6f9ba-121">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="6f9ba-122">路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-122">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="6f9ba-123">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-123">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span> <span data-ttu-id="6f9ba-124">使用者缺乏必要的權限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="6f9ba-124">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9ba-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f9ba-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [<span data-ttu-id="6f9ba-126">如何：尋找具有特定模式的子目錄</span><span class="sxs-lookup"><span data-stu-id="6f9ba-126">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [<span data-ttu-id="6f9ba-127">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="6f9ba-127">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [<span data-ttu-id="6f9ba-128">如何：取得目錄的檔案集合</span><span class="sxs-lookup"><span data-stu-id="6f9ba-128">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
