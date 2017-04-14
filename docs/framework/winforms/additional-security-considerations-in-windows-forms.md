---
title: "Windows Form 中的其他安全性考量 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "應用程式開發介面的呼叫, Windows Form 安全性設定"
  - "API, 呼叫"
  - "剪貼簿, 保護存取"
  - "安全性 [Windows Form]"
  - "安全性 [Windows Form], 呼叫 API"
  - "Windows 應用程式開發介面, 呼叫"
  - "Windows 應用程式開發介面, 安全的呼叫"
  - "Windows 應用程式開發介面, Windows Form 安全性設定"
  - "Windows Form, 對 Windows API 的安全呼叫"
ms.assetid: 15abda8b-0527-47c7-aedb-77ab595f2bf1
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# Windows Form 中的其他安全性考量
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 的安全性設定可能會使應用程式在部分信任的環境中，以不同於本機電腦的方式執行。  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 會限制對檔案系統、網路、Unmanaged API 以及其他許多重要本機資源的存取。  安全性設定會影響呼叫 Microsoft Win32 API 或其他無法由安全性系統驗證之 API 的功能。  安全性也會影響應用程式的其他方面，包括檔案和資料存取以及列印。  如需在部分信任環境中檔案和資料存取的詳細資訊，請參閱 [Windows Form 中更安全的檔案和資料存取](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)。  如需在部分信任環境中列印的詳細資訊，請參閱 [Windows Form 中更安全的列印](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)。  
  
 下列小節將討論如何使用剪貼簿、執行視窗管理，以及從在部分信任環境中執行的應用程式呼叫 Win32 API。  
  
## 剪貼簿存取  
 <xref:System.Security.Permissions.UIPermission> 類別會控制對 \[剪貼簿\] 的存取，而關聯的 <xref:System.Security.Permissions.UIPermissionClipboard> 列舉值會表示存取層級。  下表顯示可能的使用權限等級。  
  
