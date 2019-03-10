---
title: HOW TO：應用程式圖示加入工作列使用 Windows Forms NotifyIcon 元件
ms.date: 03/30/2017
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
ms.openlocfilehash: 04f6b98a2206371a2838b3a6952feeafcd788309
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714251"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>HOW TO：應用程式圖示加入工作列使用 Windows Forms NotifyIcon 元件
Windows Form<xref:System.Windows.Forms.NotifyIcon>元件會顯示單一圖示在工作列的狀態通知區域中。 若要顯示多個圖示，狀態 區域中，您必須有多個<xref:System.Windows.Forms.NotifyIcon>您的表單上的元件。 若要設定控制項所顯示的圖示，使用<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。 您也可以撰寫程式碼<xref:System.Windows.Forms.NotifyIcon.DoubleClick>事件處理常式，因此當使用者按兩下的圖示時，會有發生的情況。 例如，您可以進行使用者設定圖示所代表的背景處理序出現的對話方塊。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon>元件用以通知僅供，某個動作或事件已發生的警示使用者，或已有某種形式的狀態變更。 您應該使用標準互動的應用程式的功能表、 工具列和其他使用者介面項目。  
  
### <a name="to-set-the-icon"></a>若要設定圖示  
  
1.  指派值給<xref:System.Windows.Forms.NotifyIcon.Icon%2A>屬性。 值必須是型別`System.Drawing.Icon`和從.ico 檔可以載入。 在程式碼，或按一下省略符號按鈕，您可以指定的圖示檔 (![VisualStudioEllipsesButton 螢幕擷取畫面](../media/vbellipsesbutton.png "vbEllipsesButton")) 旁<xref:System.Windows.Forms.NotifyIcon.Icon%2A>中的屬性**屬性**視窗中，，然後選取 檔案中的**開啟**出現的對話方塊。  
  
2.  將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設定為 `true`。  
  
3.  設定<xref:System.Windows.Forms.NotifyIcon.Text%2A>屬性設為適當的工具提示字串。  
  
     在下列程式碼範例中，將路徑設為圖示的位置**我的文件**資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。 選擇此位置也可讓具有最少的系統存取層級的使用者安全地執行應用程式。 下列範例需要表單<xref:System.Windows.Forms.NotifyIcon>已經加入的控制項。 它也需要圖示檔名為`Icon.ico`。  
  
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
  
## <a name="see-also"></a>另請參閱
- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [如何：使用 Windows Forms NotifyIcon 元件關聯的捷徑功能表](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon 元件](notifyicon-component-windows-forms.md)
- [NotifyIcon 元件概觀](notifyicon-component-overview-windows-forms.md)
