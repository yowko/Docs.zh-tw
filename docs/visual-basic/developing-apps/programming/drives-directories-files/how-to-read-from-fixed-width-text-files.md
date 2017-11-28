---
title: "如何：在 Visual Basic 中從固定寬度的文字檔讀取"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5caa124af1bf4681a4c061f453ce5e09ec2dae7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="b48e0-102">如何：在 Visual Basic 中從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="b48e0-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="b48e0-103">`TextFieldParser` 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b48e0-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="b48e0-104">`TextFieldType` 屬性會定義所剖析的檔案是有分隔符號的檔案，還是具有固定寬度文字欄位的檔案。</span><span class="sxs-lookup"><span data-stu-id="b48e0-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="b48e0-105">在固定寬度的文字檔中，結尾欄位可以有可變寬度。</span><span class="sxs-lookup"><span data-stu-id="b48e0-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="b48e0-106">若要指定結尾欄位是否有可變寬度，請將其寬度定義為小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="b48e0-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="b48e0-107">剖析固定寬度的文字檔</span><span class="sxs-lookup"><span data-stu-id="b48e0-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="b48e0-108">建立新的 `TextFieldParser`。</span><span class="sxs-lookup"><span data-stu-id="b48e0-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="b48e0-109">下列程式碼會建立名為 `Reader` 的 `TextFieldParser`，並開啟檔案 `test.log`。</span><span class="sxs-lookup"><span data-stu-id="b48e0-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  <span data-ttu-id="b48e0-110">將 `TextFieldType` 屬性定義為 `FixedWidth`，並定義寬度和格式。</span><span class="sxs-lookup"><span data-stu-id="b48e0-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="b48e0-111">下列程式碼會定義文字的資料行：第一個資料行為 5 個字元寬、第二個資料行為 10 個字元寬、第三個資料行為 11 個字元寬，而第四個資料行的寬度是可變動的。</span><span class="sxs-lookup"><span data-stu-id="b48e0-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  <span data-ttu-id="b48e0-112">在檔案的欄位之間執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="b48e0-112">Loop through the fields in the file.</span></span> <span data-ttu-id="b48e0-113">如果有任何一行損毀，即會報告錯誤並繼續剖析。</span><span class="sxs-lookup"><span data-stu-id="b48e0-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  <span data-ttu-id="b48e0-114">使用 `End While` 和 `End Using` 關閉 `While` 和 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="b48e0-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="b48e0-115">範例</span><span class="sxs-lookup"><span data-stu-id="b48e0-115">Example</span></span>  
 <span data-ttu-id="b48e0-116">此範例會從檔案 `test.log` 讀取。</span><span class="sxs-lookup"><span data-stu-id="b48e0-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b48e0-117">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="b48e0-117">Robust programming</span></span>  
 <span data-ttu-id="b48e0-118">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b48e0-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b48e0-119">無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="b48e0-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="b48e0-120">例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。</span><span class="sxs-lookup"><span data-stu-id="b48e0-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="b48e0-121">指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="b48e0-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="b48e0-122">發生使用者權限不足而無法存取檔案的部分信任狀況</span><span class="sxs-lookup"><span data-stu-id="b48e0-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="b48e0-123">(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="b48e0-123">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="b48e0-124">路徑太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="b48e0-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="b48e0-125">使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="b48e0-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b48e0-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="b48e0-126">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [<span data-ttu-id="b48e0-127">如何：從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="b48e0-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="b48e0-128">如何：以多種格式從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="b48e0-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="b48e0-129">使用 TextFieldParser 物件剖析文字檔</span><span class="sxs-lookup"><span data-stu-id="b48e0-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [<span data-ttu-id="b48e0-130">逐步解說：在 Visual Basic 中管理檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="b48e0-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="b48e0-131">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="b48e0-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 
