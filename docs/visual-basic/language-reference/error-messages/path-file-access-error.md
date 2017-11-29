---
title: "路徑檔案存取錯誤"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a><span data-ttu-id="a055a-102">路徑/檔案存取錯誤</span><span class="sxs-lookup"><span data-stu-id="a055a-102">Path/File access error</span></span>
<span data-ttu-id="a055a-103">檔案存取或磁碟存取作業時，作業系統無法建立路徑和檔案名稱之間的連接。</span><span class="sxs-lookup"><span data-stu-id="a055a-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a055a-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a055a-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="a055a-105">請確定已正確地格式化檔案規格。</span><span class="sxs-lookup"><span data-stu-id="a055a-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="a055a-106">檔案名稱可以包含完整 （絕對） 或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="a055a-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="a055a-107">使用磁碟機名稱 （如果路徑在另一個磁碟機上） 開始的完整的路徑，並列出根檔案的明確路徑。</span><span class="sxs-lookup"><span data-stu-id="a055a-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="a055a-108">任何不完整的路徑是相對於目前的磁碟機和目錄。</span><span class="sxs-lookup"><span data-stu-id="a055a-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="a055a-109">請務必確認您未嘗試儲存檔案，來取代現有的唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="a055a-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="a055a-110">如果這種情況時，變更唯讀屬性的目標檔案，或使用不同的檔案名稱儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="a055a-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="a055a-111">請確定您未嘗試開啟唯讀檔案中循序`Output`或`Append`模式。</span><span class="sxs-lookup"><span data-stu-id="a055a-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="a055a-112">如果這種情況，請開啟檔案的`Input`模式或變更檔案的唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="a055a-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="a055a-113">請確定您未嘗試變更[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]資料庫或文件中的專案。</span><span class="sxs-lookup"><span data-stu-id="a055a-113">Make sure you did not attempt to change a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a055a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a055a-114">See Also</span></span>  
 [<span data-ttu-id="a055a-115">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="a055a-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
