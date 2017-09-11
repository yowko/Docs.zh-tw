---
title: "如何：在 Visual Basic 中重新命名檔案"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files, renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f003cfc7c7880a47515f7328a0503072f3b02cbf
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="f9fd1-102">如何：在 Visual Basic 中重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="f9fd1-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="f9fd1-103">您可以使用 `My.Computer.FileSystem` 物件的 `RenameFile` 方法，藉由提供目前的位置、檔案名稱和新的檔案名稱，來重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="f9fd1-104">這個方法無法用來移動檔案，請使用 `MoveFile` 方法來移動並重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="f9fd1-105">重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="f9fd1-105">To rename a file</span></span>  
  
-   <span data-ttu-id="f9fd1-106">使用 `My.Computer.FileSystem.RenameFile` 方法來重新命名檔案。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="f9fd1-107">此範例會將名為 `Test.txt` 的檔案重新命名為 `SecondTest.txt`。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     <span data-ttu-id="f9fd1-108">[!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f9fd1-108">[!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]</span></span>  
  
 <span data-ttu-id="f9fd1-109">這個程式碼範例也可作為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-109">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f9fd1-110">在程式碼片段選擇器中，該程式碼片段會位於 [檔案系統 - 處理磁碟、資料夾和檔案] 中。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-110">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="f9fd1-111">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-111">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f9fd1-112">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="f9fd1-112">Robust Programming</span></span>  
 <span data-ttu-id="f9fd1-113">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="f9fd1-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f9fd1-114">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-115">`newName` 包含路徑資訊 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-115">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-116">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-117">`newName` 為 `Nothing` 或空字串 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-117">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-118">來源檔案無效或不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-118">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-119">已有 `newName` 中所指定之名稱的檔案或目錄 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-119">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-120">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-120">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-121">路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-121">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-122">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="f9fd1-123">使用者沒有必要的權限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="f9fd1-123">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9fd1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9fd1-124">See Also</span></span>  
 <span data-ttu-id="f9fd1-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A></span><span class="sxs-lookup"><span data-stu-id="f9fd1-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A></span></span>   
 <span data-ttu-id="f9fd1-126">[如何：移動檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md) </span><span class="sxs-lookup"><span data-stu-id="f9fd1-126">[How to: Move a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md) </span></span>  
 <span data-ttu-id="f9fd1-127">[建立、刪除和移動檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="f9fd1-127">[Creating, Deleting, and Moving Files and Directories](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md) </span></span>  
 <span data-ttu-id="f9fd1-128">[如何：在相同目錄內建立檔案複本](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md) </span><span class="sxs-lookup"><span data-stu-id="f9fd1-128">[How to: Create a Copy of a File in the Same Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md) </span></span>  
 [<span data-ttu-id="f9fd1-129">如何：於不同目錄內建立檔案複本</span><span class="sxs-lookup"><span data-stu-id="f9fd1-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)

