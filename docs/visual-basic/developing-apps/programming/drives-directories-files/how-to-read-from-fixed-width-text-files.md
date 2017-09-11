---
title: "如何：在 Visual Basic 中從固定寬度的文字檔讀取 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- fixed-width text file
- reading text files, fixed-width
- files, parsing
- text files, tasks
- text files, reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: 24
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f0cd02a26be70d2d3272ecd56b11e31e3d26f83a
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="281a6-102">如何：在 Visual Basic 中從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="281a6-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="281a6-103">`TextFieldParser` 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。</span><span class="sxs-lookup"><span data-stu-id="281a6-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="281a6-104">`TextFieldType` 屬性會定義所剖析的檔案是有分隔符號的檔案，還是具有固定寬度文字欄位的檔案。</span><span class="sxs-lookup"><span data-stu-id="281a6-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="281a6-105">在固定寬度的文字檔中，結尾欄位可以有可變寬度。</span><span class="sxs-lookup"><span data-stu-id="281a6-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="281a6-106">若要指定結尾欄位是否有可變寬度，請將其寬度定義為小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="281a6-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="281a6-107">剖析固定寬度的文字檔</span><span class="sxs-lookup"><span data-stu-id="281a6-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="281a6-108">建立新的 `TextFieldParser`。</span><span class="sxs-lookup"><span data-stu-id="281a6-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="281a6-109">下列程式碼會建立名為 `Reader` 的 `TextFieldParser`，並開啟檔案 `test.log`。</span><span class="sxs-lookup"><span data-stu-id="281a6-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     <span data-ttu-id="281a6-110">[!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="281a6-110">[!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]</span></span>  
  
2.  <span data-ttu-id="281a6-111">將 `TextFieldType` 屬性定義為 `FixedWidth`，並定義寬度和格式。</span><span class="sxs-lookup"><span data-stu-id="281a6-111">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="281a6-112">下列程式碼會定義文字的資料行：第一個資料行為 5 個字元寬、第二個資料行為 10 個字元寬、第三個資料行為 11 個字元寬，而第四個資料行的寬度是可變動的。</span><span class="sxs-lookup"><span data-stu-id="281a6-112">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     <span data-ttu-id="281a6-113">[!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="281a6-113">[!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]</span></span>  
  
3.  <span data-ttu-id="281a6-114">在檔案的欄位之間執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="281a6-114">Loop through the fields in the file.</span></span> <span data-ttu-id="281a6-115">如果有任何一行損毀，即會報告錯誤並繼續剖析。</span><span class="sxs-lookup"><span data-stu-id="281a6-115">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     <span data-ttu-id="281a6-116">[!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="281a6-116">[!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]</span></span>  
  
4.  <span data-ttu-id="281a6-117">使用 `End While` 和 `End Using` 關閉 `While` 和 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="281a6-117">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     <span data-ttu-id="281a6-118">[!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="281a6-118">[!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="281a6-119">範例</span><span class="sxs-lookup"><span data-stu-id="281a6-119">Example</span></span>  
 <span data-ttu-id="281a6-120">此範例會從檔案 `test.log` 讀取。</span><span class="sxs-lookup"><span data-stu-id="281a6-120">This example reads from the file `test.log`.</span></span>  
  
 <span data-ttu-id="281a6-121">[!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="281a6-121">[!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="281a6-122">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="281a6-122">Robust programming</span></span>  
 <span data-ttu-id="281a6-123">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="281a6-123">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="281a6-124">無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="281a6-124">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="281a6-125">例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。</span><span class="sxs-lookup"><span data-stu-id="281a6-125">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="281a6-126">指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="281a6-126">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="281a6-127">發生使用者權限不足而無法存取檔案的部分信任狀況</span><span class="sxs-lookup"><span data-stu-id="281a6-127">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="281a6-128">(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="281a6-128">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="281a6-129">路徑太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="281a6-129">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="281a6-130">使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="281a6-130">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="281a6-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="281a6-131">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
<span data-ttu-id="281a6-132"> [如何：從逗號分隔文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="281a6-132"> [How to: Read From Comma-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md) </span></span>  
<span data-ttu-id="281a6-133"> [如何：以多種格式從文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span><span class="sxs-lookup"><span data-stu-id="281a6-133"> [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md) </span></span>  
<span data-ttu-id="281a6-134"> [使用 TextFieldParser 物件剖析文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span><span class="sxs-lookup"><span data-stu-id="281a6-134"> [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md) </span></span>  
<span data-ttu-id="281a6-135"> [逐步解說：在 Visual Basic 中管理檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span><span class="sxs-lookup"><span data-stu-id="281a6-135"> [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md) </span></span>  
<span data-ttu-id="281a6-136"> [疑難排解：讀取和寫入文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)</span><span class="sxs-lookup"><span data-stu-id="281a6-136"> [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)</span></span>   
 
