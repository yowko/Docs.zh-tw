---
title: 作法：在 Visual Basic 中擷取 [我的文件] 目錄的內容
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: 6d4e0bc7d300b2553d5286600cc65b7c494359b9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964173"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="a94fe-102">作法：在 Visual Basic 中擷取 [我的文件] 目錄的內容</span><span class="sxs-lookup"><span data-stu-id="a94fe-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>
<span data-ttu-id="a94fe-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> 物件可以用來讀取許多 [所有使用者] 目錄，例如 [我的文件] 或 [桌面]。</span><span class="sxs-lookup"><span data-stu-id="a94fe-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="a94fe-104">讀取 [我的文件] 資料夾</span><span class="sxs-lookup"><span data-stu-id="a94fe-104">To read from the My Documents folder</span></span>  
  
-   <span data-ttu-id="a94fe-105">使用 `ReadAllText` 方法，讀取特定目錄中每個檔案的文字。</span><span class="sxs-lookup"><span data-stu-id="a94fe-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="a94fe-106">下列程式碼指定目錄和檔案，然後使用 `ReadAllText` 將它們讀入名為 `patients` 的字串。</span><span class="sxs-lookup"><span data-stu-id="a94fe-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a94fe-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a94fe-107">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
