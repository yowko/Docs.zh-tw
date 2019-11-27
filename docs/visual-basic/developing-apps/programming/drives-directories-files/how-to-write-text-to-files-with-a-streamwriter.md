---
title: 如何：以 StreamWriter 將文字寫入檔案
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
ms.openlocfilehash: 869e29263abcdd8525b2c372c7bb466e3e21fc65
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334490"
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="cc1ef-102">如何：在 Visual Basic 中以 StreamWriter 將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="cc1ef-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>

<span data-ttu-id="cc1ef-103">此範例使用 <xref:System.IO.StreamWriter> 方法開啟 `My.Computer.FileSystem.OpenTextFileWriter` 物件，然後使用該物件搭配 <xref:System.IO.TextWriter.WriteLine%2A> 類別的 <xref:System.IO.StreamWriter> 方法，將字串寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc1ef-104">範例</span><span class="sxs-lookup"><span data-stu-id="cc1ef-104">Example</span></span>  

 [!code-vb[VbFileIOWrite#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#5)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cc1ef-105">最佳化程式設計</span><span class="sxs-lookup"><span data-stu-id="cc1ef-105">Robust Programming</span></span>  

 <span data-ttu-id="cc1ef-106">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="cc1ef-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cc1ef-107">該檔案存在且為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cc1ef-108">磁碟已滿 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="cc1ef-109">路徑名稱太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="cc1ef-110">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="cc1ef-110">.NET Framework Security</span></span>  

 <span data-ttu-id="cc1ef-111">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="cc1ef-112">如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="cc1ef-113">如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="cc1ef-114">若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="cc1ef-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc1ef-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc1ef-115">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>
- [<span data-ttu-id="cc1ef-116">如何：從文字檔讀取</span><span class="sxs-lookup"><span data-stu-id="cc1ef-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)
- [<span data-ttu-id="cc1ef-117">寫入檔案</span><span class="sxs-lookup"><span data-stu-id="cc1ef-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
