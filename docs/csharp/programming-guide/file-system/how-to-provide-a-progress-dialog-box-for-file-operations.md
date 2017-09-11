---
title: "如何：提供檔案作業的進度對話方塊 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 1d2b0ecf2886e6bda5b605b9e8976e1647d593fa
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a><span data-ttu-id="43f4e-102">如何：提供檔案作業的進度對話方塊 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="43f4e-102">How to: Provide a Progress Dialog Box for File Operations (C# Programming Guide)</span></span>
<span data-ttu-id="43f4e-103">如果您使用 <xref:Microsoft.VisualBasic?displayProperty=fullName> 命名空間中的 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> 方法，則可以提供標準對話方塊來顯示 Windows 中檔案作業的進度。</span><span class="sxs-lookup"><span data-stu-id="43f4e-103">You can provide a standard dialog box that shows progress on file operations in Windows if you use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> method in the <xref:Microsoft.VisualBasic?displayProperty=fullName> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a><span data-ttu-id="43f4e-104">在 Visual Studio 中加入參考</span><span class="sxs-lookup"><span data-stu-id="43f4e-104">To add a reference in Visual Studio</span></span>  
  
1.  <span data-ttu-id="43f4e-105">在功能表列上，選擇 **[專案]**、**[加入參考]**。</span><span class="sxs-lookup"><span data-stu-id="43f4e-105">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="43f4e-106">**[參考管理員]** 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="43f4e-106">The **Reference Manager** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="43f4e-107">在 **[組件]** 區域中，選擇 **[架構]** (如果尚未選擇)。</span><span class="sxs-lookup"><span data-stu-id="43f4e-107">In the **Assemblies** area, choose**Framework** if it isn’t already chosen.</span></span>  
  
3.  <span data-ttu-id="43f4e-108">在名稱清單中，選取 **[Microsoft.VisualBasic]**核取方塊，然後選擇 **[確定]** 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="43f4e-108">In the list of names, select the **Microsoft.VisualBasic** check box, and then choose the **OK** button to close the dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43f4e-109">範例</span><span class="sxs-lookup"><span data-stu-id="43f4e-109">Example</span></span>  
 <span data-ttu-id="43f4e-110">下列程式碼會將 `sourcePath` 指定的目錄複製到 `destinationPath` 指定的目錄。</span><span class="sxs-lookup"><span data-stu-id="43f4e-110">The following code copies the directory that `sourcePath` specifies into the directory that `destinationPath` specifies.</span></span> <span data-ttu-id="43f4e-111">此程式碼也會提供標準對話方塊，來顯示作業完成前的預估剩餘時間量。</span><span class="sxs-lookup"><span data-stu-id="43f4e-111">This code also provides a standard dialog box that shows the estimated amount of time remaining before the operation finishes.</span></span>  
  
 <span data-ttu-id="43f4e-112">[!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="43f4e-112">[!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f4e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43f4e-113">See Also</span></span>  
 [<span data-ttu-id="43f4e-114">檔案系統和登錄 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="43f4e-114">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
