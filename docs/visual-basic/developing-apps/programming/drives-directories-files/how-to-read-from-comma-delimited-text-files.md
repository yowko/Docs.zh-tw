---
title: 如何：在 Visual Basic 中從逗號分隔文字檔讀取
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 050f8635e1cb0fa1a2dd29249873e3bf12dad121
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520382"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="6990f-102">如何：在 Visual Basic 中從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="6990f-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="6990f-103">`TextFieldParser` 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。</span><span class="sxs-lookup"><span data-stu-id="6990f-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="6990f-104">`TextFieldType` 屬性會定義檔案是有分隔符號的檔案，還是具有固定寬度文字欄位的檔案。</span><span class="sxs-lookup"><span data-stu-id="6990f-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="6990f-105">剖析逗號分隔文字檔</span><span class="sxs-lookup"><span data-stu-id="6990f-105">To parse a comma delimited text file</span></span>  
  
1.  <span data-ttu-id="6990f-106">建立新的 `TextFieldParser`。</span><span class="sxs-lookup"><span data-stu-id="6990f-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="6990f-107">下列程式碼會建立名為 `MyReader` 的 `TextFieldParser`，並開啟檔案 `test.txt`。</span><span class="sxs-lookup"><span data-stu-id="6990f-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  <span data-ttu-id="6990f-108">定義 `TextField` 類型和分隔符號。</span><span class="sxs-lookup"><span data-stu-id="6990f-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="6990f-109">下列程式碼會將 `TextFieldType` 屬性定義為 `Delimited`，並將分隔符號定義為 ","。</span><span class="sxs-lookup"><span data-stu-id="6990f-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  <span data-ttu-id="6990f-110">在檔案的欄位之間執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="6990f-110">Loop through the fields in the file.</span></span> <span data-ttu-id="6990f-111">如果有任何一行損毀，即會報告錯誤並繼續剖析。</span><span class="sxs-lookup"><span data-stu-id="6990f-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="6990f-112">下列程式碼會在檔案之間執行迴圈，依序顯示每個欄位，並報告所有格式不正確的欄位。</span><span class="sxs-lookup"><span data-stu-id="6990f-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  <span data-ttu-id="6990f-113">使用 `End While` 和 `End Using` 關閉 `While` 和 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="6990f-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="6990f-114">範例</span><span class="sxs-lookup"><span data-stu-id="6990f-114">Example</span></span>  
 <span data-ttu-id="6990f-115">此範例會從檔案 `test.txt` 讀取。</span><span class="sxs-lookup"><span data-stu-id="6990f-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="6990f-116">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="6990f-116">Robust programming</span></span>  
 <span data-ttu-id="6990f-117">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="6990f-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6990f-118">無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="6990f-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="6990f-119">例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。</span><span class="sxs-lookup"><span data-stu-id="6990f-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="6990f-120">指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="6990f-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="6990f-121">發生使用者權限不足而無法存取檔案的部分信任狀況</span><span class="sxs-lookup"><span data-stu-id="6990f-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="6990f-122">(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="6990f-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="6990f-123">路徑太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="6990f-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="6990f-124">使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="6990f-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6990f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6990f-125">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="6990f-126">如何：從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="6990f-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="6990f-127">如何：以多種格式從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="6990f-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="6990f-128">使用 TextFieldParser 物件剖析文字檔</span><span class="sxs-lookup"><span data-stu-id="6990f-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="6990f-129">逐步解說：在 Visual Basic 中管理檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="6990f-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="6990f-130">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="6990f-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
