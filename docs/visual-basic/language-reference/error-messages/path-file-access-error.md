---
title: 路徑 / 檔案存取錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 3c364296997f571956caad995581102ed990549d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842560"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="04d54-102">路徑/檔案存取錯誤</span><span class="sxs-lookup"><span data-stu-id="04d54-102">Path/File access error</span></span>
<span data-ttu-id="04d54-103">存取檔案或磁碟存取作業時，作業系統可能進行的路徑和檔案名稱之間的連線。</span><span class="sxs-lookup"><span data-stu-id="04d54-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="04d54-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="04d54-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="04d54-105">請確定已正確地格式化檔案規格。</span><span class="sxs-lookup"><span data-stu-id="04d54-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="04d54-106">檔案名稱可以包含完整 （絕對） 或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="04d54-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="04d54-107">（如果路徑在另一個磁碟機上），磁碟機名稱開頭的完整的路徑，並列出該檔案從根的明確路徑。</span><span class="sxs-lookup"><span data-stu-id="04d54-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="04d54-108">任何不完整的路徑是相對於目前的磁碟機和目錄。</span><span class="sxs-lookup"><span data-stu-id="04d54-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2.  <span data-ttu-id="04d54-109">請確定您沒有不嘗試儲存檔案，其中會取代現有的唯讀檔案。</span><span class="sxs-lookup"><span data-stu-id="04d54-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="04d54-110">如果發生這種情況，變更唯讀屬性的目標檔案，或使用不同的檔案名稱儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="04d54-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3.  <span data-ttu-id="04d54-111">請確定您未嘗試開啟唯讀檔案，在循序`Output`或`Append`模式。</span><span class="sxs-lookup"><span data-stu-id="04d54-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="04d54-112">如果發生這種情況，請開啟檔案的`Input`模式或變更檔案的唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="04d54-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4.  <span data-ttu-id="04d54-113">請確定您未嘗試變更 Visual Basic 專案中的資料庫或文件。</span><span class="sxs-lookup"><span data-stu-id="04d54-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d54-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04d54-114">See also</span></span>

- [<span data-ttu-id="04d54-115">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="04d54-115">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
