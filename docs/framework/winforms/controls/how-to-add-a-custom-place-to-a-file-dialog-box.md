---
title: 如何：將自訂位置新增至檔案對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 824c948fafd0a0995ad261389414d2d79918c8a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916343"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="e34e2-102">如何：將自訂位置新增至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="e34e2-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="e34e2-103">[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] 上的預設開啟和儲存對話方塊，在 [最愛的連結] 對話方塊左側有一個區域。</span><span class="sxs-lookup"><span data-stu-id="e34e2-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="e34e2-104">這個區域稱為自訂位置。</span><span class="sxs-lookup"><span data-stu-id="e34e2-104">This area is called custom places.</span></span> <span data-ttu-id="e34e2-105">和類別可讓您將資料夾新增至<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>集合。 <xref:System.Windows.Forms.SaveFileDialog> <xref:System.Windows.Forms.OpenFileDialog></span><span class="sxs-lookup"><span data-stu-id="e34e2-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e34e2-106">為了讓自訂位置出現<xref:System.Windows.Forms.OpenFileDialog>在或<xref:System.Windows.Forms.SaveFileDialog>中, <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性必須設定為`true` (預設值)。</span><span class="sxs-lookup"><span data-stu-id="e34e2-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="e34e2-107">將自訂位置新增至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="e34e2-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="e34e2-108">將路徑、已知的資料夾 GUID 或<xref:System.Windows.Forms.FileDialogCustomPlace>物件新增<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>至對話方塊的集合。</span><span class="sxs-lookup"><span data-stu-id="e34e2-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="e34e2-109">下列程式碼範例示範如何新增路徑：</span><span class="sxs-lookup"><span data-stu-id="e34e2-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e34e2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e34e2-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e34e2-111">檔案對話方塊自訂位置的已知資料夾 GUID</span><span class="sxs-lookup"><span data-stu-id="e34e2-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
