---
title: "如何：將自訂位置加入至檔案對話方塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ce5efccfd2efda2f333b51868e375849f7c7752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="da8ab-102">如何：將自訂位置加入至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="da8ab-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="da8ab-103">[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] 上的預設開啟和儲存對話方塊，在 [最愛的連結] 對話方塊左側有一個區域。</span><span class="sxs-lookup"><span data-stu-id="da8ab-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="da8ab-104">這個區域稱為自訂位置。</span><span class="sxs-lookup"><span data-stu-id="da8ab-104">This area is called custom places.</span></span> <span data-ttu-id="da8ab-105"><xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>類別可讓您加入資料夾來<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="da8ab-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da8ab-106">為了讓自訂的位置，才會出現在<xref:System.Windows.Forms.OpenFileDialog>或<xref:System.Windows.Forms.SaveFileDialog>、<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性必須設定為`true`（預設值）。</span><span class="sxs-lookup"><span data-stu-id="da8ab-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="da8ab-107">將自訂位置新增至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="da8ab-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="da8ab-108">新增已知資料夾 GUID 路徑，或<xref:System.Windows.Forms.FileDialogCustomPlace>物件<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>對話框的集合。</span><span class="sxs-lookup"><span data-stu-id="da8ab-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="da8ab-109">下列程式碼範例示範如何新增路徑：</span><span class="sxs-lookup"><span data-stu-id="da8ab-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="da8ab-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da8ab-110">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>  
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="da8ab-111">檔案對話方塊自訂位置的已知資料夾 GUID</span><span class="sxs-lookup"><span data-stu-id="da8ab-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)
