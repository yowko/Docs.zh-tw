---
title: 如何為檔操作提供進度對話方塊 - C# 程式設計指南
ms.date: 07/20/2015
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
ms.openlocfilehash: 30ab84054d26f5b32a3f042a8d35d5ef1211d928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705128"
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="ada22-102">如何為檔操作提供進度對話方塊（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="ada22-102">How to provide a progress dialog box for file operations (C# Programming Guide)</span></span>
<span data-ttu-id="ada22-103">如果您在 <xref:Microsoft.VisualBasic?displayProperty=nameWithType> 命名空間中使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> 方法，則可以提供標準對話方塊，以在 Windows 中顯示檔案作業進度。</span><span class="sxs-lookup"><span data-stu-id="ada22-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="ada22-104">在 Visual Studio 中加入參考</span><span class="sxs-lookup"><span data-stu-id="ada22-104">To add a reference in Visual Studio</span></span>  
  
1. <span data-ttu-id="ada22-105">在功能表列上，選擇 **[專案]**、**[加入參考]**。</span><span class="sxs-lookup"><span data-stu-id="ada22-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="ada22-106">[參考管理員]\*\*\*\* 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="ada22-106">The **Reference Manager** dialog box appears.</span></span>  
  
2. <span data-ttu-id="ada22-107">在 [組件]\*\*\*\* 區域中，選擇 [Framework]\*\*\*\* (如果尚未選擇)。</span><span class="sxs-lookup"><span data-stu-id="ada22-107">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
3. <span data-ttu-id="ada22-108">在名稱清單中，選取 **[Microsoft.VisualBasic]** 核取方塊，然後選擇 **[確定]** 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ada22-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ada22-109">範例</span><span class="sxs-lookup"><span data-stu-id="ada22-109">Example</span></span>  
 <span data-ttu-id="ada22-110">下列程式碼會將 `sourcePath` 指定的目錄複製到 `destinationPath` 指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="ada22-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="ada22-111">此程式碼也會提供標準對話方塊，來顯示作業完成前的預估剩餘時間量。</span><span class="sxs-lookup"><span data-stu-id="ada22-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 [!code-csharp[csFilesandFolders#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ada22-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ada22-112">See also</span></span>

- [<span data-ttu-id="ada22-113">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="ada22-113">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
