---
title: 如何：在 Visual Basic 中於相同目錄內建立檔案複本
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af592e16bb1f7f0bbb188b2ea39394ec1074d302
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="a62f7-102">如何：在 Visual Basic 中於相同目錄內建立檔案複本</span><span class="sxs-lookup"><span data-stu-id="a62f7-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="a62f7-103">使用 `My.Computer.FileSystem.CopyFile` 方法來複製檔案。</span><span class="sxs-lookup"><span data-stu-id="a62f7-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="a62f7-104">這些參數可讓您覆寫現有檔案、重新命名檔案、顯示作業進度，並讓使用者取消作業。</span><span class="sxs-lookup"><span data-stu-id="a62f7-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="a62f7-105">在相同資料夾中建立檔案複本</span><span class="sxs-lookup"><span data-stu-id="a62f7-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="a62f7-106">使用 `CopyFile` 方法，並提供目標檔案和位置。</span><span class="sxs-lookup"><span data-stu-id="a62f7-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="a62f7-107">下列範例會建立稱為 `test2.txt` 的 `test.txt` 複本。</span><span class="sxs-lookup"><span data-stu-id="a62f7-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="a62f7-108">在相同資料夾中建立檔案複本，以覆寫現有檔案</span><span class="sxs-lookup"><span data-stu-id="a62f7-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="a62f7-109">使用 `CopyFile` 方法，並提供目標檔案和位置，以及將 `overwrite` 設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="a62f7-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="a62f7-110">下列範例會建立稱為 `test2.txt` 的 `test.txt` 複本，並以該名稱覆寫任何現有檔案。</span><span class="sxs-lookup"><span data-stu-id="a62f7-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="a62f7-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="a62f7-111">Robust Programming</span></span>  
 <span data-ttu-id="a62f7-112">下列條件可能會造成擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="a62f7-112">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="a62f7-113">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="a62f7-114">系統無法擷取絕對路徑 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="a62f7-115">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="a62f7-116">來源檔案無效或不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="a62f7-117">合併的路徑指向現有目錄 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a62f7-118">目的地檔案存在且 `overwrite` 設定為 `False` (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a62f7-119">使用者沒有足夠權限以存取檔案 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a62f7-120">正在使用目標資枓夾中同名的檔案 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a62f7-121">路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="a62f7-122">`ShowUI` 設定為 `True`、`onUserCancel` 設定為 `ThrowException`，而且使用者已取消作業 (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="a62f7-123">`ShowUI` 設定為 `True`、`onUserCancel` 設定為 `ThrowException`，而且發生未指定的 I/O 錯誤 (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="a62f7-124">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="a62f7-125">使用者沒有必要的權限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="a62f7-126">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="a62f7-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62f7-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a62f7-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="a62f7-128">如何：將具有特定模式的檔案複製到目錄</span><span class="sxs-lookup"><span data-stu-id="a62f7-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="a62f7-129">如何：於不同目錄內建立檔案複本</span><span class="sxs-lookup"><span data-stu-id="a62f7-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="a62f7-130">如何：將目錄複製到另一個目錄</span><span class="sxs-lookup"><span data-stu-id="a62f7-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="a62f7-131">如何：重新命名檔案</span><span class="sxs-lookup"><span data-stu-id="a62f7-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
