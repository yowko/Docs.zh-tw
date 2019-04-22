---
title: HOW TO：在 Visual Basic 中建立檔案
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: a05e73a2096c82c9299e4483bbaf69e560fc2e45
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839414"
---
# <a name="how-to-create-a-file-in-visual-basic"></a><span data-ttu-id="40dc2-102">HOW TO：在 Visual Basic 中建立檔案</span><span class="sxs-lookup"><span data-stu-id="40dc2-102">How to: Create a File in Visual Basic</span></span>
<span data-ttu-id="40dc2-103">這個範例會在 <xref:System.IO.File> 類別中使用 <xref:System.IO.File.Create%2A> 方法，以在指定的路徑中建立空白文字檔。</span><span class="sxs-lookup"><span data-stu-id="40dc2-103">This example creates an empty text file at the specified path using the <xref:System.IO.File.Create%2A> method in the <xref:System.IO.File> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40dc2-104">範例</span><span class="sxs-lookup"><span data-stu-id="40dc2-104">Example</span></span>  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40dc2-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="40dc2-105">Compiling the Code</span></span>  
 <span data-ttu-id="40dc2-106">使用 `file` 變數，以寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="40dc2-106">Use the `file` variable to write to the file.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="40dc2-107">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="40dc2-107">Robust Programming</span></span>  
 <span data-ttu-id="40dc2-108">如果檔案已存在，則會予以取代。</span><span class="sxs-lookup"><span data-stu-id="40dc2-108">If the file already exists, it is replaced.</span></span>  
  
 <span data-ttu-id="40dc2-109">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="40dc2-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="40dc2-110">路徑名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="40dc2-110">The path name is malformed.</span></span> <span data-ttu-id="40dc2-111">例如，它包含不合法的字元，或只有空白字元 (<xref:System.ArgumentException>)。</span><span class="sxs-lookup"><span data-stu-id="40dc2-111">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="40dc2-112">路徑為唯讀 (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="40dc2-112">The path is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="40dc2-113">路徑名稱是 `Nothing` (<xref:System.ArgumentNullException>)。</span><span class="sxs-lookup"><span data-stu-id="40dc2-113">The path name is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="40dc2-114">路徑名稱太長 (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="40dc2-114">The path name is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="40dc2-115">路徑無效 (<xref:System.IO.DirectoryNotFoundException>)。</span><span class="sxs-lookup"><span data-stu-id="40dc2-115">The path is invalid (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="40dc2-116">此路徑只是一個冒號 ":" (<xref:System.NotSupportedException>)。</span><span class="sxs-lookup"><span data-stu-id="40dc2-116">The path is only a colon ":" (<xref:System.NotSupportedException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="40dc2-117">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="40dc2-117">.NET Framework Security</span></span>  
 <span data-ttu-id="40dc2-118">在部分信任環境中，可能會擲回 <xref:System.Security.SecurityException>。</span><span class="sxs-lookup"><span data-stu-id="40dc2-118">A <xref:System.Security.SecurityException> may be thrown in partial-trust environments.</span></span>  
  
 <span data-ttu-id="40dc2-119"><xref:System.IO.File.Create%2A> 方法呼叫需要 <xref:System.Security.Permissions.FileIOPermission>。</span><span class="sxs-lookup"><span data-stu-id="40dc2-119">The call to the <xref:System.IO.File.Create%2A> method requires <xref:System.Security.Permissions.FileIOPermission>.</span></span>  
  
 <span data-ttu-id="40dc2-120">如果使用者無權建立檔案，則會擲回 <xref:System.UnauthorizedAccessException>。</span><span class="sxs-lookup"><span data-stu-id="40dc2-120">An <xref:System.UnauthorizedAccessException> is thrown if the user does not have permission to create the file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40dc2-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="40dc2-121">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [<span data-ttu-id="40dc2-122">從部分受信任程式碼使用程式庫</span><span class="sxs-lookup"><span data-stu-id="40dc2-122">Using Libraries from Partially Trusted Code</span></span>](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [<span data-ttu-id="40dc2-123">程式碼存取安全性的基本概念</span><span class="sxs-lookup"><span data-stu-id="40dc2-123">Code Access Security Basics</span></span>](../../../../framework/misc/code-access-security-basics.md)
