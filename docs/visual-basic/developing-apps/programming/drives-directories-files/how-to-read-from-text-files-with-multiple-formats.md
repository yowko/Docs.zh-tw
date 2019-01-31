---
title: HOW TO：在 Visual Basic 中以多種格式從文字檔讀取
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: fd48f77a299c5d29a32f96e4e063e262ad20fd18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678495"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="c6b21-102">HOW TO：在 Visual Basic 中以多種格式從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="c6b21-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="c6b21-103"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c6b21-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="c6b21-104">您可以使用 `PeekChars` 方法來處理具有多種格式的檔案，以在剖析整個檔案時判斷每行格式。</span><span class="sxs-lookup"><span data-stu-id="c6b21-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="c6b21-105">剖析具有多種格式的文字檔</span><span class="sxs-lookup"><span data-stu-id="c6b21-105">To parse a text file with multiple formats</span></span>  
  
1.  <span data-ttu-id="c6b21-106">將名為 testfile.txt 的文字檔新增至專案。</span><span class="sxs-lookup"><span data-stu-id="c6b21-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="c6b21-107">將下列內容新增至文字檔。</span><span class="sxs-lookup"><span data-stu-id="c6b21-107">Add the following content to the text file.</span></span>  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  <span data-ttu-id="c6b21-108">定義預期的格式，以及回報錯誤時所使用的格式。</span><span class="sxs-lookup"><span data-stu-id="c6b21-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="c6b21-109">每個陣列中的最後一個項目為 -1，因此將最後一個欄位假設為可變寬度。</span><span class="sxs-lookup"><span data-stu-id="c6b21-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="c6b21-110">陣列中的最後一個項目小於或等於 0 時會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="c6b21-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  <span data-ttu-id="c6b21-111">建立新的 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件，並定義寬度和格式。</span><span class="sxs-lookup"><span data-stu-id="c6b21-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  <span data-ttu-id="c6b21-112">反覆執行資料列，並在讀取之前測試格式。</span><span class="sxs-lookup"><span data-stu-id="c6b21-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  <span data-ttu-id="c6b21-113">將錯誤寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="c6b21-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="c6b21-114">範例</span><span class="sxs-lookup"><span data-stu-id="c6b21-114">Example</span></span>  
 <span data-ttu-id="c6b21-115">下列是從 `testfile.txt` 檔案進行讀取的完整範例。</span><span class="sxs-lookup"><span data-stu-id="c6b21-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c6b21-116">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="c6b21-116">Robust Programming</span></span>  
 <span data-ttu-id="c6b21-117">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="c6b21-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="c6b21-118">無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="c6b21-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="c6b21-119">例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。</span><span class="sxs-lookup"><span data-stu-id="c6b21-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="c6b21-120">指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="c6b21-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="c6b21-121">發生使用者權限不足而無法存取檔案的部分信任狀況</span><span class="sxs-lookup"><span data-stu-id="c6b21-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="c6b21-122">(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="c6b21-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="c6b21-123">路徑太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="c6b21-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="c6b21-124">使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="c6b21-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6b21-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6b21-125">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="c6b21-126">如何：從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="c6b21-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="c6b21-127">如何：從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="c6b21-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="c6b21-128">使用 TextFieldParser 物件剖析文字檔</span><span class="sxs-lookup"><span data-stu-id="c6b21-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
