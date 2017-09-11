---
title: "如何：在 Visual Basic 中刪除檔案"
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
- Delete method
- files, deleting
- files, manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
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
ms.openlocfilehash: e4b0b87fd403556777e0ab5a1edd517687360374
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="e4f00-102">如何：在 Visual Basic 中刪除檔案</span><span class="sxs-lookup"><span data-stu-id="e4f00-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="e4f00-103">`My.Computer.FileSystem` 物件的 `DeleteFile` 方法可讓您刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="e4f00-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="e4f00-104">提供的選項包括︰是否要將已刪除的檔案傳送至 [資源回收筒]、是否要求使用者確認應該刪除檔案，以及使用者取消該作業時該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="e4f00-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="e4f00-105">刪除文字檔</span><span class="sxs-lookup"><span data-stu-id="e4f00-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="e4f00-106">使用 `DeleteFile` 方法來刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="e4f00-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="e4f00-107">下列程式碼示範如何刪除名為 `test.txt` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="e4f00-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     <span data-ttu-id="e4f00-108">[!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e4f00-108">[!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]</span></span>  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="e4f00-109">刪除文字檔並要求使用者確認應該刪除檔案</span><span class="sxs-lookup"><span data-stu-id="e4f00-109">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="e4f00-110">使用 `DeleteFile` 方法來刪除檔案，並將 `showUI` 設定為 `AllDialogs`。</span><span class="sxs-lookup"><span data-stu-id="e4f00-110">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="e4f00-111">下列程式碼示範如何刪除名為 `test.txt` 的檔案，並讓使用者確認應該刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="e4f00-111">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     <span data-ttu-id="e4f00-112">[!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e4f00-112">[!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]</span></span>  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="e4f00-113">刪除文字檔並將它傳送至資源回收筒</span><span class="sxs-lookup"><span data-stu-id="e4f00-113">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="e4f00-114">使用 `DeleteFile` 方法來刪除檔案，並指定 `recycle` 參數的 `SendToRecycleBin`。</span><span class="sxs-lookup"><span data-stu-id="e4f00-114">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="e4f00-115">下列程式碼示範如何刪除名為 `test.txt` 的檔案，並將它傳送至 [資源回收筒]。</span><span class="sxs-lookup"><span data-stu-id="e4f00-115">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     <span data-ttu-id="e4f00-116">[!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e4f00-116">[!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e4f00-117">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="e4f00-117">Robust Programming</span></span>  
 <span data-ttu-id="e4f00-118">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e4f00-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e4f00-119">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e4f00-120">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e4f00-121">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="e4f00-122">路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-122">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="e4f00-123">檔案正在使用中 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-123">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e4f00-124">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="e4f00-125">檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-125">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="e4f00-126">使用者無權刪除檔案，或檔案為唯讀 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-126">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="e4f00-127">發生使用者權限不足的部分信任狀況 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-127">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="e4f00-128">使用者已取消作業，而且 `onUserCancel` 設定為 `ThrowException` (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="e4f00-128">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4f00-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4f00-129">See Also</span></span>  
 <span data-ttu-id="e4f00-130"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span><span class="sxs-lookup"><span data-stu-id="e4f00-130"><xref:Microsoft.VisualBasic.FileIO.UICancelOption></span></span>   
 <span data-ttu-id="e4f00-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="e4f00-131"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="e4f00-132"><xref:Microsoft.VisualBasic.FileIO.UIOption></span><span class="sxs-lookup"><span data-stu-id="e4f00-132"><xref:Microsoft.VisualBasic.FileIO.UIOption></span></span>   
 <span data-ttu-id="e4f00-133"><xref:Microsoft.VisualBasic.FileIO.RecycleOption></span><span class="sxs-lookup"><span data-stu-id="e4f00-133"><xref:Microsoft.VisualBasic.FileIO.RecycleOption></span></span>   
 [<span data-ttu-id="e4f00-134">如何：取得目錄的檔案集合</span><span class="sxs-lookup"><span data-stu-id="e4f00-134">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

