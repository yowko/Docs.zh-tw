---
title: 作法：在 Visual Basic 中從文字檔讀取
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: f830a0794f67c0f8f7aca24a181e323317901923
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955963"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="2502f-102">作法：在 Visual Basic 中從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="2502f-102">How to: Read From Text Files in Visual Basic</span></span>
<span data-ttu-id="2502f-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> 物件的 `My.Computer.FileSystem` 方法允許您從文字檔讀取。</span><span class="sxs-lookup"><span data-stu-id="2502f-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="2502f-104">如果檔案的內容是使用 ASCII 或 UTF-8 之類的編碼方式，則可以指定檔案編碼方式。</span><span class="sxs-lookup"><span data-stu-id="2502f-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>  
  
 <span data-ttu-id="2502f-105">如果您是從含擴充字元的檔案讀取，您將需要指定檔案的編碼方式。</span><span class="sxs-lookup"><span data-stu-id="2502f-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2502f-106">若要一次讀取檔案中的一行文字，請使用 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> 物件的 `My.Computer.FileSystem` 方法。</span><span class="sxs-lookup"><span data-stu-id="2502f-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="2502f-107">`OpenTextFileReader` 方法會傳回 <xref:System.IO.StreamReader> 物件。</span><span class="sxs-lookup"><span data-stu-id="2502f-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="2502f-108">您可以使用 <xref:System.IO.StreamReader.ReadLine%2A> 物件的 `StreamReader` 方法，以一次讀取檔案中的一行。</span><span class="sxs-lookup"><span data-stu-id="2502f-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="2502f-109">您可以使用 <xref:System.IO.StreamReader.EndOfStream%2A> 物件的 `StreamReader` 方法測試檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="2502f-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>  
  
### <a name="to-read-from-a-text-file"></a><span data-ttu-id="2502f-110">若要從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="2502f-110">To read from a text file</span></span>  
  
- <span data-ttu-id="2502f-111">使用 `ReadAllText` 物件的 `My.Computer.FileSystem` 方法並提供路徑，將文字檔的內容讀取到字串中。</span><span class="sxs-lookup"><span data-stu-id="2502f-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="2502f-112">下列範例會將 test.txt 的內容讀取到字串中，然後顯示於訊息方塊中。</span><span class="sxs-lookup"><span data-stu-id="2502f-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="2502f-113">若要從已編碼的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="2502f-113">To read from a text file that is encoded</span></span>  
  
- <span data-ttu-id="2502f-114">使用 `ReadAllText` 物件的 `My.Computer.FileSystem` 方法，並且提供路徑和檔案編碼類型，將文字檔的內容讀取到字串中。</span><span class="sxs-lookup"><span data-stu-id="2502f-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="2502f-115">下列範例會將 UTF32 檔案 test.txt 的內容讀取到字串中，然後顯示於訊息方塊中。</span><span class="sxs-lookup"><span data-stu-id="2502f-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2502f-116">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="2502f-116">Robust Programming</span></span>  
 <span data-ttu-id="2502f-117">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="2502f-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="2502f-118">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="2502f-119">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="2502f-120">檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="2502f-121">檔案正由另一個程序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2502f-122">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="2502f-123">路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="2502f-124">沒有足夠的記憶體可將字串寫入緩衝區 (<xref:System.OutOfMemoryException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
- <span data-ttu-id="2502f-125">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="2502f-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="2502f-126">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="2502f-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="2502f-127">例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="2502f-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="2502f-128">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="2502f-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="2502f-129">檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。</span><span class="sxs-lookup"><span data-stu-id="2502f-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2502f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2502f-130">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="2502f-131">從檔案讀取</span><span class="sxs-lookup"><span data-stu-id="2502f-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="2502f-132">如何：從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="2502f-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="2502f-133">如何：從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="2502f-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="2502f-134">如何：以多種格式從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="2502f-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="2502f-135">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="2502f-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="2502f-136">逐步解說：在 Visual Basic 中管理檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="2502f-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="2502f-137">檔案編碼方式</span><span class="sxs-lookup"><span data-stu-id="2502f-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
