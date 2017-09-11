---
title: "如何：在 Visual Basic 中剖析檔案路徑"
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
- file names, parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 6327d661c6f1fe7647cc64b56d7f72f1f3455467
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-parse-file-paths-in-visual-basic"></a><span data-ttu-id="31cb2-102">如何：在 Visual Basic 中剖析檔案路徑</span><span class="sxs-lookup"><span data-stu-id="31cb2-102">How to: Parse File Paths in Visual Basic</span></span>
<span data-ttu-id="31cb2-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem> 物件提供剖析檔案路徑時的數種有用方法。</span><span class="sxs-lookup"><span data-stu-id="31cb2-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem> object offers a number of useful methods when parsing file paths.</span></span>  
  
-   <span data-ttu-id="31cb2-104"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> 方法會採用兩個路徑，並傳回格式正確的合併路徑。</span><span class="sxs-lookup"><span data-stu-id="31cb2-104">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> method takes two paths and returns a properly formatted combined path.</span></span>  
  
-   <span data-ttu-id="31cb2-105"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> 方法會傳回所提供路徑之上層的絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="31cb2-105">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> method returns the absolute path of the parent of the provided path.</span></span>  
  
-   <span data-ttu-id="31cb2-106"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> 方法會傳回 <xref:System.IO.FileInfo> 物件，這個物件可以進行查詢來判斷檔案的屬性 (例如其名稱和路徑)。</span><span class="sxs-lookup"><span data-stu-id="31cb2-106">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method returns a <xref:System.IO.FileInfo> object that can be queried to determine the file's properties, such as its name and path.</span></span>  
  
 <span data-ttu-id="31cb2-107">請不要根據副檔名來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="31cb2-107">Do not make decisions about the contents of the file based on the file name extension.</span></span> <span data-ttu-id="31cb2-108">例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="31cb2-108">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
### <a name="to-determine-a-files-name-and-path"></a><span data-ttu-id="31cb2-109">判斷檔案的名稱和路徑</span><span class="sxs-lookup"><span data-stu-id="31cb2-109">To determine a file's name and path</span></span>  
  
-   <span data-ttu-id="31cb2-110">使用 <xref:System.IO.FileInfo.DirectoryName%2A> 物件的 <xref:System.IO.FileInfo.Name%2A> 和 <xref:System.IO.FileInfo> 屬性來判斷檔案的名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="31cb2-110">Use the <xref:System.IO.FileInfo.DirectoryName%2A> and <xref:System.IO.FileInfo.Name%2A> properties of the <xref:System.IO.FileInfo> object to determine a file's name and path.</span></span> <span data-ttu-id="31cb2-111">這個範例會判斷名稱和路徑，並予以顯示。</span><span class="sxs-lookup"><span data-stu-id="31cb2-111">This example determines the name and path and displays them.</span></span>  
  
     <span data-ttu-id="31cb2-112">[!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="31cb2-112">[!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]</span></span>  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a><span data-ttu-id="31cb2-113">合併檔案的名稱和目錄以建立完整路徑</span><span class="sxs-lookup"><span data-stu-id="31cb2-113">To combine a file's name and directory to create the full path</span></span>  
  
-   <span data-ttu-id="31cb2-114">使用 `CombinePath` 方法，並提供目錄和名稱。</span><span class="sxs-lookup"><span data-stu-id="31cb2-114">Use the `CombinePath` method, supplying the directory and name.</span></span> <span data-ttu-id="31cb2-115">這個範例會採用前一個範例中所建立的字串 `folderPath` 和 `fileName` 、合併它們，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="31cb2-115">This example takes the strings `folderPath` and `fileName` created in the previous example, combines them, and displays the result.</span></span>  
  
     <span data-ttu-id="31cb2-116">[!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="31cb2-116">[!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31cb2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31cb2-117">See Also</span></span>  
 <span data-ttu-id="31cb2-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="31cb2-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="31cb2-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A></span><span class="sxs-lookup"><span data-stu-id="31cb2-119"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A></span></span>   
 <span data-ttu-id="31cb2-120"><xref:System.IO.FileInfo></span><span class="sxs-lookup"><span data-stu-id="31cb2-120"><xref:System.IO.FileInfo></span></span>   
 <span data-ttu-id="31cb2-121"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A></span><span class="sxs-lookup"><span data-stu-id="31cb2-121"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A></span></span>   
 [<span data-ttu-id="31cb2-122">如何：取得目錄的檔案集合</span><span class="sxs-lookup"><span data-stu-id="31cb2-122">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

