---
title: "如何：在 Visual Basic 中以 StreamWriter 將文字寫入檔案"
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
- files, writing to
- text, writing to files
- writing to files, StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: 14
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
ms.openlocfilehash: ea85d57e9af4fdd640733db5dc2fa8b0ab25325c
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="61714-102">如何：在 Visual Basic 中以 StreamWriter 將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="61714-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="61714-103">此範例使用 `My.Computer.FileSystem.OpenTextFileWriter` 方法開啟 <xref:System.IO.StreamWriter> 物件，然後使用該物件搭配 <xref:System.IO.StreamWriter> 類別的 <xref:System.IO.TextWriter.WriteLine%2A> 方法，將字串寫入文字檔。</span><span class="sxs-lookup"><span data-stu-id="61714-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61714-104">範例</span><span class="sxs-lookup"><span data-stu-id="61714-104">Example</span></span>  
 <span data-ttu-id="61714-105">[!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="61714-105">[!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="61714-106">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="61714-106">Robust Programming</span></span>  
 <span data-ttu-id="61714-107">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="61714-107">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="61714-108">該檔案存在且為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="61714-108">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="61714-109">磁碟已滿 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="61714-109">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="61714-110">路徑名稱太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="61714-110">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="61714-111">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="61714-111">.NET Framework Security</span></span>  
 <span data-ttu-id="61714-112">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="61714-112">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="61714-113">如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="61714-113">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="61714-114">如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="61714-114">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="61714-115">若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。</span><span class="sxs-lookup"><span data-stu-id="61714-115">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61714-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61714-116">See Also</span></span>  
 <span data-ttu-id="61714-117"><xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="61714-117"><xref:System.IO.StreamWriter></span></span>   
 <span data-ttu-id="61714-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span><span class="sxs-lookup"><span data-stu-id="61714-118"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A></span></span>   
 <span data-ttu-id="61714-119">[如何：從文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md) </span><span class="sxs-lookup"><span data-stu-id="61714-119">[How to: Read from Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md) </span></span>  
 [<span data-ttu-id="61714-120">寫入檔案</span><span class="sxs-lookup"><span data-stu-id="61714-120">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)

