---
title: "如何：在 Visual Basic 中寫入二進位檔案"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], binary access
- WriteAllBytes method [Visual Basic]
- binary files [Visual Basic], writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d8f908822dbcb865f427bee082b8bc4e22ca7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="e18de-102">如何：在 Visual Basic 中寫入二進位檔案</span><span class="sxs-lookup"><span data-stu-id="e18de-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="e18de-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> 方法會將資料寫入二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="e18de-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="e18de-104">如果 `append` 參數為 `True`，它會將資料附加至檔案；若否，則會覆寫檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="e18de-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="e18de-105">如果指定路徑 (不含檔案名稱) 無效，則會擲回 <xref:System.IO.DirectoryNotFoundException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e18de-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="e18de-106">如果此路徑有效，但檔案不存在，則系統會建立檔案。</span><span class="sxs-lookup"><span data-stu-id="e18de-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="e18de-107">若要寫入二進位檔案</span><span class="sxs-lookup"><span data-stu-id="e18de-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="e18de-108">使用 `WriteAllBytes` 方法，同時提供檔案路徑、檔案名稱以及要寫入的位元組。</span><span class="sxs-lookup"><span data-stu-id="e18de-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="e18de-109">這個範例會將資料陣列 `CustomerData` 附加至名為 `CollectedData.dat` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="e18de-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e18de-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="e18de-110">Robust Programming</span></span>  
 <span data-ttu-id="e18de-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e18de-111">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="e18de-112">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元，或者它包含無效的字元。</span><span class="sxs-lookup"><span data-stu-id="e18de-112">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="e18de-113">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="e18de-113">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e18de-114">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="e18de-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e18de-115">`File` 指向不存在的路徑 (<xref:System.IO.FileNotFoundException> 或 <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="e18de-115">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="e18de-116">檔案正由另一個處理序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="e18de-116">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e18de-117">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="e18de-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="e18de-118">路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="e18de-118">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="e18de-119">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="e18de-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e18de-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e18de-120">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>  
 [<span data-ttu-id="e18de-121">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="e18de-121">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
