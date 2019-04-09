---
title: 作法：在 Visual Basic 中刪除檔案
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 288c54fa854d753e9b8030463968137b32353b4e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58828559"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="2d16a-102">作法：在 Visual Basic 中刪除檔案</span><span class="sxs-lookup"><span data-stu-id="2d16a-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="2d16a-103">`My.Computer.FileSystem` 物件的 `DeleteFile` 方法可讓您刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="2d16a-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="2d16a-104">提供的選項包括︰是否要將已刪除的檔案傳送至 [資源回收筒]、是否要求使用者確認應該刪除檔案，以及使用者取消該作業時該怎麼辦。</span><span class="sxs-lookup"><span data-stu-id="2d16a-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="2d16a-105">刪除文字檔</span><span class="sxs-lookup"><span data-stu-id="2d16a-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="2d16a-106">使用 `DeleteFile` 方法來刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="2d16a-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="2d16a-107">下列程式碼示範如何刪除名為 `test.txt` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="2d16a-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="2d16a-108">刪除文字檔並要求使用者確認應該刪除檔案</span><span class="sxs-lookup"><span data-stu-id="2d16a-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="2d16a-109">使用 `DeleteFile` 方法來刪除檔案，並將 `showUI` 設定為 `AllDialogs`。</span><span class="sxs-lookup"><span data-stu-id="2d16a-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="2d16a-110">下列程式碼示範如何刪除名為 `test.txt` 的檔案，並讓使用者確認應該刪除檔案。</span><span class="sxs-lookup"><span data-stu-id="2d16a-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="2d16a-111">刪除文字檔並將它傳送至資源回收筒</span><span class="sxs-lookup"><span data-stu-id="2d16a-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="2d16a-112">使用 `DeleteFile` 方法來刪除檔案，並指定 `recycle` 參數的 `SendToRecycleBin`。</span><span class="sxs-lookup"><span data-stu-id="2d16a-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="2d16a-113">下列程式碼示範如何刪除名為 `test.txt` 的檔案，並將它傳送至 [資源回收筒]。</span><span class="sxs-lookup"><span data-stu-id="2d16a-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2d16a-114">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="2d16a-114">Robust Programming</span></span>  
 <span data-ttu-id="2d16a-115">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="2d16a-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2d16a-116">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="2d16a-117">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="2d16a-118">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="2d16a-119">路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="2d16a-120">檔案正在使用中 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2d16a-121">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="2d16a-122">檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="2d16a-123">使用者無權刪除檔案，或檔案為唯讀 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="2d16a-124">發生使用者權限不足的部分信任狀況 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="2d16a-125">使用者已取消作業，而且 `onUserCancel` 設定為 `ThrowException` (<xref:System.OperationCanceledException>)。</span><span class="sxs-lookup"><span data-stu-id="2d16a-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d16a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d16a-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="2d16a-127">如何：取得目錄的檔案集合</span><span class="sxs-lookup"><span data-stu-id="2d16a-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
