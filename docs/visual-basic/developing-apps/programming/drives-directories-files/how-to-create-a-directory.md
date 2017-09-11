---
title: "如何：在 Visual Basic 中建立目錄"
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
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
caps.latest.revision: 19
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
ms.openlocfilehash: 1a45a785916b480dcee6e36fd295390266eaa0a0
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-directory-in-visual-basic"></a><span data-ttu-id="71b54-102">如何：在 Visual Basic 中建立目錄</span><span class="sxs-lookup"><span data-stu-id="71b54-102">How to: Create a Directory in Visual Basic</span></span>
<span data-ttu-id="71b54-103">使用 `My.Computer.FileSystem` 物件的 `CreateDirectory` 方法來建立目錄。</span><span class="sxs-lookup"><span data-stu-id="71b54-103">Use the `CreateDirectory` method of the `My.Computer.FileSystem` object to create directories.</span></span>  
  
 <span data-ttu-id="71b54-104">如果目錄已經存在，則不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="71b54-104">If the directory already exists, no exception is thrown.</span></span>  
  
### <a name="to-create-a-directory"></a><span data-ttu-id="71b54-105">建立目錄</span><span class="sxs-lookup"><span data-stu-id="71b54-105">To create a directory</span></span>  
  
-   <span data-ttu-id="71b54-106">指定應該建立目錄之位置的完整路徑，以使用 `CreateDirectory` 方法。</span><span class="sxs-lookup"><span data-stu-id="71b54-106">Use the `CreateDirectory` method by specifying the full path of the location where the directory should be created.</span></span> <span data-ttu-id="71b54-107">這個範例會在 `C:\Documents and Settings\All Users\Documents` 中建立 `NewDirectory` 目錄。</span><span class="sxs-lookup"><span data-stu-id="71b54-107">This example creates the directory `NewDirectory` in `C:\Documents and Settings\All Users\Documents`.</span></span>  
  
     <span data-ttu-id="71b54-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="71b54-108">[!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="71b54-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="71b54-109">Robust Programming</span></span>  
 <span data-ttu-id="71b54-110">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="71b54-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="71b54-111">目錄名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="71b54-111">The directory name is malformed.</span></span> <span data-ttu-id="71b54-112">例如，它包含不合法的字元，或只有空白字元 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="71b54-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="71b54-113">要建立之目錄的父目錄為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="71b54-113">The parent directory of the directory to be created is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="71b54-114">目錄名稱為 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="71b54-114">The directory name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="71b54-115">目錄名稱太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="71b54-115">The directory name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="71b54-116">目錄名稱為冒號 ":" (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="71b54-116">The directory name is a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="71b54-117">使用者沒有權限，無法建立目錄 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="71b54-117">The user does not have permission to create the directory (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="71b54-118">使用者在部分信任狀況下的權限不足 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="71b54-118">The user lacks permissions in a partial-trust situation (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71b54-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71b54-119">See Also</span></span>  
 <span data-ttu-id="71b54-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span><span class="sxs-lookup"><span data-stu-id="71b54-120"><xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A></span></span>   
 [<span data-ttu-id="71b54-121">建立、刪除和移動檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="71b54-121">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)

