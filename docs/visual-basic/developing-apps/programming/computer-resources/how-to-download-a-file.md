---
title: 作法：在 Visual Basic 中下載檔案
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 4dd45ef70dbe3b1949e6d787748bbb27bb88d52c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046618"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="5b582-102">作法：在 Visual Basic 中下載檔案</span><span class="sxs-lookup"><span data-stu-id="5b582-102">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="5b582-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> 方法可以用來下載遠端檔案，並將它儲存到特定位置。</span><span class="sxs-lookup"><span data-stu-id="5b582-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="5b582-104">如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示下載進度，並允許使用者取消作業。</span><span class="sxs-lookup"><span data-stu-id="5b582-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="5b582-105">根據預設，不會覆寫具有相同名稱的現有檔案；如果您想要覆寫現有檔案，請將 `overwrite` 參數設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="5b582-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="5b582-106">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="5b582-106">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="5b582-107">磁碟機名稱無效 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="5b582-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="5b582-108">未提供必要驗證 (<xref:System.UnauthorizedAccessException> 或 <xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="5b582-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="5b582-109">伺服器在指定的 `connectionTimeout` 內沒有回應 (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="5b582-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="5b582-110">要求被網站拒絕 (<xref:System.Net.WebException>)。</span><span class="sxs-lookup"><span data-stu-id="5b582-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="5b582-111">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="5b582-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="5b582-112">例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="5b582-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="5b582-113">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="5b582-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="5b582-114">檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。</span><span class="sxs-lookup"><span data-stu-id="5b582-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="5b582-115">下載檔案</span><span class="sxs-lookup"><span data-stu-id="5b582-115">To download a file</span></span>

- <span data-ttu-id="5b582-116">使用 `DownloadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置，以及指定要儲存檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="5b582-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="5b582-117">此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至 `C:\Documents and Settings\All Users\Documents`：</span><span class="sxs-lookup"><span data-stu-id="5b582-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="5b582-118">下載檔案並指定逾時間隔</span><span class="sxs-lookup"><span data-stu-id="5b582-118">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="5b582-119">使用 `DownloadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置、指定要儲存檔案的位置，以及指定以毫秒為單位的逾時間隔 (預設值為 1000)。</span><span class="sxs-lookup"><span data-stu-id="5b582-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="5b582-120">此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至 `C:\Documents and Settings\All Users\Documents`，並指定 500 毫秒的逾時間隔：</span><span class="sxs-lookup"><span data-stu-id="5b582-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="5b582-121">下載檔案並提供使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="5b582-121">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="5b582-122">使用 `DownLoadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置，以及指定要儲存檔案、使用者名稱和密碼的位置。</span><span class="sxs-lookup"><span data-stu-id="5b582-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="5b582-123">此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至具有使用者名稱 `anonymous` 和空白密碼的 `C:\Documents and Settings\All Users\Documents`。</span><span class="sxs-lookup"><span data-stu-id="5b582-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="5b582-124">`DownLoadFile` 方法所使用的 FTP 通訊協定會以純文字傳送資訊 (包括密碼)，不應用於傳輸機密資訊。</span><span class="sxs-lookup"><span data-stu-id="5b582-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b582-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b582-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="5b582-126">如何：上傳檔案</span><span class="sxs-lookup"><span data-stu-id="5b582-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="5b582-127">如何：剖析檔案路徑</span><span class="sxs-lookup"><span data-stu-id="5b582-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
