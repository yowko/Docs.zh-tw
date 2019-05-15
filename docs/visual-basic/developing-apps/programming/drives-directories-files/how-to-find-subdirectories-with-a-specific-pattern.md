---
title: 作法：在 Visual Basic 中尋找具有特定模式的子目錄
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: fcb02fa26a3177b6f25f04174563b25cddb0ac44
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64629109"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="d802a-102">作法：在 Visual Basic 中尋找具有特定模式的子目錄</span><span class="sxs-lookup"><span data-stu-id="d802a-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="d802a-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> 方法會傳回代表目錄中子目錄之路徑名稱的唯讀字串集合。</span><span class="sxs-lookup"><span data-stu-id="d802a-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="d802a-104">您可以使用 `wildCards` 參數指定特定模式。</span><span class="sxs-lookup"><span data-stu-id="d802a-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="d802a-105">如果您想要在搜尋中包括子目錄的內容，請將 `searchType` 參數設定為 `SearchOption.SearchAllSubDirectories`。</span><span class="sxs-lookup"><span data-stu-id="d802a-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="d802a-106">如果找不到符合指定模式的目錄，則會傳回空集合。</span><span class="sxs-lookup"><span data-stu-id="d802a-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="d802a-107">尋找具有特定模式的子目錄</span><span class="sxs-lookup"><span data-stu-id="d802a-107">To find subdirectories with a specific pattern</span></span>  
  
- <span data-ttu-id="d802a-108">使用 `GetDirectories` 方法，並提供您想要搜尋之目錄的名稱和路徑。</span><span class="sxs-lookup"><span data-stu-id="d802a-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="d802a-109">下列範例會傳回目錄結構中名稱包含 "Logs" 單字的所有目錄，並將它們新增至 `ListBox1`。</span><span class="sxs-lookup"><span data-stu-id="d802a-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d802a-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d802a-110">Robust Programming</span></span>  
 <span data-ttu-id="d802a-111">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="d802a-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="d802a-112">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="d802a-113">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d802a-114">一或多個指定的萬用字元是 `Nothing`、空字串，或只包含空格 (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="d802a-115">`directory` 不存在 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="d802a-116">`directory` 指向現有檔案 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="d802a-117">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="d802a-118">路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="d802a-119">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="d802a-120">使用者缺乏必要的權限 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="d802a-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d802a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d802a-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="d802a-122">如何：尋找具有特定模式的檔案</span><span class="sxs-lookup"><span data-stu-id="d802a-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
