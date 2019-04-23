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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>如何：將自訂位置新增至檔案對話方塊
[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] 上的預設開啟和儲存對話方塊，在 [最愛的連結] 對話方塊左側有一個區域。 這個區域稱為自訂位置。 <xref:System.Windows.Forms.OpenFileDialog>並<xref:System.Windows.Forms.SaveFileDialog>類別可讓您加入資料夾來<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>集合。  
  
> [!NOTE]
>  為了讓自訂的位置，才會出現在<xref:System.Windows.Forms.OpenFileDialog>或是<xref:System.Windows.Forms.SaveFileDialog>，則<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性必須設為`true`（預設值）。  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>將自訂位置新增至檔案對話方塊  
  
-   新增路徑時，已知資料夾 GUID，或<xref:System.Windows.Forms.FileDialogCustomPlace>物件至<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>對話方塊中的集合。  
  
     下列程式碼範例示範如何新增路徑：  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [檔案對話方塊自訂位置的已知資料夾 GUID](known-folder-guids-for-file-dialog-custom-places.md)
