---
title: 作法：在 Visual Basic 中從二進位檔案讀取
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: e9b30d119a404396e2bf37aa445a420f7823c57b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980382"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a><span data-ttu-id="fe1f1-102">HOW TO：在 Visual Basic 中從二進位檔案讀取</span><span class="sxs-lookup"><span data-stu-id="fe1f1-102">How to: Read From Binary Files in Visual Basic</span></span>
<span data-ttu-id="fe1f1-103">`My.Computer.FileSystem` 物件提供用來讀取二進位檔案的 `ReadAllBytes` 方法。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-103">The `My.Computer.FileSystem` object provides the `ReadAllBytes` method for reading from binary files.</span></span>  
  
### <a name="to-read-from-a-binary-file"></a><span data-ttu-id="fe1f1-104">讀取二進位檔案</span><span class="sxs-lookup"><span data-stu-id="fe1f1-104">To read from a binary file</span></span>  
  
-   <span data-ttu-id="fe1f1-105">使用 `ReadAllBytes` 方法，以將檔案內容傳回為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-105">Use the `ReadAllBytes` method, which returns the contents of a file as a byte array.</span></span> <span data-ttu-id="fe1f1-106">此範例會從檔案 `C:/Documents and Settings/selfportrait.jpg` 讀取。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-106">This example reads from the file `C:/Documents and Settings/selfportrait.jpg`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
-   <span data-ttu-id="fe1f1-107">對於大型二進位檔案，您可以使用 <xref:System.IO.FileStream> 物件的 <xref:System.IO.FileStream.Read%2A> 方法，同時只讀取指定數量的檔案。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-107">For large binary files, you can use the <xref:System.IO.FileStream.Read%2A> method of the <xref:System.IO.FileStream> object to read from the file only a specified amount at a time.</span></span> <span data-ttu-id="fe1f1-108">您接著可以限制每次讀取作業時將檔案的多少內容載入至記憶體。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-108">You can then limit how much of the file is loaded into memory for each read operation.</span></span> <span data-ttu-id="fe1f1-109">下列程式碼範例會複製檔案，並可讓呼叫端指定在每次讀取作業時將檔案的多少內容讀入記憶體。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-109">The following code example copies a file and allows the caller to specify how much of the file is read into memory per read operation.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fe1f1-110">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="fe1f1-110">Robust Programming</span></span>  
 <span data-ttu-id="fe1f1-111">下列條件可能會造成擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="fe1f1-111">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="fe1f1-112">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="fe1f1-113">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="fe1f1-114">檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-114">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="fe1f1-115">檔案正由另一個處理序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-115">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fe1f1-116">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-116">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="fe1f1-117">路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-117">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="fe1f1-118">沒有足夠的記憶體可將字串寫入緩衝區 (<xref:System.OutOfMemoryException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-118">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="fe1f1-119">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="fe1f1-120">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-120">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="fe1f1-121">例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-121">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="fe1f1-122">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-122">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="fe1f1-123">檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。</span><span class="sxs-lookup"><span data-stu-id="fe1f1-123">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1f1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe1f1-124">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [<span data-ttu-id="fe1f1-125">從檔案讀取</span><span class="sxs-lookup"><span data-stu-id="fe1f1-125">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="fe1f1-126">如何：以多種格式從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="fe1f1-126">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="fe1f1-127">在剪貼簿儲存和讀取資料</span><span class="sxs-lookup"><span data-stu-id="fe1f1-127">Storing Data to and Reading from the Clipboard</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
