---
title: "如何：以 StreamReader 從檔案讀取文字 (Visual Basic)"
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
- reading files, text
- text, reading from files
- reading text from files
- files, reading
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: 18
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d895b32b1613462a6c8dedcc19040b5040f936ec
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-text-from-files-with-a-streamreader-visual-basic"></a><span data-ttu-id="cee2a-102">如何：以 StreamReader 從檔案讀取文字 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cee2a-102">How to: Read Text from Files with a StreamReader (Visual Basic)</span></span>
<span data-ttu-id="cee2a-103">`My.Computer.FileSystem` 物件提供方法來開啟 <xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter>。</span><span class="sxs-lookup"><span data-stu-id="cee2a-103">The `My.Computer.FileSystem` object provides methods to open a <xref:System.IO.TextReader> and a <xref:System.IO.TextWriter>.</span></span> <span data-ttu-id="cee2a-104">除非您選取 [全部] 索引標籤，否則 `OpenTextFileWriter` 和 `OpenTextFileReader` 這兩種方法是未出現在 IntelliSense 中的進階方法。</span><span class="sxs-lookup"><span data-stu-id="cee2a-104">These methods, `OpenTextFileWriter` and `OpenTextFileReader`, are advanced methods that do not appear in IntelliSense unless you select the **All** tab.</span></span>  
  
### <a name="to-read-a-line-from-a-file-with-a-text-reader"></a><span data-ttu-id="cee2a-105">使用文字讀取器從檔案讀取一行</span><span class="sxs-lookup"><span data-stu-id="cee2a-105">To read a line from a file with a text reader</span></span>  
  
-   <span data-ttu-id="cee2a-106">使用 `OpenTextFileReader` 方法來開啟 <xref:System.IO.TextReader>，並指定檔案。</span><span class="sxs-lookup"><span data-stu-id="cee2a-106">Use the `OpenTextFileReader` method to open the <xref:System.IO.TextReader>, specifying the file.</span></span> <span data-ttu-id="cee2a-107">這個範例會開啟名為 `testfile.txt` 的檔案，並讀取其中一行，然後顯示訊息方塊中的行。</span><span class="sxs-lookup"><span data-stu-id="cee2a-107">This example opens the file named `testfile.txt`, reads a line from it, and displays the line in a message box.</span></span>  
  
     <span data-ttu-id="cee2a-108">[!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="cee2a-108">[!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="cee2a-109">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="cee2a-109">Robust Programming</span></span>  
 <span data-ttu-id="cee2a-110">讀取的檔案必須是文字檔。</span><span class="sxs-lookup"><span data-stu-id="cee2a-110">The file that is read must be a text file.</span></span>  
  
 <span data-ttu-id="cee2a-111">請勿根據檔案名稱來判斷檔案內容。</span><span class="sxs-lookup"><span data-stu-id="cee2a-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="cee2a-112">例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。</span><span class="sxs-lookup"><span data-stu-id="cee2a-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>  
  
 <span data-ttu-id="cee2a-113">在應用程式中使用這些資料之前，請先驗證所有輸入值。</span><span class="sxs-lookup"><span data-stu-id="cee2a-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="cee2a-114">檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。</span><span class="sxs-lookup"><span data-stu-id="cee2a-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cee2a-115">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="cee2a-115">.NET Framework Security</span></span>  
 <span data-ttu-id="cee2a-116">若要讀取檔案，您的組件需要 <xref:System.Security.Permissions.FileIOPermission> 類別所授與的權限等級。</span><span class="sxs-lookup"><span data-stu-id="cee2a-116">To read from a file, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission> class.</span></span> <span data-ttu-id="cee2a-117">如果要在部分信任內容中執行，則程式碼可能會因權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cee2a-117">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="cee2a-118">如需詳細資訊，請參閱[程式碼存取安全性基本概念](https://msdn.microsoft.com/library/33tceax8)。</span><span class="sxs-lookup"><span data-stu-id="cee2a-118">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span> <span data-ttu-id="cee2a-119">使用者也需要存取檔案。</span><span class="sxs-lookup"><span data-stu-id="cee2a-119">The user also needs access to the file.</span></span> <span data-ttu-id="cee2a-120">如需詳細資訊，請參閱 [ACL 技術概觀](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045)。</span><span class="sxs-lookup"><span data-stu-id="cee2a-120">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cee2a-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cee2a-121">See Also</span></span>  
 <span data-ttu-id="cee2a-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span><span class="sxs-lookup"><span data-stu-id="cee2a-122"><xref:Microsoft.VisualBasic.FileIO.FileSystem></span></span>   
 <span data-ttu-id="cee2a-123"><xref:System.Windows.Forms.OpenFileDialog></span><span class="sxs-lookup"><span data-stu-id="cee2a-123"><xref:System.Windows.Forms.OpenFileDialog></span></span>   
 <span data-ttu-id="cee2a-124"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span><span class="sxs-lookup"><span data-stu-id="cee2a-124"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span></span>   
 <span data-ttu-id="cee2a-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A></span><span class="sxs-lookup"><span data-stu-id="cee2a-125"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A></span></span>   
 <span data-ttu-id="cee2a-126">[SaveFileDialog 元件](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) </span><span class="sxs-lookup"><span data-stu-id="cee2a-126">[SaveFileDialog Component](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) </span></span>  
 [<span data-ttu-id="cee2a-127">從檔案讀取</span><span class="sxs-lookup"><span data-stu-id="cee2a-127">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)

