---
title: HOW TO：在 Visual Basic 中將目錄複製到另一個目錄
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 25919e0256b967f59bd98d20e75d159e018ac954
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594742"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="07e07-102">HOW TO：在 Visual Basic 中將目錄複製到另一個目錄</span><span class="sxs-lookup"><span data-stu-id="07e07-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>
<span data-ttu-id="07e07-103">使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> 方法可將目錄複製到另一個目錄。</span><span class="sxs-lookup"><span data-stu-id="07e07-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="07e07-104">這個方法會複製目錄內容以及目錄本身。</span><span class="sxs-lookup"><span data-stu-id="07e07-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="07e07-105">如果目標目錄不存在，則會予以建立。</span><span class="sxs-lookup"><span data-stu-id="07e07-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="07e07-106">如果目標位置存在同名的目錄且 `overwrite` 設為 `False`，即合併兩個目錄的內容。</span><span class="sxs-lookup"><span data-stu-id="07e07-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="07e07-107">您可以在作業期間指定目錄的新名稱。</span><span class="sxs-lookup"><span data-stu-id="07e07-107">You can specify a new name for the directory during the operation.</span></span>  
  
 <span data-ttu-id="07e07-108">複製目錄內的檔案時，可能會因為特定的檔案而擲回例外狀況，例如合併期間存在檔案，而 `overwrite` 設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="07e07-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="07e07-109">當這類例外狀況被擲回時，它們會合併成單一例外狀況，其 `Data` 屬性保留項目中的檔案或目錄路徑是索引鍵，而特定的例外狀況訊息則包含在對應值中。</span><span class="sxs-lookup"><span data-stu-id="07e07-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>  
  
### <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="07e07-110">將目錄複製到另一個目錄</span><span class="sxs-lookup"><span data-stu-id="07e07-110">To copy a directory to another directory</span></span>  
  
-   <span data-ttu-id="07e07-111">使用 `CopyDirectory` 方法指定來源和目的地目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="07e07-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="07e07-112">下例會將名為 `TestDirectory1` 的目錄複製到 `TestDirectory2`，覆寫現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="07e07-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     <span data-ttu-id="07e07-113">這個程式碼範例也可用為 IntelliSense 程式碼片段。</span><span class="sxs-lookup"><span data-stu-id="07e07-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="07e07-114">在程式碼片段選擇器中，它位於 [檔案系統 - 處理磁碟、資料夾和檔案] 中。</span><span class="sxs-lookup"><span data-stu-id="07e07-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="07e07-115">如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。</span><span class="sxs-lookup"><span data-stu-id="07e07-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="07e07-116">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="07e07-116">Robust Programming</span></span>  
 <span data-ttu-id="07e07-117">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="07e07-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="07e07-118">為目錄指定的新名稱包含冒號 (:) 或斜線 (\ 或 /) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="07e07-119">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="07e07-120">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="07e07-121">`destinationDirectoryName` 為 `Nothing` 或空字串 (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="07e07-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="07e07-122">來源目錄不存在 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="07e07-123">來源目錄不是根目錄 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="07e07-124">合併路徑指向現有的檔案 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="07e07-125">來源路徑和目標路徑相同 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="07e07-126">`ShowUI` 設定為 `UIOption.AllDialogs` 且使用者取消作業，或無法複製目錄中的一或多個檔案 (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="07e07-127">作業是循環的 (<xref:System.InvalidOperationException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>  
  
-   <span data-ttu-id="07e07-128">路徑包含冒號 (:) (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="07e07-129">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="07e07-130">路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="07e07-131">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="07e07-132">目的地檔案存在，但無法存取 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="07e07-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e07-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07e07-133">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="07e07-134">如何：尋找具有特定模式的子目錄</span><span class="sxs-lookup"><span data-stu-id="07e07-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="07e07-135">如何：取得目錄的檔案集合</span><span class="sxs-lookup"><span data-stu-id="07e07-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
