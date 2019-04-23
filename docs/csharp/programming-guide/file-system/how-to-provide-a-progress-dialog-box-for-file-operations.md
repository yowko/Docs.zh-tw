---
title: HOW TO：提供檔案作業的進度對話方塊 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 882e4ea71331fe0513f3be71c371bbc0f714b44f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59309533"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="3233d-102">HOW TO：提供檔案作業的進度對話方塊 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3233d-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="3233d-103">如果您在 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 命名空間中使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> 方法，則可以提供標準對話方塊，以在 Windows 中顯示檔案作業進度。</span><span class="sxs-lookup"><span data-stu-id="3233d-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="3233d-104">在 Visual Studio 中加入參考</span><span class="sxs-lookup"><span data-stu-id="3233d-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="3233d-105">在功能表列上，選擇 **[專案]**、**[加入參考]**。</span><span class="sxs-lookup"><span data-stu-id="3233d-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="3233d-106">[參考管理員] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="3233d-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="3233d-107">在 [組件] 區域中，選擇 [Framework] (如果尚未選擇)。</span><span class="sxs-lookup"><span data-stu-id="3233d-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="3233d-108">在名稱清單中，選取 **[Microsoft.VisualBasic]** 核取方塊，然後選擇 **[確定]** 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="3233d-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3233d-109">範例</span><span class="sxs-lookup"><span data-stu-id="3233d-109">Example</span></span>  
 <span data-ttu-id="3233d-110">下列程式碼會將 `sourcePath` 指定的目錄複製到 `destinationPath` 指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="3233d-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="3233d-111">此程式碼也會提供標準對話方塊，來顯示作業完成前的預估剩餘時間量。</span><span class="sxs-lookup"><span data-stu-id="3233d-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3233d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3233d-112">See also</span></span>

- [<span data-ttu-id="3233d-113">檔案系統和登錄 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="3233d-113">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
