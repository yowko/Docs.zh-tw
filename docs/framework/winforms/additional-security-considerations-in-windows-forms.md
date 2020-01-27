---
title: 其他安全性考慮
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, secure calls to Windows API
- security [Windows Forms]
- security [Windows Forms], calling APIs
- Clipboard [Windows Forms], securing access
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
ms.openlocfilehash: c8d51a57194f1dc536bc4b5d0376987dbfd3b2cf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739816"
---
# <a name="additional-security-considerations-in-windows-forms"></a>Windows Form 中的其他安全性考量
.NET Framework 安全性設定可能會導致您的應用程式在部分信任環境中的執行方式與您的本機電腦不同。 .NET Framework 會限制對這類重要本機資源的存取，例如檔案系統、網路和未受管理的 Api，還有其他專案。 安全性設定會影響呼叫 Microsoft Windows API 或其他無法由安全性系統驗證之 Api 的能力。 安全性也會影響應用程式的其他層面，包括檔案和資料存取及列印。 如需在部分信任環境中存取檔案和資料的詳細資訊，請參閱 [Windows Forms 中更安全的檔案和資料存取](more-secure-file-and-data-access-in-windows-forms.md)。 如需在部分信任環境中列印的詳細資訊，請參閱 [Windows Forms 中更安全的列印](more-secure-printing-in-windows-forms.md)。  
  
 下列各節將討論如何使用剪貼簿、執行視窗操作，以及從在部分信任環境中執行的應用程式呼叫 Windows API。  
  
## <a name="clipboard-access"></a>剪貼簿存取  
 <xref:System.Security.Permissions.UIPermission> 類別可控制剪貼簿的存取，而相關聯的 <xref:System.Security.Permissions.UIPermissionClipboard> 列舉值則表示存取層級。 下表顯示可能的權限層級。  
  
|UIPermissionClipboard 值|描述|  
|---------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard>|可以不受限制使用剪貼簿。|  
|<xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard>|可以在受到部分限制下使用剪貼簿。 能夠不受限制將資料放在剪貼簿 (複製或剪下命令作業)。 接受貼上的內建控制項 (例如文字方塊) 可以接受剪貼簿資料，但無法以程式設計方式從剪貼簿讀取使用者控制項。|  
|<xref:System.Security.Permissions.UIPermissionClipboard.NoClipboard>|無法使用剪貼簿。|  
  
 根據預設，近端內部網路區域會收到 <xref:System.Security.Permissions.UIPermissionClipboard.AllClipboard> 存取權，而網際網路區域會收到 <xref:System.Security.Permissions.UIPermissionClipboard.OwnClipboard> 存取權。 這表示應用程式可以將資料複製到剪貼簿，但應用程式無法以程式設計方式在剪貼簿中貼上或讀取。 這些限制會防止未受完全信任的程式讀取另一個應用程式複製到剪貼簿的內容。 如果您的應用程式需要完整的剪貼簿存取，但您沒有權限，您必須提高應用程式的權限。 如需提高權限的詳細資訊，請參閱[一般安全性原則管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))。  
  
## <a name="window-manipulation"></a>視窗操作  
 <xref:System.Security.Permissions.UIPermission> 類別也會控制執行視窗操作和其他 UI 相關動作的許可權，而相關聯的 <xref:System.Security.Permissions.UIPermissionWindow> 列舉值則表示存取層級。 下表顯示可能的權限層級。  
  
 根據預設，近端內部網路區域會收到 <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> 存取權，而網際網路區域會收到 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> 存取權。 這表示在網際網路區域中，應用程式可以執行大部分的視窗和 UI 動作，但視窗的外觀會經過修改。 修改過的視窗會在第一次執行時顯示氣球通知、包含修改過的標題列文字，而且在標題列上需要有關閉按鈕。 氣球通知和標題列讓應用程式的使用者知道，應用程式正在部分信任下執行。  
  
