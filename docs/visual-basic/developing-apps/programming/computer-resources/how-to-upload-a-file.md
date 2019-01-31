---
title: HOW TO：在 Visual Basic 中上傳檔案
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 0d0aaca06a72b9bd2631a652a0b4756f4681df7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704403"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="762b5-102">HOW TO：在 Visual Basic 中上傳檔案</span><span class="sxs-lookup"><span data-stu-id="762b5-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="762b5-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> 方法可以用於上傳檔案，並將其存放到遠端位置。</span><span class="sxs-lookup"><span data-stu-id="762b5-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="762b5-104">如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示上傳進度，並允許使用者取消作業。</span><span class="sxs-lookup"><span data-stu-id="762b5-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="762b5-105">上傳檔案</span><span class="sxs-lookup"><span data-stu-id="762b5-105">To upload a file</span></span>  
  
-   <span data-ttu-id="762b5-106">使用 `UploadFile` 方法來上傳檔案，並將來源檔案的位置和目標目錄位置指定為字串或 URI (統一資源識別項)。這個範例會將檔案 `Order.txt` 上傳到 `http://www.cohowinery.com/uploads.aspx`。</span><span class="sxs-lookup"><span data-stu-id="762b5-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="762b5-107">上傳檔案並顯示作業進度</span><span class="sxs-lookup"><span data-stu-id="762b5-107">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="762b5-108">使用 `UploadFile` 方法來上傳檔案，並將來源檔案的位置和目標目錄位置指定為字串或 URI。</span><span class="sxs-lookup"><span data-stu-id="762b5-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="762b5-109">這個範例會在未提供使用者名稱或密碼的情況下將 `Order.txt` 檔案上傳至 `http://www.cohowinery.com/uploads.aspx`、顯示上傳進度，並具有 500 毫秒的逾時間隔。</span><span class="sxs-lookup"><span data-stu-id="762b5-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="762b5-110">上傳檔案並提供使用者名稱和密碼</span><span class="sxs-lookup"><span data-stu-id="762b5-110">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="762b5-111">使用 `UploadFile` 方法來上傳檔案，並將來源檔案的位置和目標目錄位置指定為字串或 URI，以及指定使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="762b5-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="762b5-112">這個範例會將 `Order.txt` 檔案上傳至 `http://www.cohowinery.com/uploads.aspx`，並提供使用者名稱 `anonymous` 和空白密碼。</span><span class="sxs-lookup"><span data-stu-id="762b5-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="762b5-113">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="762b5-113">Robust Programming</span></span>  
 <span data-ttu-id="762b5-114">下列條件可能會擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="762b5-114">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="762b5-115">本機檔案路徑無效 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="762b5-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="762b5-116">驗證失敗 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="762b5-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="762b5-117">連線逾時 (<xref:System.TimeoutException>)。</span><span class="sxs-lookup"><span data-stu-id="762b5-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="762b5-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="762b5-118">See also</span></span>
- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="762b5-119">如何：下載檔案</span><span class="sxs-lookup"><span data-stu-id="762b5-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="762b5-120">如何：剖析檔案路徑</span><span class="sxs-lookup"><span data-stu-id="762b5-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
