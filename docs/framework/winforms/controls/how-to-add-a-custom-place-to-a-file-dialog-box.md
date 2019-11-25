---
title: 如何：將自訂位置加入至檔案對話方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Custom Place to dialog box
- adding Custom Place to dialog box
- CustomPlaces collection
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
ms.openlocfilehash: 7172e484451cf932413920910ec9124b3388bd76
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976995"
---
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="8aca3-102">如何：將自訂位置加入至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="8aca3-102">How To: Add a Custom Place to a File Dialog Box</span></span>
<span data-ttu-id="8aca3-103">Windows Vista 上預設的 [開啟] 和 [儲存] 對話方塊，在標題為 [我的**最愛連結**] 的對話方塊左邊有一個區域。</span><span class="sxs-lookup"><span data-stu-id="8aca3-103">The default open and save dialog boxes on Windows Vista have an area on the left side of the dialog box titled **Favorite Links**.</span></span> <span data-ttu-id="8aca3-104">這個區域稱為自訂位置。</span><span class="sxs-lookup"><span data-stu-id="8aca3-104">This area is called custom places.</span></span> <span data-ttu-id="8aca3-105">[<xref:System.Windows.Forms.OpenFileDialog>] 和 [<xref:System.Windows.Forms.SaveFileDialog>] 類別可讓您將資料夾新增至 <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="8aca3-105">The <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes allow you to add folders to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8aca3-106">為了讓自訂位置出現在 <xref:System.Windows.Forms.OpenFileDialog> 或 <xref:System.Windows.Forms.SaveFileDialog>中，<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> 屬性必須設定為 `true` （預設值）。</span><span class="sxs-lookup"><span data-stu-id="8aca3-106">In order for a custom place to appear in the <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog>, the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property must be set to `true` (the default).</span></span>  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a><span data-ttu-id="8aca3-107">將自訂位置新增至檔案對話方塊</span><span class="sxs-lookup"><span data-stu-id="8aca3-107">To add a custom place to a file dialog box</span></span>  
  
- <span data-ttu-id="8aca3-108">將路徑、已知的資料夾 GUID 或 <xref:System.Windows.Forms.FileDialogCustomPlace> 物件新增至對話方塊的 <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> 集合。</span><span class="sxs-lookup"><span data-stu-id="8aca3-108">Add a path, a Known Folder GUID, or a <xref:System.Windows.Forms.FileDialogCustomPlace> object to the <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> collection of the dialog box.</span></span>  
  
     <span data-ttu-id="8aca3-109">下列程式碼範例示範如何新增路徑：</span><span class="sxs-lookup"><span data-stu-id="8aca3-109">The following code example shows how to add a path:</span></span>  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8aca3-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="8aca3-110">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8aca3-111">檔案對話方塊自訂位置的已知資料夾 GUID</span><span class="sxs-lookup"><span data-stu-id="8aca3-111">Known Folder GUIDs for File Dialog Custom Places</span></span>](known-folder-guids-for-file-dialog-custom-places.md)
