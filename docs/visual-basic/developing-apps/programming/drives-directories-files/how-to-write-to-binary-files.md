---
title: "如何：在 Visual Basic 中寫入二進位檔案"
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
- files, binary access
- WriteAllBytes method
- binary files, writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
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
ms.openlocfilehash: ae6f275dd86a53c6b6251feb08210a775adba0b0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a><span data-ttu-id="4d1f8-102">如何：在 Visual Basic 中寫入二進位檔案</span><span class="sxs-lookup"><span data-stu-id="4d1f8-102">How to: Write to Binary Files in Visual Basic</span></span>
<span data-ttu-id="4d1f8-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> 方法會將資料寫入二進位檔案。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> method writes data to a binary file.</span></span> <span data-ttu-id="4d1f8-104">如果 `append` 參數為 `True`，它會將資料附加至檔案；若否，則會覆寫檔案中的資料。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-104">If the `append` parameter is `True`, it will append the data to the file; otherwise data in the file is overwritten.</span></span>  
  
 <span data-ttu-id="4d1f8-105">如果指定路徑 (不含檔案名稱) 無效，則會擲回 <xref:System.IO.DirectoryNotFoundException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-105">If the specified path excluding the file name is not valid, a <xref:System.IO.DirectoryNotFoundException> exception will be thrown.</span></span> <span data-ttu-id="4d1f8-106">如果此路徑有效，但檔案不存在，則系統會建立檔案。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-106">If the path is valid but the file does not exist, the file will be created.</span></span>  
  
### <a name="to-write-to-a-binary-file"></a><span data-ttu-id="4d1f8-107">若要寫入二進位檔案</span><span class="sxs-lookup"><span data-stu-id="4d1f8-107">To write to a binary file</span></span>  
  
-   <span data-ttu-id="4d1f8-108">使用 `WriteAllBytes` 方法，同時提供檔案路徑、檔案名稱以及要寫入的位元組。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-108">Use the `WriteAllBytes` method, supplying the file path and name and the bytes to be written.</span></span> <span data-ttu-id="4d1f8-109">這個範例會將資料陣列 `CustomerData` 附加至名為 `CollectedData.dat` 的檔案。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-109">This example appends the data array `CustomerData` to the file named `CollectedData.dat`.</span></span>  
  
     <span data-ttu-id="4d1f8-110">[!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4d1f8-110">[!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4d1f8-111">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="4d1f8-111">Robust Programming</span></span>  
 <span data-ttu-id="4d1f8-112">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="4d1f8-112">The following conditions may create an exception:</span></span>  
  
-   <span data-ttu-id="4d1f8-113">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元，或者它包含無效的字元。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-113">The path is not valid for one of the following reasons: it is a zero-length string; it contains only white space; or it contains invalid characters.</span></span> <span data-ttu-id="4d1f8-114">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="4d1f8-114">(<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="4d1f8-115">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="4d1f8-116">`File` 指向不存在的路徑 (<xref:System.IO.FileNotFoundException> 或 <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-116">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="4d1f8-117">檔案正由另一個處理序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-117">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="4d1f8-118">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="4d1f8-119">路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="4d1f8-120">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="4d1f8-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1f8-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d1f8-121">See Also</span></span>  
 <span data-ttu-id="4d1f8-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A></span><span class="sxs-lookup"><span data-stu-id="4d1f8-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A></span></span>   
 [<span data-ttu-id="4d1f8-123">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="4d1f8-123">How to: Write Text to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)

