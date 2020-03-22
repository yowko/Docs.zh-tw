---
title: 如何：擷取我的文件目錄的內容
ms.date: 07/20/2015
helpviewer_keywords:
- My Documents directory
ms.assetid: 26560d01-7dda-4457-8e95-21db23d71aea
ms.openlocfilehash: cf4470020507c581999b9d72602ddb6e3e76ed74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334541"
---
# <a name="how-to-retrieve-the-contents-of-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="90ee7-102">如何：在 Visual Basic 中擷取我的文件目錄的內容</span><span class="sxs-lookup"><span data-stu-id="90ee7-102">How to: Retrieve the Contents of the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="90ee7-103"><xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> 物件可以用來讀取許多 [所有使用者]\*\*\*\* 目錄，例如 [我的文件]\*\*\*\* 或 [桌面]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="90ee7-103">The <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories> object can be used to read from many of the **All Users** directories, such as **My Documents** or **Desktop**.</span></span>  
  
### <a name="to-read-from-the-my-documents-folder"></a><span data-ttu-id="90ee7-104">讀取 [我的文件] 資料夾</span><span class="sxs-lookup"><span data-stu-id="90ee7-104">To read from the My Documents folder</span></span>  
  
- <span data-ttu-id="90ee7-105">使用 `ReadAllText` 方法，讀取特定目錄中每個檔案的文字。</span><span class="sxs-lookup"><span data-stu-id="90ee7-105">Use the `ReadAllText` method to read the text from each file in a specific directory.</span></span> <span data-ttu-id="90ee7-106">下列程式碼指定目錄和檔案，然後使用 `ReadAllText` 將它們讀入名為 `patients` 的字串。</span><span class="sxs-lookup"><span data-stu-id="90ee7-106">The following code specifies a directory and file and then uses `ReadAllText` to read them into the string named `patients`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="90ee7-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90ee7-107">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
