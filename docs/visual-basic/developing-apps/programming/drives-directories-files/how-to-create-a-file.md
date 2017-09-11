---
title: "如何：在 Visual Basic 中建立檔案"
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
- text files, creating
- files, creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
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
ms.openlocfilehash: d06d274b31afad0a437405d1679e0be7548f2e14
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="a202b-102">如何：在 Visual Basic 中建立檔案</span><span class="sxs-lookup"><span data-stu-id="a202b-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="a202b-103">這個範例會在 <xref:System.IO.File> 類別中使用 <xref:System.IO.File.Create%2A> 方法，以在指定的路徑中建立空白文字檔。</span><span class="sxs-lookup"><span data-stu-id="a202b-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a202b-104">範例</span><span class="sxs-lookup"><span data-stu-id="a202b-104">Example</span></span>  
 <span data-ttu-id="a202b-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a202b-105">[!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a202b-106">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a202b-106">Compiling the Code</span></span>  
 <span data-ttu-id="a202b-107">使用 `file` 變數，以寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="a202b-107">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a202b-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="a202b-108">Robust Programming</span></span>  
 <span data-ttu-id="a202b-109">如果檔案已存在，則會予以取代。</span><span class="sxs-lookup"><span data-stu-id="a202b-109">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="a202b-110">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="a202b-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a202b-111">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="a202b-111">The path name is malformed.</span></span> <span data-ttu-id="a202b-112">例如，它包含不合法的字元，或只有空白字元 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="a202b-112">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="a202b-113">路徑為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="a202b-113">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="a202b-114">路徑名稱是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="a202b-114">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="a202b-115">路徑名稱太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="a202b-115">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="a202b-116">路徑無效 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="a202b-116">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="a202b-117">此路徑只是一個冒號 ":" (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="a202b-117">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a202b-118">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="a202b-118">.NET Framework Security</span></span>  
 <span data-ttu-id="a202b-119">在部分信任環境中，可能會擲回 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="a202b-119">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="a202b-120"><xref:System.IO.File.Create%2A> 方法呼叫需要 <xref:System.Security.Permissions.FileIOPermission>。</span><span class="sxs-lookup"><span data-stu-id="a202b-120">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="a202b-121">如果使用者無權建立檔案，則會擲回 <xref:System.UnauthorizedAccessException>。</span><span class="sxs-lookup"><span data-stu-id="a202b-121">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a202b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a202b-122">See Also</span></span>  
 <span data-ttu-id="a202b-123"><xref:System.IO></span><span class="sxs-lookup"><span data-stu-id="a202b-123"><xref:System.IO></span></span>   
 <span data-ttu-id="a202b-124"><xref:System.IO.File.Create%2A></span><span class="sxs-lookup"><span data-stu-id="a202b-124"><xref:System.IO.File.Create%2A></span></span>   
 <span data-ttu-id="a202b-125">[從部分受信任程式碼使用程式庫](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span><span class="sxs-lookup"><span data-stu-id="a202b-125">[Using Libraries from Partially Trusted Code](../../../../framework/misc/using-libraries-from-partially-trusted-code.md) </span></span>  
 [<span data-ttu-id="a202b-126">程式碼存取安全性的基本概念</span><span class="sxs-lookup"><span data-stu-id="a202b-126">Code Access Security Basics</span></span>](https://msdn.microsoft.com/library/33tceax8)

