---
title: 路徑 - 檔案存取錯誤
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 70de8f9cb33ab3d889f4916ae3d5de48cd218092
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871197"
---
# <a name="pathfile-access-error"></a><span data-ttu-id="68f30-102">路徑/檔案存取錯誤</span><span class="sxs-lookup"><span data-stu-id="68f30-102">Path/File access error</span></span>

<span data-ttu-id="68f30-103">在檔案存取或磁片存取作業期間，作業系統無法建立路徑與檔案名之間的連接。</span><span class="sxs-lookup"><span data-stu-id="68f30-103">During a file-access or disk-access operation, the operating system could not make a connection between the path and the file name.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="68f30-104">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="68f30-104">To correct this error</span></span>  
  
1. <span data-ttu-id="68f30-105">請確認檔案規格的格式正確。</span><span class="sxs-lookup"><span data-stu-id="68f30-105">Make sure the file specification is correctly formatted.</span></span> <span data-ttu-id="68f30-106">檔案名可以包含完整的 (絕對) 或相對路徑。</span><span class="sxs-lookup"><span data-stu-id="68f30-106">A file name can contain a fully qualified (absolute) or relative path.</span></span> <span data-ttu-id="68f30-107">完整路徑的開頭為磁片磁碟機名稱 (如果路徑是在另一個磁片磁碟機上) ，並列出從根目錄到檔案的明確路徑。</span><span class="sxs-lookup"><span data-stu-id="68f30-107">A fully qualified path starts with the drive name (if the path is on another drive) and lists the explicit path from the root to the file.</span></span> <span data-ttu-id="68f30-108">任何未完整限定的路徑都是相對於目前磁片磁碟機和目錄。</span><span class="sxs-lookup"><span data-stu-id="68f30-108">Any path that is not fully qualified is relative to the current drive and directory.</span></span>  
  
2. <span data-ttu-id="68f30-109">請確定您未嘗試儲存會取代現有唯讀檔案的檔案。</span><span class="sxs-lookup"><span data-stu-id="68f30-109">Make sure that you did not attempt to save a file that would replace an existing read-only file.</span></span> <span data-ttu-id="68f30-110">如果是這種情況，請變更目標檔案的唯讀屬性，或以不同的檔案名儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="68f30-110">If this is the case, change the read-only attribute of the target file, or save the file with a different file name.</span></span>  
  
3. <span data-ttu-id="68f30-111">請確定您未嘗試以連續 `Output` 模式或模式開啟唯讀檔案 `Append` 。</span><span class="sxs-lookup"><span data-stu-id="68f30-111">Make sure you did not attempt to open a read-only file in sequential `Output` or `Append` mode.</span></span> <span data-ttu-id="68f30-112">如果是這種情況，請以模式開啟檔案， `Input` 或變更檔案的唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="68f30-112">If this is the case, open the file in `Input` mode or change the read-only attribute of the file.</span></span>  
  
4. <span data-ttu-id="68f30-113">請確定您未嘗試變更資料庫或檔內的 Visual Basic 專案。</span><span class="sxs-lookup"><span data-stu-id="68f30-113">Make sure you did not attempt to change a Visual Basic project within a database or document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f30-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68f30-114">See also</span></span>

- [<span data-ttu-id="68f30-115">錯誤類型</span><span class="sxs-lookup"><span data-stu-id="68f30-115">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