|UIPermissionClipboard 值|描述|  
|-----------------------------|--------|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|可以無限制地使用 \[剪貼簿\]。|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|可以在一些限制下使用 \[剪貼簿\]。  將資料放到 \[剪貼簿\]\(\[複製\] 或 \[剪下\] 命令作業\) 的能力不受限制。  可接受貼上動作的內建 \(Intrinsic\) 控制項 \(例如文字方塊\) 都可以接受剪貼簿資料，但是使用者控制項不能以程式設計方式從剪貼簿讀取資料。|  
|<xref:System.Security.Permissions.UIPermissionClipboard>|不能使用 \[剪貼簿\]。|  
  
 根據預設，近端內部網路區域會取得 <xref:System.Security.Permissions.UIPermissionClipboard> 存取權限，而網際網路區域則會取得 <xref:System.Security.Permissions.UIPermissionClipboard> 存取權限。  這表示應用程式可以將資料複製到剪貼簿，但是不能以程式設計方式將資料貼到剪貼簿中或從剪貼簿讀取資料。  這些限制能防止未受完全信任的程式，讀取其他應用程式複製到 \[剪貼簿\] 的內容。  如果應用程式需要完整的剪貼簿存取權限，但是您不具有這樣的使用權限，就必須提高應用程式的使用權限。  如需提高使用權限的詳細資訊，請參閱[一般安全性原則管理](http://msdn.microsoft.com/zh-tw/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)。  
  
## 視窗管理  
 <xref:System.Security.Permissions.UIPermission> 類別也會控制執行視窗管理及其他 UI 相關動作的使用權限，而相關聯的 <xref:System.Security.Permissions.UIPermissionWindow> 列舉值則會指示存取層級。  下表顯示可能的使用權限等級。  
  
 根據預設，近端內部網路區域會取得 <xref:System.Security.Permissions.UIPermissionWindow> 存取權限，而網際網路區域則會取得 <xref:System.Security.Permissions.UIPermissionWindow> 存取權限。  這表示在網際網路區域中，應用程式可以執行大部分的視窗和 UI 動作，不過視窗的外觀將會有所修改。  修改的視窗在首次執行時會顯示汽球通知，包含修改的標題列文字，而且在標題列上需要關閉按鈕。  汽球通知和標題列可以讓應用程式的使用者知道，應用程式正在部分信任的環境中執行。  
  
|UIPermissionWindow 值|描述|  
|--------------------------|--------|  
|<xref:System.Security.Permissions.UIPermissionWindow>|使用者可以使用所有視窗和使用者輸入事件，完全不受限制。|  
|<xref:System.Security.Permissions.UIPermissionWindow>|使用者只能使用較安全最上層視窗和較安全子視窗進行繪圖，而且只能在這些最上層視窗和子視窗中使用使用者介面的使用者輸入事件。  這些較安全的視窗都會清楚標記出來，而且有最小和最大的大小限制。  這些限制可以防止可能有害的詐騙攻擊，例如模仿系統登入畫面或系統桌面，並且會限制以程式設計方式存取父視窗、焦點相關的 API 及使用 <xref:System.Windows.Forms.ToolTip> 控制項。|  
|<xref:System.Security.Permissions.UIPermissionWindow>|使用者只能使用較安全子視窗進行繪圖，而且在該子視窗內只能使用使用者介面的使用者輸入事件。  顯示在瀏覽器中的控制項就是較安全子視窗的例子。|  
|<xref:System.Security.Permissions.UIPermissionWindow>|使用者不能使用任何視窗或使用者介面事件。  無法使用使用者介面。|  
  
 以 <xref:System.Security.Permissions.UIPermissionWindow> 列舉型別識別之每個使用權限等級所允許的動作都會少於上一個等級。  下表會分別指出 <xref:System.Security.Permissions.UIPermissionWindow> 和 <xref:System.Security.Permissions.UIPermissionWindow> 值所限制的動作。  如需了解各成員所需要的確實使用權限，請參閱 .NET Framework 類別庫 \(Class Library\) 文件中該成員的參考。  
  
 <xref:System.Security.Permissions.UIPermissionWindow> 使用權限會限制下表中所列的動作。  
  
|元件|限制的動作|  
|--------|-----------|  
|<xref:System.Windows.Forms.Application>|-   設定 <xref:System.Windows.Forms.Application.SafeTopLevelCaptionFormat%2A> 屬性。|  
|<xref:System.Windows.Forms.Control>|-   取得 <xref:System.Windows.Forms.Control.Parent%2A> 屬性。<br />-   設定 `Region` 屬性。<br />-   呼叫 <xref:System.Windows.Forms.Control.FindForm%2A>、<xref:System.Windows.Forms.Control.Focus%2A>、<xref:System.Windows.Forms.Control.FromChildHandle%2A> 和 <xref:System.Windows.Forms.Control.FromHandle%2A>、<xref:System.Windows.Forms.Control.PreProcessMessage%2A>、<xref:System.Windows.Forms.Control.ReflectMessage%2A> 或 <xref:System.Windows.Forms.Control.SetTopLevel%2A> 方法。<br />-   呼叫 <xref:System.Windows.Forms.Control.GetChildAtPoint%2A> 方法 \(如果傳回的控制項不是呼叫控制項的子項\)。<br />-   修改容器 \(Container\) 控制項內的控制項焦點。|  
|<xref:System.Windows.Forms.Cursor>|-   設定 <xref:System.Windows.Forms.Cursor.Clip%2A> 屬性。<br />-   呼叫 <xref:System.Windows.Forms.Control.Hide%2A> 方法。|  
|<xref:System.Windows.Forms.DataGrid>|-   呼叫 <xref:System.Windows.Forms.ContainerControl.ProcessTabKey%2A> 方法。|  
|<xref:System.Windows.Forms.Form>|-   取得 <xref:System.Windows.Forms.Form.ActiveForm%2A> 或 <xref:System.Windows.Forms.Form.MdiParent%2A> 屬性。<br />-   設定 <xref:System.Windows.Forms.Form.ControlBox%2A>、<xref:System.Windows.Forms.Form.ShowInTaskbar%2A> 或 <xref:System.Windows.Forms.Form.TopMost%2A> 屬性。<br />-   將 <xref:System.Windows.Forms.Form.Opacity%2A> 屬性設定為低於 50%。<br />-   以程式設計方式將 <xref:System.Windows.Forms.Form.WindowState%2A> 屬性設定為 <xref:System.Windows.Forms.FormWindowState>。<br />-   呼叫 <xref:System.Windows.Forms.Form.Activate%2A> 方法。<br />-   使用 <xref:System.Windows.Forms.FormBorderStyle>、<xref:System.Windows.Forms.FormBorderStyle> 和 <xref:System.Windows.Forms.FormBorderStyle> <xref:System.Windows.Forms.FormBorderStyle> 列舉值。|  
|<xref:System.Windows.Forms.NotifyIcon>|-   使用 <xref:System.Windows.Forms.NotifyIcon> 元件完全受到限制。|  
  
 除了 <xref:System.Security.Permissions.UIPermissionWindow> 值的限制以外，<xref:System.Security.Permissions.UIPermissionWindow> 值還會限制下表中所列的動作。  
  
|元件|限制的動作|  
|--------|-----------|  
|<xref:System.Windows.Forms.CommonDialog>|-   顯示衍生自 <xref:System.Windows.Forms.CommonDialog> 類別的對話方塊。|  
|<xref:System.Windows.Forms.Control>|-   呼叫 <xref:System.Windows.Forms.Control.CreateGraphics%2A> 方法。<br />-   設定 <xref:System.Windows.Forms.Control.Cursor%2A> 屬性。|  
|<xref:System.Windows.Forms.Control.Cursor%2A>|-   設定 <xref:System.Windows.Forms.Cursor.Current%2A> 屬性。|  
|<xref:System.Windows.Forms.MessageBox>|-   呼叫 <xref:System.Windows.Forms.Form.Show%2A> 方法。|  
  
### 裝載協力廠商控制項  
 如果您的表單中包含協力廠商控制項，那麼可能會需要使用不同的視窗管理方法。  協力廠商控制項是指任何不是由您自己開發及編譯的自訂 <xref:System.Windows.Forms.UserControl>。  雖然裝載的狀況不容易受到外界攻擊，但是理論上，協力廠商是能夠擴展控制項的呈現介面，以涵蓋表單的整個區域。  然後，這個控制項便會產生一個會威脅安全性的對話方塊，要求您的使用者輸入如使用者\/密碼或銀行帳號一類的資訊。  
  
 若要限制這項潛在的風險，請只使用您所信任廠商的協力廠商控制項。  如果您使用從無法驗證的來源下載的協力廠商控制項，我們便建議您檢閱程式碼以找出潛在弱點。  在驗證過該來源是無惡意的之後，您就應該自己編譯組件以確保來源會符合組件。  
  
## Win32 API 呼叫  
 如果應用程式設計需要從 Win32 API 呼叫函式，就表示您正在存取 Unmanaged 程式碼。  在這種情況下，當您正在使用 Win32 API 呼叫或值時，將無法判斷程式碼對視窗或作業系統執行的動作。  <xref:System.Security.Permissions.SecurityPermissionFlag> 列舉型別的 <xref:System.Security.Permissions.SecurityPermission> 類別和 <xref:System.Security.Permissions.SecurityPermissionFlag> 值會控制對 Unmanaged 程式碼的存取。  只有當應用程式取得 <xref:System.Security.Permissions.SecurityPermissionFlag> 使用權限後，才能存取 Unmanaged 程式碼。  根據預設，只有在本機執行的應用程式才能呼叫 Unmanaged 程式碼。  
  
 有些 Windows Form 成員會提供需要 <xref:System.Security.Permissions.SecurityPermissionFlag> 使用權限的 Unmanaged 存取。  下表列出 <xref:System.Windows.Forms> 命名空間中需要使用權限的成員。  如需成員所需要之使用權限的詳細資訊，請參閱 .NET Framework 類別庫文件。  
  
|元件|成員|  
|--------|--------|  
|<xref:System.Windows.Forms.Application>|-   <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法<br />-   <xref:System.Windows.Forms.Application.CurrentInputLanguage%2A> 屬性<br />-   `Exit` 方法<br />-   <xref:System.Windows.Forms.Application.ExitThread%2A> 方法<br />-   <xref:System.Windows.Forms.Application.ThreadException> 事件|  
|<xref:System.Windows.Forms.CommonDialog>|-   <xref:System.Windows.Forms.CommonDialog.HookProc%2A> 方法<br />-   <xref:System.Windows.Forms.CommonDialog.OwnerWndProc%2A>\\ 方法<br />-   <xref:System.Windows.Forms.CommonDialog.Reset%2A> 方法<br />-   <xref:System.Windows.Forms.CommonDialog.RunDialog%2A> 方法|  
|<xref:System.Windows.Forms.Control>|-   <xref:System.Windows.Forms.Control.CreateParams%2A> 方法<br />-   <xref:System.Windows.Forms.Control.DefWndProc%2A> 方法<br />-   <xref:System.Windows.Forms.Control.DestroyHandle%2A> 方法<br />-   <xref:System.Windows.Forms.Control.WndProc%2A> 方法|  
|<xref:System.Windows.Forms.Help>|-   <xref:System.Windows.Forms.Help.ShowHelp%2A> 方法<br />-   <xref:System.Windows.Forms.Help.ShowHelpIndex%2A> 方法|  
|<xref:System.Windows.Forms.NativeWindow>|-   <xref:System.Windows.Forms.NativeWindow> 類別|  
|<xref:System.Windows.Forms.Screen>|-   <xref:System.Windows.Forms.Screen.FromHandle%2A> 方法|  
|<xref:System.Windows.Forms.SendKeys>|-   <xref:System.Windows.Forms.SendKeys.Send%2A> 方法<br />-   <xref:System.Windows.Forms.SendKeys.SendWait%2A> 方法|  
  
 如果應用程式不具有呼叫 Unmanaged 程式碼的使用權限，則應用程式必須要求 <xref:System.Security.Permissions.SecurityPermissionFlag> 使用權限，或者您必須考慮實作功能的其他替代方式，在許多情況下，Windows Form 會提供 Win32 API 函式的 Managed 替代用法。  如果沒有替代用法，而且應用程式必須存取 Unmanaged 程式碼，您就必須提高應用程式的使用權限。  
  
 呼叫 Unmanaged 程式碼的使用權限，可讓應用程式執行大部分的工作。  因此，呼叫 Unmanaged 程式碼的使用權限只能授與來自信任來源的應用程式。  或者，您可以根據應用程式，將呼叫 Unmanaged 程式碼的那一部分應用程式功能變成選擇性的功能，或是只能在完全信任的環境中啟用。  如需危險使用權限的詳細資訊，請參閱[危險使用權限和原則管理](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)。  如需提高使用權限的詳細資訊，請參閱[NIB: General Security Policy Administration](http://msdn.microsoft.com/zh-tw/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)。  
  
## 請參閱  
 [Windows Form 中更安全的檔案和資料存取](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)   
 [Windows Form 中更安全的列印](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)   
 [Windows Form 中的安全性概觀](../../../docs/framework/winforms/security-in-windows-forms-overview.md)   
 [Windows Form 安全性](../../../docs/framework/winforms/windows-forms-security.md)   
 [保護 ClickOnce 應用程式](../Topic/Securing%20ClickOnce%20Applications.md)