|UIPermissionWindow 值|描述|  
|------------------------------|-----------------|  
|<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>|使用者可以無限制使用所有視窗和使用者輸入事件。|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows>|使用者只能使用較安全的最上層視窗和較安全的子視窗來繪圖，且只能使用這些最上層視窗和子視窗內之使用者介面的使用者輸入事件。 這些較安全的視窗有清楚的標籤，也有大小上限和下限的限制。 這些限制可防止可能有害的詐騙攻擊，例如模仿系統登入畫面或系統桌面，並限制以程式設計方式存取父視窗、與焦點相關的 Api，以及使用 <xref:System.Windows.Forms.ToolTip> 控制項。|  
|<xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows>|使用者只能使用較安全的子視窗來繪圖，且只能使用該子視窗內之使用者介面的使用者輸入事件。 瀏覽器內顯示的控制項即為較安全子視窗的一個例子。|  
|<xref:System.Security.Permissions.UIPermissionWindow.NoWindows>|使用者無法使用任何視窗或使用者介面事件。 無法使用任何使用者介面。|  
  
 <xref:System.Security.Permissions.UIPermissionWindow> 列舉所識別的每個許可權層級所允許的動作，比高於其上的層級更少。 下表指出 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> 和 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> 值所限制的動作。 如果每個成員所需的確切權限，請參閱 .NET Framework Class Library 文件中該成員的參考。  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> 許可權會限制下表所列的動作。  
  
|元件|受限制的動作|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.Application>|-   設定 <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> 屬性。|  
|<xref:System.Windows.Forms.Control>|-取得 <xref:System.Windows.Forms.Control.Parent%2A> 屬性。<br />-   設定 `Region` 屬性。<br />-呼叫 <xref:System.Windows.Forms.Control.FindForm%2A>、<xref:System.Windows.Forms.Control.Focus%2A>、<xref:System.Windows.Forms.Control.FromChildHandle%2A> 和 <xref:System.Windows.Forms.Control.FromHandle%2A>、<xref:System.Windows.Forms.Control.PreProcessMessage%2A>、<xref:System.Windows.Forms.Control.ReflectMessage%2A>或 <xref:System.Windows.Forms.Control.SetTopLevel%2A> 方法。<br />-如果傳回的控制項不是呼叫控制項的子系，則呼叫 <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> 方法。<br />-   修改容器控制項內的控制項焦點。|  
|<xref:System.Windows.Forms.Cursor>|-   設定 <xref:System.Windows.Forms.Cursor.Clip%2A> 屬性。<br />-呼叫 <xref:System.Windows.Forms.Control.Hide%2A> 方法。|  
|<xref:System.Windows.Forms.DataGrid>|-呼叫 <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> 方法。|  
|<xref:System.Windows.Forms.Form>|-取得 <xref:System.Windows.Forms.Form.ActiveForm%2A> 或 <xref:System.Windows.Forms.Form.MdiParent%2A> 屬性。<br />-設定 <xref:System.Windows.Forms.Form.ControlBox%2A>、<xref:System.Windows.Forms.Form.ShowInTaskbar%2A>或 <xref:System.Windows.Forms.Form.TopMost%2A> 屬性。<br />-將 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性設定為低於50%。<br />-將 <xref:System.Windows.Forms.Form.WindowState%2A> 屬性設定為以程式設計方式 <xref:System.Windows.Forms.FormWindowState.Minimized>。<br />-呼叫 <xref:System.Windows.Forms.Form.Activate%2A> 方法。<br />-使用 <xref:System.Windows.Forms.FormBorderStyle.None>、<xref:System.Windows.Forms.FormBorderStyle.FixedToolWindow>和 <xref:System.Windows.Forms.FormBorderStyle.SizableToolWindow><xref:System.Windows.Forms.FormBorderStyle> 列舉值。|  
|<xref:System.Windows.Forms.NotifyIcon>|-使用 <xref:System.Windows.Forms.NotifyIcon> 元件完全受到限制。|  
  
 <xref:System.Security.Permissions.UIPermissionWindow.SafeSubWindows> 值會限制下表所列的動作，以及 <xref:System.Security.Permissions.UIPermissionWindow.SafeTopLevelWindows> 值所設定的限制。  
  
