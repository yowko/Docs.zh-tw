---
title: 無法寫入輸出檔&#39;&lt;檔名&gt;&#39;:&lt;錯誤&gt;
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: c82f1e6e4a01af87cc7dce49cfaa78f9be1631db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572691"
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="a0032-102">無法寫入輸出檔&#39;&lt;檔名&gt;&#39;:&lt;錯誤&gt;</span><span class="sxs-lookup"><span data-stu-id="a0032-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="a0032-103">建立檔案時發生問題。</span><span class="sxs-lookup"><span data-stu-id="a0032-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="a0032-104">無法開啟輸出檔案以供寫入。</span><span class="sxs-lookup"><span data-stu-id="a0032-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="a0032-105">檔案 (或包含檔案的資料夾) 可能已由另一個處理序以獨佔方式開啟使用，或是其可能設定了唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="a0032-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="a0032-106">以獨佔方式開啟檔案的常見狀況有：</span><span class="sxs-lookup"><span data-stu-id="a0032-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="a0032-107">應用程式已在執行中，且正在使用其檔案。</span><span class="sxs-lookup"><span data-stu-id="a0032-107">The application is already running and using its files.</span></span> <span data-ttu-id="a0032-108">若要解決此問題，請確定應用程式不在執行中。</span><span class="sxs-lookup"><span data-stu-id="a0032-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="a0032-109">另一個應用程式已開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="a0032-109">Another application has opened the file.</span></span> <span data-ttu-id="a0032-110">若要解決此問題，請確定沒有其他應用程式正在存取檔案。</span><span class="sxs-lookup"><span data-stu-id="a0032-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="a0032-111">您不一定能顯而易見地分辨出是哪個應用程式在存取您的檔案；在這種情況下，重新啟動電腦可能是終止該應用程式最容易的方法。</span><span class="sxs-lookup"><span data-stu-id="a0032-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="a0032-112">即使是其中一個專案輸出檔被標為唯讀，都會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a0032-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="a0032-113">**錯誤 ID:** BC31019</span><span class="sxs-lookup"><span data-stu-id="a0032-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0032-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a0032-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="a0032-115">再次編譯程式，看看錯誤是否重複發生。</span><span class="sxs-lookup"><span data-stu-id="a0032-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="a0032-116">如果錯誤持續發生，請儲存您的工作，然後重新啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a0032-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3.  <span data-ttu-id="a0032-117">如果錯誤繼續發生，請重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="a0032-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="a0032-118">如果錯誤重複發生，請重新安裝 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="a0032-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="a0032-119">如果錯誤在重新安裝之後持續發生，請通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="a0032-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="a0032-120">在檔案總管中檢查檔案屬性</span><span class="sxs-lookup"><span data-stu-id="a0032-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="a0032-121">開啟您感興趣的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a0032-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="a0032-122">按一下 **檢視**圖示，然後選擇**詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="a0032-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="a0032-123">以滑鼠右鍵按一下資料行標頭，然後選擇**屬性**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a0032-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="a0032-124">變更檔案或資料夾的屬性</span><span class="sxs-lookup"><span data-stu-id="a0032-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="a0032-125">在 **檔案總管**，以滑鼠右鍵按一下檔案或資料夾，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="a0032-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="a0032-126">在 [**屬性**一節**一般**索引標籤上，清除**唯讀**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="a0032-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="a0032-127">按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a0032-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0032-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0032-128">See also</span></span>
- [<span data-ttu-id="a0032-129">告訴我們</span><span class="sxs-lookup"><span data-stu-id="a0032-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
