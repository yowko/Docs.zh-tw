---
title: 作法：在 Visual Basic 中將文字寫入檔案
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic]
- examples [Visual Basic], text files
ms.assetid: 304956eb-530d-4df7-b48f-9b4d1f2581a0
ms.openlocfilehash: 7862e9b471808c2d01771acacefef15bdb31dda5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975065"
---
# <a name="how-to-write-text-to-files-in-visual-basic"></a><span data-ttu-id="7e1eb-102">HOW TO：在 Visual Basic 中將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="7e1eb-102">How to: Write Text to Files in Visual Basic</span></span>
<span data-ttu-id="7e1eb-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> 方法可用來將文字寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method can be used to write text to files.</span></span> <span data-ttu-id="7e1eb-104">如果指定的檔案不存在，則會建立該檔案。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-104">If the specified file does not exist, it is created.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="7e1eb-105">程序</span><span class="sxs-lookup"><span data-stu-id="7e1eb-105">Procedure</span></span>  
  
#### <a name="to-write-text-to-a-file"></a><span data-ttu-id="7e1eb-106">將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="7e1eb-106">To write text to a file</span></span>  
  
-   <span data-ttu-id="7e1eb-107">使用 `WriteAllText` 方法，將文字寫入檔案中，並指定要寫入的檔案和文字。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-107">Use the `WriteAllText` method to write text to a file, specifying the file and text to be written.</span></span> <span data-ttu-id="7e1eb-108">這個範例會將 `"This is new text."` 行寫入名為 `test.txt` 的檔案，並將文字附加至檔案中的任何現有文字。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-108">This example writes the line `"This is new text."` to the file named `test.txt`, appending the text to any existing text in the file.</span></span>  
  
     [!code-vb[VbFileIOWrite#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#3)]  
  
#### <a name="to-write-a-series-of-strings-to-a-file"></a><span data-ttu-id="7e1eb-109">將一連串的字串寫入檔案</span><span class="sxs-lookup"><span data-stu-id="7e1eb-109">To write a series of strings to a file</span></span>  
  
-   <span data-ttu-id="7e1eb-110">反覆執行字串集合。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-110">Loop through the string collection.</span></span> <span data-ttu-id="7e1eb-111">使用 `WriteAllText` 方法，將文字寫入檔案，並指定要新增的目標檔案和字串以及將 `append` 設定為 `True`。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-111">Use the `WriteAllText` method to write text to a file, specifying the target file and string to be added and setting `append` to `True`.</span></span>  
  
     <span data-ttu-id="7e1eb-112">這個範例會將 `Documents and Settings` 目錄中的檔案名稱寫入 `FileList.txt`，並在每個之間插入換行符號，以增加可讀性。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-112">This example writes the names of the files in the `Documents and Settings` directory to `FileList.txt`, inserting a carriage return between each for better readability.</span></span>  
  
     [!code-vb[VbFileIOWrite#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#4)]  
  
## <a name="robust-programming"></a><span data-ttu-id="7e1eb-113">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="7e1eb-113">Robust Programming</span></span>  
 <span data-ttu-id="7e1eb-114">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="7e1eb-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="7e1eb-115">因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-115">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="7e1eb-116">路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-116">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="7e1eb-117">`File` 指向不存在的路徑 (<xref:System.IO.FileNotFoundException> 或 <xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-117">`File` points to a path that does not exist (<xref:System.IO.FileNotFoundException> or <xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="7e1eb-118">檔案正由另一個處理序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-118">The file is in use by another process, or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="7e1eb-119">路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="7e1eb-120">路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="7e1eb-121">使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="7e1eb-122">磁碟已滿，且 `WriteAllText` 的呼叫失敗 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-122">The disk is full, and the call to `WriteAllText` fails (<xref:System.IO.IOException>).</span></span>  
  
 <span data-ttu-id="7e1eb-123">如果要在部分信任內容中執行，則程式碼可能會因權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-123">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="7e1eb-124">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="7e1eb-124">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e1eb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e1eb-125">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- [<span data-ttu-id="7e1eb-126">如何：從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="7e1eb-126">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
