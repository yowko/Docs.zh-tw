---
title: 使用 NotifyIcon 元件將應用程式圖示新增至工作列
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
ms.openlocfilehash: 46b50ecaabe75dba08fea922d7b5639031692269
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746242"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>如何：使用 Windows Form NotifyIcon 元件將應用程式圖示加入至 TaskBar

Windows Forms <xref:System.Windows.Forms.NotifyIcon> 元件會在工作列的狀態通知區域中顯示單一圖示。 若要在 [狀態] 區域中顯示多個圖示，您的表單上必須有多個 <xref:System.Windows.Forms.NotifyIcon> 元件。 若要設定控制項的顯示圖示，請使用 [<xref:System.Windows.Forms.NotifyIcon.Icon%2A>] 屬性。 您也可以在 <xref:System.Windows.Forms.NotifyIcon.DoubleClick> 事件處理常式中撰寫程式碼，如此一來，當使用者按兩下圖示時，就會發生問題。 例如，您可以讓使用者看到對話方塊，以設定圖示所代表的背景進程。

> [!NOTE]
> <xref:System.Windows.Forms.NotifyIcon> 元件僅供通知之用，用來警示使用者發生動作或事件，或某個排序狀態有變更。 您應該使用功能表、工具列和其他使用者介面元素，來與應用程式進行標準互動。

### <a name="to-set-the-icon"></a>若要設定圖示

1. 將值指派給 <xref:System.Windows.Forms.NotifyIcon.Icon%2A> 屬性。 此值必須是 `System.Drawing.Icon` 類型，而且可以從 .ico 檔案載入。 您可以在程式碼中指定圖示檔，或按一下省略號按鈕（![**屬性**] 視窗中 [<xref:System.Windows.Forms.NotifyIcon.Icon%2A>] 屬性旁邊的 [](./media/visual-studio-ellipsis-button.png)Visual Studio 屬性視窗中的省略號按鈕（...），然後在出現的 [**開啟**] 對話方塊中選取檔案。

2. 將 <xref:System.Windows.Forms.NotifyIcon.Visible%2A> 屬性設定為 `true`。

3. 將 [<xref:System.Windows.Forms.NotifyIcon.Text%2A>] 屬性設定為適當的工具提示字串。

     在下列程式碼範例中，為圖示的位置設定的路徑是 [**我的文件**] 資料夾。 因為您可以假設大部分執行 Windows 作業系統的電腦都包含此資料夾，所以會使用這個位置。 選擇此位置也可讓具有最低系統存取層級的使用者安全地執行應用程式。 下列範例需要已經加入 <xref:System.Windows.Forms.NotifyIcon> 控制項的表單。 它也需要名為 `Icon.ico`的圖示檔。

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

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [操作說明：將捷徑功能表與 Windows Forms NotifyIcon 元件關聯](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon 元件](notifyicon-component-windows-forms.md)
- [NotifyIcon 元件概觀](notifyicon-component-overview-windows-forms.md)
