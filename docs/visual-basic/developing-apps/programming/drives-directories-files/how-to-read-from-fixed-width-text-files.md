---
title: 如何：在 Visual Basic 中從固定寬度的文字檔讀取
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: de60bbe111de151ac358c1b1c00a14dee225447d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344061"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="72bb4-102">如何：在 Visual Basic 中從固定寬度的文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="72bb4-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="72bb4-103">`TextFieldParser` 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。</span><span class="sxs-lookup"><span data-stu-id="72bb4-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="72bb4-104">`TextFieldType` 屬性會定義所剖析的檔案是有分隔符號的檔案，還是具有固定寬度文字欄位的檔案。</span><span class="sxs-lookup"><span data-stu-id="72bb4-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="72bb4-105">在固定寬度的文字檔中，結尾欄位可以有可變寬度。</span><span class="sxs-lookup"><span data-stu-id="72bb4-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="72bb4-106">若要指定結尾欄位是否有可變寬度，請將其寬度定義為小於或等於零。</span><span class="sxs-lookup"><span data-stu-id="72bb4-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="72bb4-107">剖析固定寬度的文字檔</span><span class="sxs-lookup"><span data-stu-id="72bb4-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="72bb4-108">建立新的 `TextFieldParser`。</span><span class="sxs-lookup"><span data-stu-id="72bb4-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="72bb4-109">下列程式碼會建立名為 `Reader` 的 `TextFieldParser`，並開啟檔案 `test.log`。</span><span class="sxs-lookup"><span data-stu-id="72bb4-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="72bb4-110">將 `TextFieldType` 屬性定義為 `FixedWidth`，並定義寬度和格式。</span><span class="sxs-lookup"><span data-stu-id="72bb4-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="72bb4-111">下列程式碼會定義文字的資料行：第一個資料行為 5 個字元寬、第二個資料行為 10 個字元寬、第三個資料行為 11 個字元寬，而第四個資料行的寬度是可變動的。</span><span class="sxs-lookup"><span data-stu-id="72bb4-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="72bb4-112">在檔案的欄位之間執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="72bb4-112">Loop through the fields in the file.</span></span> <span data-ttu-id="72bb4-113">如果有任何一行損毀，即會報告錯誤並繼續剖析。</span><span class="sxs-lookup"><span data-stu-id="72bb4-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="72bb4-114">使用 `End While` 和 `End Using` 關閉 `While` 和 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="72bb4-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="72bb4-115">範例</span><span class="sxs-lookup"><span data-stu-id="72bb4-115">Example</span></span>  
 <span data-ttu-id="72bb4-116">此範例會從檔案 `test.log` 讀取。</span><span class="sxs-lookup"><span data-stu-id="72bb4-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="72bb4-117">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="72bb4-117">Robust programming</span></span>  
 <span data-ttu-id="72bb4-118">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="72bb4-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="72bb4-119">無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。</span><span class="sxs-lookup"><span data-stu-id="72bb4-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="72bb4-120">例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。</span><span class="sxs-lookup"><span data-stu-id="72bb4-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="72bb4-121">指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="72bb4-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="72bb4-122">發生使用者權限不足而無法存取檔案的部分信任狀況</span><span class="sxs-lookup"><span data-stu-id="72bb4-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="72bb4-123">(<xref:System.Security.SecurityException>)</span><span class="sxs-lookup"><span data-stu-id="72bb4-123">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="72bb4-124">路徑太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="72bb4-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="72bb4-125">使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。</span><span class="sxs-lookup"><span data-stu-id="72bb4-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72bb4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72bb4-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="72bb4-127">作法：從逗號分隔文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="72bb4-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="72bb4-128">作法：以多種格式從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="72bb4-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="72bb4-129">使用 TextFieldParser 物件剖析文字檔</span><span class="sxs-lookup"><span data-stu-id="72bb4-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="72bb4-130">逐步解說：在 Visual Basic 中管理檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="72bb4-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="72bb4-131">疑難排解：讀取和寫入文字檔</span><span class="sxs-lookup"><span data-stu-id="72bb4-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
