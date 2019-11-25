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
# <a name="how-to-add-a-custom-place-to-a-file-dialog-box"></a>如何：將自訂位置加入至檔案對話方塊
Windows Vista 上預設的 [開啟] 和 [儲存] 對話方塊，在標題為 [我的**最愛連結**] 的對話方塊左邊有一個區域。 這個區域稱為自訂位置。 [<xref:System.Windows.Forms.OpenFileDialog>] 和 [<xref:System.Windows.Forms.SaveFileDialog>] 類別可讓您將資料夾新增至 <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> 集合。  
  
> [!NOTE]
> 為了讓自訂位置出現在 <xref:System.Windows.Forms.OpenFileDialog> 或 <xref:System.Windows.Forms.SaveFileDialog>中，<xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> 屬性必須設定為 `true` （預設值）。  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>將自訂位置新增至檔案對話方塊  
  
- 將路徑、已知的資料夾 GUID 或 <xref:System.Windows.Forms.FileDialogCustomPlace> 物件新增至對話方塊的 <xref:System.Windows.Forms.FileDialog.CustomPlaces%2A> 集合。  
  
     下列程式碼範例示範如何新增路徑：  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>請參閱

- <xref:System.Windows.Forms.FileDialog>
- <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=nameWithType>
- [檔案對話方塊自訂位置的已知資料夾 GUID](known-folder-guids-for-file-dialog-custom-places.md)
