---
title: "疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題 | Microsoft Docs"
ms.custom: 
ms.date: 05/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, troubleshooting blocked installations
- blocked .NET Framework installations, troubleshooting
ms.assetid: c3fdfbc1-ed99-4202-a2b0-8c4f1646385d
caps.latest.revision: 57
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: ddcefb2b35f8cbf06a3abcc16158eee850f799ff
ms.openlocfilehash: 55228928d5d3d95cf28384e5179a43bfb0f598e9
ms.contentlocale: zh-tw
ms.lasthandoff: 05/11/2017

---
# <a name="troubleshooting-blocked-net-framework-installations-and-uninstallations"></a>疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題
當您執行 .NET Framework 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2 或 4.7 的 [Web 或離線安裝程式](../../../docs/framework/install/guide-for-developers.md)時，可能會遇到導致無法進行或封鎖 .NET Framework 安裝的問題。 下面表格列出可能造成阻礙的問題並且提供疑難排解資訊。  
  
 在 Windows 8 (含) 以上版本中，.NET Framework 是作業系統元件，無法單獨解除安裝。 .NET Framework 的更新會出現在 [控制台] 之 [程式和功能] 應用程式的 [已安裝更新] 索引標籤中。 若是未預先安裝 .NET Framework 的作業系統，.NET Framework 會出現在 主控台 之 程式和功能 應用程式的 解除安裝或​​變更程式 索引標籤 (或 新增/移除程式 索引標籤) 中。 如需預先安裝 .NET Framework 之 Windows 版本的資訊，請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。  