|元件|受限制的動作|  
|---------------|------------------------|  
|<xref:System.Windows.Forms.CommonDialog>|-顯示衍生自 <xref:System.Windows.Forms.CommonDialog> 類別的對話方塊。|  
|<xref:System.Windows.Forms.Control>|-呼叫 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 方法。<br />-   設定 <xref:System.Windows.Forms.Control.Cursor%2A> 屬性。|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   設定 <xref:System.Windows.Forms.Cursor.Current%2A> 屬性。|  
|<xref:System.Windows.Forms.MessageBox>|-呼叫 <xref:System.Windows.Forms.Form.Show%2A> 方法。|  
  
### <a name="hosting-third-party-controls"></a>裝載協力廠商控制項  
 如果您的表單裝載協力廠商控制項，可能會有另一種視窗操作。 協力廠商控制項是您未自行開發和編譯的任何自訂 <xref:System.Windows.Forms.UserControl>。 雖然很難入侵裝載情節，但在理論上，協力廠商控制項有可能展開其呈現表面來涵蓋表單的整個區域。 接著，此控制項可模擬重要的對話方塊，然後向您的使用者要求資訊，例如使用者名稱/密碼組合或銀行帳戶號碼。  
  
 為了限制這種潛在風險，請只使用您信任的廠商的協力廠商控制項。 如果您使用的協力廠商控制項是從未驗證的來源下載，建議您檢閱原始程式碼中潛在的弱點。 在確認來源沒有惡意之後，您應該自行編譯組件，以確保來源符合組件。  
  
## <a name="windows-api-calls"></a>Windows API 呼叫  
 如果您的應用程式設計需要從 Windows API 呼叫函式，您會存取非受控碼。 在此情況下，當您使用 Windows API 呼叫或值時，無法判斷程式碼對視窗或作業系統的動作。 <xref:System.Security.Permissions.SecurityPermission> 類別和 <xref:System.Security.Permissions.SecurityPermissionFlag> 列舉的 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 值控制對非受控程式碼的存取。 只有當應用程式被授與 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 許可權時，才可以存取非受控碼。 根據預設，只有在本機執行的應用程式才能呼叫 Unmanaged 程式碼。  
  
 某些 Windows Forms 成員會提供需要 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 許可權的非受控存取權。 下表列出 <xref:System.Windows.Forms> 命名空間中需要許可權的成員。 如需成員所需權限的詳細資訊，請參閱 .NET Framework Class Library 文件。  
  
|元件|成員|  
|---------------|------------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> 屬性<br />-   `Exit` 方法<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> 方法<br />-   <xref:System.Windows.Forms.Application.ThreadException> 事件|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> 方法<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\ 方法<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> 方法<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> 方法|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> 方法<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> 方法<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> 方法<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> 方法|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> 方法<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> 方法|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> 類別|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> 方法|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> 方法<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> 方法|  
  
 如果您的應用程式沒有呼叫非受控碼的許可權，您的應用程式必須要求 <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> 許可權，或者您必須考慮採用其他方式來執行功能;在許多情況下，Windows Forms 提供 Windows API 函式的受控替代方式。 如果沒有替代做法，但應用程式必須存取 Unmanaged 程式碼，您必須提高應用程式的權限。  
  
 呼叫 Unmanaged 程式碼的權限可讓應用程式執行大部分的動作。 因此，呼叫 Unmanaged 程式碼的權限應該只授與來自受信任來源的應用程式。 另外，視應用程式而定，應用程式功能中會呼叫 Unmanaged 程式碼的部分可以是選擇性，或只在完全信任環境中啟用。 如需危險性權限的詳細資訊，請參閱[危險性權限和原則管理](../misc/dangerous-permissions-and-policy-administration.md)。 如需提高權限的詳細資訊，請參閱[一般安全性原則管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))。  
  
## <a name="see-also"></a>請參閱

- [Windows Forms 中更安全的檔案和資料存取](more-secure-file-and-data-access-in-windows-forms.md)
- [Windows Forms 中更安全的列印](more-secure-printing-in-windows-forms.md)
- [Windows Forms 中的安全性概觀](security-in-windows-forms-overview.md)
- [Windows Forms 安全性](windows-forms-security.md)
- [保護 ClickOnce 應用程式](/visualstudio/deployment/securing-clickonce-applications)
