---
title: HOW TO：在 Visual Basic 中以 StreamWriter 將文字寫入檔案
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: ca792106bdd341fa4be8f3554ce70cd7d3f22522
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816064"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="8a9b4-102">HOW TO：在 Visual Basic 中以 StreamWriter 將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="8a9b4-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="8a9b4-103">此範例使用 `My.Computer.FileSystem.OpenTextFileWriter` 方法開啟 <xref:System.IO.StreamWriter> 物件，然後使用該物件搭配 <xref:System.IO.StreamWriter> 類別的 <xref:System.IO.TextWriter.WriteLine%2A> 方法，將字串寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a9b4-104">範例</span><span class="sxs-lookup"><span data-stu-id="8a9b4-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8a9b4-105">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="8a9b4-105">Robust Programming</span></span>  
 <span data-ttu-id="8a9b4-106">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="8a9b4-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="8a9b4-107">該檔案存在且為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="8a9b4-108">磁碟已滿 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="8a9b4-109">路徑名稱太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8a9b4-110">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="8a9b4-110">.NET Framework Security</span></span>  
 <span data-ttu-id="8a9b4-111">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="8a9b4-112">如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="8a9b4-113">如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="8a9b4-114">若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="8a9b4-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a9b4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a9b4-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="8a9b4-116">如何：從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="8a9b4-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="8a9b4-117">寫入檔案</span><span class="sxs-lookup"><span data-stu-id="8a9b4-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
