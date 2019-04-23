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
ms.openlocfilehash: 79836dd260cb13912ccba43cfb4a0a3e0ad195fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087679"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="983c7-102">如何：將自訂位置新增至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="983c7-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="983c7-103">[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] 上的預設開啟和儲存對話方塊，在 [最愛的連結] 對話方塊左側有一個區域。</span><span class="sxs-lookup"><span data-stu-id="983c7-103">The default open and save dialog boxes on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="983c7-104">這個區域稱為自訂位置。</span><span class="sxs-lookup"><span data-stu-id="983c7-104">This area is called custom places.</span></span> <span data-ttu-id="983c7-105"><xref:System.Windows.Forms.OpenFileDialog>並<xref:System.Windows.Forms.SaveFileDialog>類別可讓您加入資料夾來<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>集合。</span><span class="sxs-lookup"><span data-stu-id="983c7-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="983c7-106">為了讓自訂的位置，才會出現在<xref:System.Windows.Forms.OpenFileDialog>或是<xref:System.Windows.Forms.SaveFileDialog>，則<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性必須設為`true`（預設值）。</span><span class="sxs-lookup"><span data-stu-id="983c7-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="983c7-107">將自訂位置新增至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="983c7-107">To add a custom place to a file dialog box</span></span>  
  
-   <span data-ttu-id="983c7-108">新增路徑時，已知資料夾 GUID，或<xref:System.Windows.Forms.FileDialogCustomPlace>物件至<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>對話方塊中的集合。</span><span class="sxs-lookup"><span data-stu-id="983c7-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="983c7-109">下列程式碼範例示範如何新增路徑：</span><span class="sxs-lookup"><span data-stu-id="983c7-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="983c7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="983c7-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="983c7-111">檔案對話方塊自訂位置的已知資料夾 GUID</span><span class="sxs-lookup"><span data-stu-id="983c7-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
