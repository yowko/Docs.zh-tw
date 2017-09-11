---
title: "如何：在 Visual Basic 中將文字寫入我的文件目錄中的檔案"
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
- examples [Visual Basic], text files
- writing to files, in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: 19
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
ms.openlocfilehash: c900072d184469ead75bb76a3e152edce357a34f
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="1c7e4-102">如何：在 Visual Basic 中將文字寫入我的文件目錄中的檔案</span><span class="sxs-lookup"><span data-stu-id="1c7e4-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="1c7e4-103">`My.Computer.FileSystem.SpecialDirectories` 物件可讓您存取特殊目錄，例如 [我的文件] 目錄。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="1c7e4-104">程序</span><span class="sxs-lookup"><span data-stu-id="1c7e4-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="1c7e4-105">將新文字檔寫入 [我的文件] 目錄中</span><span class="sxs-lookup"><span data-stu-id="1c7e4-105">To write new text files in the My Documents directory</span></span>  
  
1.  <span data-ttu-id="1c7e4-106">使用 `My.Computer.FileSystem.SpecialDirectories.MyDocuments` 屬性，來提供路徑。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     <span data-ttu-id="1c7e4-107">[!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="1c7e4-107">[!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]</span></span>  
  
2.  <span data-ttu-id="1c7e4-108">使用 `WriteAllText` 方法，將文字寫入指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-108">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     <span data-ttu-id="1c7e4-109">[!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="1c7e4-109">[!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c7e4-110">範例</span><span class="sxs-lookup"><span data-stu-id="1c7e4-110">Example</span></span>  
 <span data-ttu-id="1c7e4-111">[!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="1c7e4-111">[!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1c7e4-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="1c7e4-112">Compiling the Code</span></span>  
 <span data-ttu-id="1c7e4-113">請將 `test.txt` 取代為您想要寫入之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-113">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1c7e4-114">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="1c7e4-114">Robust Programming</span></span>  
 <span data-ttu-id="1c7e4-115">這個程式碼會重新擲回將文字寫入檔案時可能發生的所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-115">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="1c7e4-116">使用 [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) 和 [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) 元件這類 Windows Forms 控制項以將使用者選項限制為有效檔案名稱，即可減少例外狀況的可能性。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-116">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](../../../../framework/winforms/controls/openfiledialog-component-windows-forms.md) and the [SaveFileDialog](../../../../framework/winforms/controls/savefiledialog-component-windows-forms.md) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="1c7e4-117">不過，使用這些控制項並不容易。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-117">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="1c7e4-118">在使用者選取檔案的時間與程式碼執行的時間之間，可以變更檔案系統。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-118">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="1c7e4-119">因此，使用檔案時，幾乎一律都需要進行例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-119">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="1c7e4-120">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="1c7e4-120">.NET Framework Security</span></span>  
 <span data-ttu-id="1c7e4-121">如果要在部分信任內容中執行，則程式碼可能會因權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-121">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="1c7e4-122">如需詳細資訊，請參閱[程式碼存取安全性基本概念](https://msdn.microsoft.com/library/33tceax8)。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-122">For more information, see [Code Access Security Basics](https://msdn.microsoft.com/library/33tceax8).</span></span>  
  
 <span data-ttu-id="1c7e4-123">這個範例會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-123">This example creates a new file.</span></span> <span data-ttu-id="1c7e4-124">如果應用程式需要建立檔案，該應用程式就需要資料夾的 [建立] 權限。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-124">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="1c7e4-125">您可以使用存取控制清單來設定權限。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="1c7e4-126">如果檔案已經存在，則應用程式只需要 [寫入] 權限，這是較小的權限。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-126">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="1c7e4-127">若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 [讀取] 權限，而不授與資料夾的 [建立] 權限。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-127">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="1c7e4-128">此外，將資料寫入使用者資料夾，而不是根資料夾或 **Program Files** 資料夾，也更加安全。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-128">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="1c7e4-129">如需詳細資訊，請參閱 [ACL 技術概觀](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045)。</span><span class="sxs-lookup"><span data-stu-id="1c7e4-129">For more information, see [ACL Technology Overview](http://msdn.microsoft.com/en-us/06fbf66d-6f02-4378-b863-b2f12e349045).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c7e4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c7e4-130">See Also</span></span>  
 <xref:System.IO.Path.Combine%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>

