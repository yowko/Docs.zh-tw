---
title: "無法寫入輸出檔 &quot;&lt;filename&gt;&quot;:&lt;錯誤&gt;|Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31019
- bc31019
dev_langs:
- VB
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
caps.latest.revision: 10
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0822a732390f308b5f8f1f1431299552fb876e74
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="a23a4-102">無法寫入輸出檔 '&lt;filename&gt;':&lt;錯誤&gt;</span><span class="sxs-lookup"><span data-stu-id="a23a4-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="a23a4-103">建立檔案時發生問題。</span><span class="sxs-lookup"><span data-stu-id="a23a4-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="a23a4-104">無法開啟輸出檔案以供寫入。</span><span class="sxs-lookup"><span data-stu-id="a23a4-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="a23a4-105">檔案 (或包含檔案的資料夾) 可能已由另一個處理序以獨佔方式開啟使用，或是其可能設定了唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="a23a4-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="a23a4-106">以獨佔方式開啟檔案的常見狀況有：</span><span class="sxs-lookup"><span data-stu-id="a23a4-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="a23a4-107">應用程式已在執行中，且正在使用其檔案。</span><span class="sxs-lookup"><span data-stu-id="a23a4-107">The application is already running and using its files.</span></span> <span data-ttu-id="a23a4-108">若要解決此問題，請確定應用程式不在執行中。</span><span class="sxs-lookup"><span data-stu-id="a23a4-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="a23a4-109">另一個應用程式已開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="a23a4-109">Another application has opened the file.</span></span> <span data-ttu-id="a23a4-110">若要解決此問題，請確定沒有其他應用程式正在存取檔案。</span><span class="sxs-lookup"><span data-stu-id="a23a4-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="a23a4-111">您不一定能顯而易見地分辨出是哪個應用程式在存取您的檔案；在這種情況下，重新啟動電腦可能是終止該應用程式最容易的方法。</span><span class="sxs-lookup"><span data-stu-id="a23a4-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="a23a4-112">即使是其中一個專案輸出檔被標為唯讀，都會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a23a4-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="a23a4-113">**錯誤識別碼︰** BC31019</span><span class="sxs-lookup"><span data-stu-id="a23a4-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a23a4-114">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="a23a4-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="a23a4-115">再次編譯程式，看看錯誤是否重複發生。</span><span class="sxs-lookup"><span data-stu-id="a23a4-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="a23a4-116">如果錯誤繼續發生，請儲存您的工作，然後重新啟動 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a23a4-116">If the error continues, save your work and restart [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)].</span></span>  
  
3.  <span data-ttu-id="a23a4-117">如果錯誤繼續發生，請重新啟動電腦。</span><span class="sxs-lookup"><span data-stu-id="a23a4-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="a23a4-118">如果問題重複發生，請重新安裝 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a23a4-118">If the error recurs, reinstall [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>  
  
5.  <span data-ttu-id="a23a4-119">如果錯誤在重新安裝之後持續發生，請通知 Microsoft 產品支援服務。</span><span class="sxs-lookup"><span data-stu-id="a23a4-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="a23a4-120">在檔案總管中檢查檔案屬性</span><span class="sxs-lookup"><span data-stu-id="a23a4-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="a23a4-121">開啟您感興趣的資料夾。</span><span class="sxs-lookup"><span data-stu-id="a23a4-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="a23a4-122">按一下 **檢視**圖示，然後選擇**詳細資料**。</span><span class="sxs-lookup"><span data-stu-id="a23a4-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="a23a4-123">以滑鼠右鍵按一下資料行標頭，然後選擇 **屬性**從下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="a23a4-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="a23a4-124">變更檔案或資料夾的屬性</span><span class="sxs-lookup"><span data-stu-id="a23a4-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="a23a4-125">在**檔案總管**，以滑鼠右鍵按一下檔案或資料夾，然後選擇 **屬性**。</span><span class="sxs-lookup"><span data-stu-id="a23a4-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="a23a4-126">在**屬性**區段**一般**索引標籤上，清除**唯讀**方塊。</span><span class="sxs-lookup"><span data-stu-id="a23a4-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="a23a4-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="a23a4-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a23a4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a23a4-128">See Also</span></span>  
 [<span data-ttu-id="a23a4-129">告訴我們</span><span class="sxs-lookup"><span data-stu-id="a23a4-129">Talk to Us</span></span>](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
