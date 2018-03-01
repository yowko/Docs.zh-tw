---
title: "如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d795df8e8b514345632491fd6afdd618c2f18ec2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar
Windows Form<xref:System.Windows.Forms.NotifyIcon>元件會在工作列的狀態通知區域中顯示一個圖示。 若要在 [狀態] 區域中顯示多個圖示，您必須有多個<xref:System.Windows.Forms.NotifyIcon>表單上的元件。 若要設定顯示控制項的圖示，請使用<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。 您也可以撰寫程式碼<xref:System.Windows.Forms.NotifyIcon.DoubleClick>事件處理常式，因此當使用者按兩下圖示時，會發生的事情的情況。 例如，您可以進行設定圖示所代表的背景處理序的使用者出現的對話方塊。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon>元件通知僅供使用，可用來警示使用者動作或事件已發生或發生某種類型的狀態變更。 您應該使用與應用程式的標準互動的功能表、 工具列和其他使用者介面項目。  
  
### <a name="to-set-the-icon"></a>若要設定圖示  
  
1.  指派值給<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。 值必須是型別`System.Drawing.Icon`且能載入從.ico 檔案。 您可以指定的圖示檔，在程式碼，或按一下省略符號按鈕 (![VisualStudioEllipsesButton 螢幕擷取畫面](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) 旁邊<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性**屬性**視窗，然後選取 檔案中的**開啟**出現的對話方塊。  
  
2.  將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設定為 `true`。  
  
3.  設定<xref:System.Windows.Forms.NotifyIcon.Text%2A>屬性設為適當的工具提示字串。  
  
     在下列程式碼範例中，將路徑設定圖示的位置是**我的文件**資料夾。 使用這個位置是因為您可以假設執行 Windows 作業系統的大部分電腦都會包含此資料夾。 選擇此位置也可讓使用者以最少的系統存取層級可安全地執行應用程式。 下列範例要求的表單具有<xref:System.Windows.Forms.NotifyIcon>已經加入的控制項。 它也需要一個名為圖示檔案`Icon.ico`。  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
    ```  
  
    ```cpp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Windows.Forms.NotifyIcon>  
 <xref:System.Windows.Forms.NotifyIcon.Icon%2A>  
 [操作說明：將捷徑功能表與 Windows Forms NotifyIcon 元件關聯](../../../../docs/framework/winforms/controls/how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)  
 [NotifyIcon 元件](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)  
 [NotifyIcon 元件概觀](../../../../docs/framework/winforms/controls/notifyicon-component-overview-windows-forms.md)
