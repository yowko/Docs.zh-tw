---
title: "如何：將自訂位置加入至檔案對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "自訂位置至對話方塊"
  - "將自訂位置加入至對話方塊"
  - "CustomPlaces 集合"
ms.assetid: 63f6469b-59cd-40f6-9e61-8b5831856780
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：將自訂位置加入至檔案對話方塊
預設會開啟並儲存在檔案對話方塊[!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)]有標題為對話方塊左側的區域**我的最愛連結**。 這個區域稱為自訂位置。 <xref:System.Windows.Forms.OpenFileDialog>和<xref:System.Windows.Forms.SaveFileDialog>類別可讓您加入資料夾來<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>集合。  
  
> [!NOTE]
>  為了讓自訂的位置，才會出現在<xref:System.Windows.Forms.OpenFileDialog>或<xref:System.Windows.Forms.SaveFileDialog>、 <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A>屬性必須設為`true`（預設值）。  
  
### <a name="to-add-a-custom-place-to-a-file-dialog-box"></a>若要將自訂位置加入至檔案對話方塊  
  
-   新增路徑時，已知資料夾 GUID 或<xref:System.Windows.Forms.FileDialogCustomPlace>物件傳遞給<xref:System.Windows.Forms.FileDialog.CustomPlaces%2A>對話框的集合。  
  
     下列程式碼範例示範如何加入路徑︰  
  
    ```vb  
    OpenFileDialog1.CustomPlaces.Add("C:\MyCustomPlace")  
    ```  
  
    ```csharp  
    openFileDialog1.CustomPlaces.Add("C:\\MyCustomPlace");  
    ```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FileDialog>   
 <xref:System.Windows.Forms.FileDialogCustomPlacesCollection.Add%2A?displayProperty=fullName>   
 [檔案對話方塊自訂位置的已知資料夾 Guid](../../../../docs/framework/winforms/controls/known-folder-guids-for-file-dialog-custom-places.md)