> [!IMPORTANT]
> 因為 .NET Framework 4.x 版是就地更新，所以您無法在已安裝更新版本的系統上安裝舊版 .NET framework 4.x。 例如，在 Windows 10 Creators Update 系統上，您無法安裝 .NET Framework 4.6.2，因為作業系統已預先安裝 .NET Framework 4.7。  
  
 您可以判斷系統上所安裝之 .NET Framework 的版本。 如需詳細資訊，請參閱[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。  
  
 下表中的 4.5.*x* 是指 .NET Framework 4.5 及其點發行版本 4.5.1 和 4.5.2，4.6.*x*是指 .NET Framework 4.6 及其點發行版本 4.6.1 和 4.6.2，而 4.7 是指 .NET Framework 4.7。  
  
|封鎖訊息|如需詳細資訊或解決這個問題|  
|----------------------|--------------------------------------------------|  
|解除安裝 Microsoft .NET Framework 可能會導致某些應用程式停止運作。|一般而言，您不應該解除安裝電腦上已安裝的任何 .NET Framework 版本，因為您使用的應用程式可能相依於特定的 .NET Framework 版本。 如需詳細資訊，請參閱*使用者入門*指南中的[適用於使用者的 .NET Framework](../../../docs/framework/get-started/index.md#ForUsers)。|  
|這部電腦已安裝 4.5*.x*/4.6*.x*/4.7 (繁體中文) 或更新版本。|不需要採取任何動作。<br /><br /> 若要判斷系統上所安裝之 .NET Framework 的版本，請參閱[如何：判斷所安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。|  
|.NET Framework 4.5*.x*/4.6*.x*/4.7 (語言) 需要 .NET Framework 4.5*.x*/4.6*.x*。 請從下載中心安裝 .NET Framework 4.5*.x*/4.6*.x*，並重新執行安裝程式。|在安裝語言套件之前，必須安裝指定 .NET Framework 版本的英文版本。 如需詳細資訊，請參閱《安裝指南》中的[安裝語言套件](../../../docs/framework/install/guide-for-developers.md#to-install-language-packs)一節。|  
|無法安裝 .NET Framework 4.5*.x*/4.6*.x*/4.7。 電腦上的其他應用程式與這個程式不相容。<br /><br /> -或-<br /><br /> 電腦上的其他應用程式與這個程式不相容。|這個訊息最可能的原因是安裝了 .NET Framework 的預覽或 RC 版本。 解除安裝預覽版本或 RC 版本，並重新執行安裝程式。|  
|無法使用這個套件解除安裝 .NET Framework 4.5*.x*/4.6*.x*/4.7。 若要從電腦將 .NET Framework 4.5*.x*/4.6*.x* 解除安裝，請移至 [控制台]，依序選擇 [程式和功能]、[檢視安裝的更新]、[Microsoft Windows (KB2828152) 更新]，然後選擇 [解除安裝]。|您要安裝的套件無法解除安裝 .NET Framework 的預覽版本或 RC 版本。<br /><br /> 請從 [控制台] 解除安裝預覽版本或 RC 版本。|  
|無法將 .NET Framework 4.5*.x*/4.6*.x*/4.7 解除安裝。 電腦上的其他應用程式依存於這個程式。|一般而言，您不應該解除安裝電腦上的任何 .NET Framework 版本，因為您使用的應用程式可能相依於特定的 .NET Framework 版本。 如需詳細資訊，請參閱*使用者入門*指南中的[適用於使用者的 .NET Framework](../../../docs/framework/get-started/index.md#ForUsers)。|  
|.NET Framework 4.5*.x*/4.6*.x*/4.7 可轉散發套件不適用於這個作業系統。 請從 Microsoft 下載中心下載適用於作業系統的 .NET Framework 4.5*.x*/4.6*.x*。|您可能嘗試在不支援的平台上安裝 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]、4.5.2、4.6、4.6.1、4.6.2 或 4.7，或您選擇的安裝套件未包含所支援的全部作業系統所需的元件。 請使用離線安裝程式 ([4.5.1](http://go.microsoft.com/fwlink/p/?LinkId=309493)、[4.5.2](http://go.microsoft.com/fwlink/p/?LinkId=397706)、[4.6](http://go.microsoft.com/fwlink/p/?LinkId=528233)、[4.6.1](http://go.microsoft.com/fwlink/p/?LinkId=671744)、[4.6.2](http://go.microsoft.com/fwlink/p/?LinkId=780604) 或 [4.7](http://go.microsoft.com/fwlink/p/?LinkId=825306)) 來重新執行安裝。 如需詳細資訊，請參閱[安裝指南](../../../docs/framework/install/guide-for-developers.md)和[系統需求](../../../docs/framework/get-started/system-requirements.md)以了解支援的作業系統。|  
|您必須先安裝對應至 KB\<號碼> 的更新，才能安裝此產品。|.NET Framework 的安裝需要先安裝 KB 更新，才能安裝 .NET Framework。 請安裝更新，再重新開始 .NET Framework 安裝。<br /><br /> 例如，若要在 Windows 8.1、Windows RT 8.1 和 Windows Server 2012 R2 上安裝 .NET Framework 的更新版本，需要安裝對應至 [KB 2919355](https://support.microsoft.com/kb/2919355) 的更新。|  
|您的電腦目前執行的是 Windows Server 2008 作業系統的 Server Core 安裝。 .NET Framework 4.5.*x* 需要較新版本的作業系統。 請安裝 Windows Server 2008 R2 SP1 (含) 以上版本並重新執行 .NET Framework 4.5.*x* 安裝程式。|Windows Server 2008 R2 SP1 (含) 以後版本的 Server Core 角色才有支援 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 和 4.5.2。 請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|您沒有足夠權限為此電腦的所有使用者完成這項作業。 請以系統管理員身分登入，然後重新執行**安裝程式**。|您必須是此電腦的系統管理員，才能安裝 .NET Framework。|  
|安裝程式無法繼續，因為前一個安裝要求您的電腦必須重新啟動。 請重新啟動您的電腦，然後再重新執行安裝程式。|有時需要重新開機才能完成安裝。 請遵循指示重新啟動您的電腦，然後再重新執行安裝程式。<br /><br /> 在罕見的情況下，如果 Windows 偵測到一些遺失更新，並將重新啟動以安裝佇列中的下一個更新，系統可能會要求您多次重新啟動系統。|  
|.NET Framework 安裝程式無法在程式相容性模式中執行。|請參閱本文稍後的[程式相容性問題](#compat)一節。|  
|未安裝 .NET Framework 4.5*.x*/4.6*.x*/4.7，因為元件存放區已損毀。|如需詳細資訊，請參閱[使用 DISM 或系統更新整備工具修復 Windows Update 錯誤](https://support.microsoft.com/en-us/kb/947821)。|  
|安裝程式無法執行，因為這部電腦沒有可用的 Windows Installer 服務。|請參閱 Microsoft 支援服務網站上的 [Windows Installer Service error when installing or updating programs](http://go.microsoft.com/fwlink/p/?LinkId=248684)(安裝或更新程式時發生 Windows Installer 服務錯誤)。|  
|安裝程式無法正確執行，因為這部電腦沒有可用的 Windows Update 服務。|電腦可能是設定為使用 Windows Server Update Services (WSUS)，而不是使用 Microsoft Windows Update。 如需詳細資訊，請參閱[當您嘗試在 Windows 8 或 Windows Server 2012 安裝 .NET Framework 3.5 時產生錯誤碼](http://support.microsoft.com/kb/2734782)中的錯誤碼 0x800F0906 一節。<br /><br /> 另外，請參閱 Microsoft 支援服務網站上的[如何取得最新版的 Windows Update 代理程式以幫助管理電腦更新](http://go.microsoft.com/fwlink/p/?LinkId=248437)。|  
|安裝程式無法正確執行，因為這部電腦沒有可用的背景智慧型傳送服務 (BITS)。|請參閱 Microsoft 支援服務網站上的 [An update to prevent a Background Intelligent Transfer Service (BITS) crash on a Windows Vista-based computer](http://go.microsoft.com/fwlink/p/?LinkId=248680) (可防止背景智慧型傳送服務 (BITS) 在 Windows Vista 電腦上損毀的更新)。|  
|因為 Windows Update 發生錯誤並顯示錯誤碼 0x80070643 或 0x643，所以安裝程式可能無法正常執行。|請參閱 Microsoft 支援服務網站上的 [.NET Framework 更新安裝錯誤："0x80070643" 或 "0x643"](https://support.microsoft.com/kb/976982)。|  
|.NET Framework 4.5.*.x*/4.6*.x*/4.7 已經包含在此作業系統中。 您不需要安裝 .NET Framework 4.5*.x*/4.6*.x*/4.7 可轉散發套件。|不需執行任何動作。<br /><br /> 若要判斷系統上所安裝之 .NET Framework 的版本，請參閱[如何：判斷所安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)。 如需支援的作業系統，請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|這個作業系統不支援 .NET Framework 4.5*.x*/4.6*.x*/4.7。|如需支援的作業系統，請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。<br /><br /> 若是 .NET framework 在 Windows 7 上安裝失敗，此訊息通常表示未安裝 Windows 7 SP1。 在 Windows 7 系統中，.NET Framework 需要 Windows 7 SP1。 若您使用 Windows 7 而尚未安裝 Service Pack 1，就必須先加以安裝，才能安裝 .NET Framework。 如需安裝 Windows 7 SP1 的資訊，請參閱[了解如何安裝 Windows 7 Service Pack 1 (SP1)](http://windows.microsoft.com/en-us/windows7/install-windows-7-service-pack-1)。|  
|您的電腦目前執行的是 Windows Server 2008 作業系統的 Server Core 安裝。 .NET Framework 4.5.*x* 需要完整版的作業系統或 Server Core 2008 R2 SP1。 請安裝 Windows Server 2008 SP2 或 Windows Server 2008 R2 SP1 或 Server Core 2008 R2 SP1 的完整版本，並重新執行 .NET Framework 4.5.*x* 安裝程式。|Windows Server 2008 R2 SP1 (含) 以後版本的 Server Core 角色才有支援 .NET Framework。 請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|.NET Framework 4.5.*x* 已是這個作業系統的一部分，但目前處於關閉狀態 (僅限 [!INCLUDE[winserver8](../../../includes/winserver8-md.md)])。|請參閱 Windows 網站上的[開啟或關閉 Windows 功能](http://go.microsoft.com/fwlink/p/?LinkId=248438)。|  
|這個安裝程式需要 x86 電腦， 無法安裝在 x64 或 IA64 電腦上。|請參閱 MSDN Library 中的[系統需求](../../../docs/framework/get-started/system-requirements.md)。|  
|這個安裝程式需要 x64 或 x86 電腦， 無法安裝在 IA64 電腦上。|請參閱 MSDN Library 中的[系統需求](../../../docs/framework/get-started/system-requirements.md)。|  

<a name="compat"></a>
### <a name="program-compatibility-issues"></a>程式相容性問題

在 Windows 程式相容性模式中執行時，.NET Framework 4.5 或其點發行版本安裝會因為 1603 錯誤碼或封鎖而失敗。 [程式相容性助理] 會指出 .NET Framework 可能沒有正確安裝，並提示您使用建議的設定 (程式相容性模式) 來重新安裝。 也有可能先前試圖執行 .NET Framework 安裝程式時失敗或取消了，而已經由「程式相容性助理」設定了程式相容性模式。

.NET Framework 安裝程式無法在程式相容性模式中執行。 若要解決這個封鎖問題，您必須確保未在 [登錄編輯程式] 中啟用全系統的相容性模式設定：

1. 選擇 [開始] 按鈕，然後選擇 [執行]。

1. 在 [執行] 對話方塊中，鍵入 "regedit"，然後選擇 [確定]。

1. 在 [登錄編輯程式] 中，瀏覽至下列子機碼：

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Compatibility Assistant\Persisted

   - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers

1. 在 [名稱] 欄中，根據安裝的版本尋找 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、4.5.1、4.5.2、4.6、4.6.1 或 4.6.2 下載名稱，然後刪除這些項目。 如需下載名稱，請參閱[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)一文。

1. 請重新執行 4.5、4.5.1、4.5.2、4.6、4.6.1、4.6.2 或 4.7 版的 .NET Framework 安裝程式。

## <a name="see-also"></a>請參閱

[安裝適用於開發人員的 .NET Framework](../../../docs/framework/install/guide-for-developers.md)   
[如何：判斷安裝的 .NET Framework 版本](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
[版本和相依性](../../../docs/framework/migration-guide/versions-and-dependencies.md)

