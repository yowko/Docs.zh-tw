---
title: "疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework, 疑難排解遭封鎖的安裝問題"
  - "遭封鎖的 .NET Framework 安裝, 疑難排解"
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
caps.latest.revision: 57
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 39
---
# 疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題
當您執行 .NET Framework 4.5、4.5.1、4.5.2、4.6 或 4.6.1 的 [Web 或離線安裝程式](../../../docs/framework/install/guide-for-developers.md)時，可能會出現無法安裝或封鎖安裝 .NET Framework 的問題。 下面表格列出可能造成阻礙的問題並且提供疑難排解資訊。  
  
 下表中的 4.5.*x* 是指 .NET Framework 4.5 及其單點發行版本 4.5.1 和 4.5.2、4.6 或 4.6.1。  
  
|封鎖訊息|如需詳細資訊或解決這個問題|  
|----------|-------------------|  
|解除安裝 Microsoft .NET Framework 可能會導致某些應用程式停止運作。|一般而言，您不應該解除安裝電腦上已安裝的任何 .NET Framework 版本，因為您使用的應用程式可能相依於特定的 .NET Framework 版本。 如需詳細資訊，請參閱*使用者入門*指南中的 [適用於使用者的 .NET Framework](../../../docs/framework/get-started/index.md#ForUsers)。|  
|.NET Framework 4.5*.x*\/4.6*.x* \(*語言*\) 需要 .NET Framework 4.5*.x*\/4.6*.x*。 請從下載中心安裝 .NET Framework 4.5*.x*\/4.6*.x*，並重新執行安裝程式。|在安裝語言套件之前，必須安裝指定 .NET Framework 版本的英文版本。 如需詳細資訊，請參閱安裝指南中有關 [若要安裝語言套件](../../../docs/framework/install/guide-for-developers.md#standalone_language_packs) 的章節。|  
|無法安裝 .NET Framework 4.5*.x*\/4.6*.x*。 電腦上的其他應用程式與這個程式不相容。<br /><br /> \-或\-<br /><br /> 電腦上的其他應用程式與這個程式不相容。|這個訊息最可能的原因是安裝了 .NET Framework 的預覽或 RC 版本。 解除安裝預覽版本或 RC 版本，並重新執行安裝程式。|  
|無法使用這個套件將 .NET Framework 4.5*.x*\/4.6*.x* 解除安裝。 若要從電腦將 .NET Framework 4.5.*x*\/4.6*.x* 解除安裝，請前往 \[控制台\]，依序選擇 \[程式和功能\]、\[檢視安裝的更新\]、\[Microsoft Windows \(KB2828152\) 更新\]，然後選擇 \[解除安裝\]。|您要安裝的套件無法解除安裝 .NET Framework 的預覽版本或 RC 版本。<br /><br /> 請從 \[控制台\] 解除安裝預覽版本或 RC 版本。|  
|無法將 .NET Framework 4.5*.x*\/4.6*.x* 解除安裝。 電腦上的其他應用程式依存於這個程式。|一般而言，您不應該解除安裝電腦上的任何 .NET Framework 版本，因為您使用的應用程式可能相依於特定的 .NET Framework 版本。 如需詳細資訊，請參閱*使用者入門*指南中的 [適用於使用者的 .NET Framework](../../../docs/framework/get-started/index.md#ForUsers)。|  
|.NET Framework 4.5*.x*\/4.6*.x* 可轉散發套件不適用於此作業系統。 請從 Microsoft 下載中心下載適用於作業系統的 .NET Framework 4.5*.x*\/4.6*.x*。|您可能嘗試在不支援的平台上安裝 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]、4.5.2、4.6 或 4.6.1，或您選擇的安裝套件不包含所有支援作業系統所需的元件。 使用離線安裝程式 \([4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=309493)、[4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)、[4.6](http://go.microsoft.com/fwlink/p/?LinkId=528233) 或 [4.6.1](http://go.microsoft.com/fwlink/p/?LinkId=671744)\) 重新執行安裝。 如需詳細資訊，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)和[系統需求](../../../docs/framework/get-started/system-requirements.md)以了解支援的作業系統。|  
|您的電腦目前執行的是 Windows Server 2008 作業系統的 Server Core 安裝。 .NET Framework 4.5.*x* 需要較新版本的作業系統。 請安裝 Windows Server 2008 R2 SP1 \(含\) 以上版本並重新執行 .NET Framework 4.5.*x* 安裝程式。|Windows Server 2008 R2 SP1 \(含\) 以後版本的 Server Core 角色才有支援 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 和 4.5.2。 請參閱 [系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|您沒有足夠權限為此電腦的所有使用者完成這項作業。 請以系統管理員身分登入，然後再重新執行**安裝程式**。|您必須是此電腦的系統管理員，才能安裝 .NET Framework。|  
|安裝程式無法繼續，因為前一個安裝要求您的電腦必須重新啟動。 請重新啟動您的電腦，然後再重新執行安裝程式。|有時需要重新開機才能完成安裝。 請遵循指示重新啟動您的電腦，然後再重新執行安裝程式。|  
|這部電腦已安裝 .NET Framework 4.5*.x*\/4.6*.x* \(繁體中文\) \(含\) 以上版本的更新。|不需要採取任何動作。|  
|.NET Framework 安裝程式無法在程式相容性模式中執行。|請參閱本文稍後的[程式相容性問題](#compat)一節。|  
|因為元件存放區已損毀，所以未安裝 .NET framework 4.5*.x*\/4.6*.x*。|如需詳細資訊，請參閱[使用 DISM 或系統更新整備工具修復 Windows 更新錯誤](https://support.microsoft.com/en-us/kb/947821)。|  
|安裝程式無法執行，因為這部電腦沒有可用的 Windows Installer 服務。|請參閱 Microsoft 技術支援網站上的[安裝或更新程式時發生 Windows Installer 服務錯誤](http://go.microsoft.com/fwlink/p/?LinkId=248684)。|  
|安裝程式無法正確執行，因為這部電腦沒有可用的 Windows Update 服務。|電腦可能是設定為使用 Windows Server Update Services \(WSUS\)，而不是使用 Microsoft Windows Update。 如需詳細資訊，請參閱[當您嘗試在 Windows 8 或 Windows Server 2012 安裝 .NET Framework 3.5 時產生錯誤碼](http://support.microsoft.com/kb/2734782)中的錯誤碼 0x800F0906 區段。<br /><br /> 另外，請參閱 Microsoft 技術支援網站上的[如何取得最新版的 Windows Update 代理程式](http://go.microsoft.com/fwlink/p/?LinkId=248437)以幫助管理電腦更新。|  
|安裝程式無法正確執行，因為這部電腦沒有可用的背景智慧型傳送服務 \(BITS\)。|請參閱 Microsoft 技術支援網站上的[可防止背景智慧型傳送服務 \(BITS\) 在 Windows Vista 電腦上損毀的更新](http://go.microsoft.com/fwlink/p/?LinkId=248680)。|  
|.NET Framework 4.5. *.x*\/4.6 已是此作業系統的一部分。 您不必安裝 .NET Framework 4.5*.x*\/4.6 可轉散發套件。|不需執行任何動作。 請參閱支援的作業系統的 [系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|此作業系統不支援 .NET Framework 4.5*.x*\/4.6*.x*。|請參閱支援的作業系統的 [系統需求](../../../docs/framework/get-started/system-requirements.md)。<br /><br /> 若是 .NET framework 在 Windows 7 上安裝失敗，此訊息通常表示未安裝 Windows 7 SP1。 在 Windows 7 系統中，.NET Framework 需要 Windows 7 SP1。 若您使用 Windows 7 而尚未安裝 Service Pack 1，就必須先加以安裝，才能安裝 .NET Framework。|  
|您的電腦目前執行的是 Windows Server 2008 作業系統的 Server Core 安裝。 .NET Framework 4.5.*x* 需要完整版的作業系統或 Server Core 2008 R2 SP1。 請安裝 Windows Server 2008 SP2 或 Windows Server 2008 R2 SP1 或 Server Core 2008 R2 SP1 的完整版本，並重新執行 .NET Framework 4.5.*x* 安裝程式。|Windows Server 2008 R2 SP1 \(含\) 以後版本的 Server Core 角色才有支援 .NET Framework。 請參閱 [系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|.NET Framework 4.5.*x* 已是這個作業系統的一部分，但目前處於關閉狀態 \(僅限 [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]\)。|請參閱 Windows 網站的[開啟或關閉 Windows 功能](http://go.microsoft.com/fwlink/p/?LinkId=248438)。|  
|這個安裝程式需要 x86 電腦， 無法安裝在 x64 或 IA64 電腦上。|請參閱 MSDN Library 中的[系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|這個安裝程式需要 x64 或 x86 電腦， 無法安裝在 IA64 電腦上。|請參閱 MSDN Library 中的[系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
  
<a name="compat"></a>   
### 程式相容性問題  
 在 Windows 程式相容性模式中執行時，.NET Framework 4.5 或其點發行版本安裝會因為 1603 錯誤碼或封鎖而失敗。 \[**程式相容性助理**\] 會指出 .NET Framework 可能沒有正確安裝，並提示您使用建議的設定 \(程式相容性模式\) 來重新安裝。 也有可能先前試圖執行 .NET Framework 安裝程式時失敗或取消了，而已經由「程式相容性助理」設定了程式相容性模式。  
  
 .NET Framework 安裝程式無法在程式相容性模式中執行。 若要解決這個封鎖問題，您必須確保未在 \[登錄編輯程式\] 中啟用全系統的相容性模式設定：  
  
1.  選擇 \[**開始**\] 按鈕，然後選擇 \[**執行**\]。  
  
2.  在 \[執行\] 對話方塊中輸入 `regedit`，然後選擇 \[確定\]。  
  
3.  在 \[登錄編輯程式\] 中，瀏覽至下列子機碼：  
  
    -   HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Compatibility Assistant\\Persisted  
  
    -   HKEY\_CURRENT\_USER\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AppCompatFlags\\Layers  
  
4.  在 \[名稱\] 欄中，根據安裝的版本尋找 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、4.5.1、4.5.2、4.6 或 4.6.1 下載名稱，然後刪除這些項目。 如需下載名稱，請參閱 [安裝指南](../../../docs/framework/install/guide-for-developers.md) 文章。  
  
5.  請重新執行 4.5、4.5.1、4.5.2，或 4.6 或 4.6.1 版本的 .NET Framework 安裝程式。  
  
## 請參閱  
 [安裝指南](../../../docs/framework/install/guide-for-developers.md)