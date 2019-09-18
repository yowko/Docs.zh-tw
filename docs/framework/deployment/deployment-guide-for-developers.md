---
title: .NET Framework 開發人員部署手冊
ms.custom: updateeachrelease
ms.date: 04/18/2019
helpviewer_keywords:
- developer's guide, deploying .NET Framework
- deployment [.NET Framework], developer's guide
ms.assetid: 094d043e-33c4-40ba-a503-e0b20b55f4cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2229dca07a3a723babe5bf202ce5ddc0c77a7374
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052196"
---
# <a name="net-framework-deployment-guide-for-developers"></a>.NET Framework 開發人員部署手冊
開發人員若要讓自己的應用程式一起安裝從 .NET Framework 4.5 至 [!INCLUDE[net_current](../../../includes/net-current-version.md)] 的任何 .NET Framework 版本，可參考本主題提供的資訊。

如需下載連結，請參閱[可轉散發套件](#redistributable-packages)一節。 您也可以從下列 Microsoft 下載中心頁面下載可轉散發套件和語言套件：

- 適用於所有作業系統的 .NET Framework 4.8 ([Web 安裝程式](http://go.microsoft.com/fwlink/?LinkId=2085155)或[離線安裝程式](https://go.microsoft.com/fwlink/?linkid=2088631))

- 適用於所有作業系統的 .NET Framework 4.7.2 ([Web 安裝程式](https://go.microsoft.com/fwlink/?LinkId=863262)或[離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=863265))

- 適用於所有作業系統的 .NET Framework 4.7.1 ([Web 安裝程式](https://go.microsoft.com/fwlink/?LinkId=852095) 或 [離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=852107))

- 適用於所有作業系統的 .NET Framework 4.7 ([Web 安裝程式](https://go.microsoft.com/fwlink/?LinkId=825299) 或 [離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=825303))

- 適用於所有作業系統的 .NET Framework 4.6.2 ([Web 安裝程式](https://go.microsoft.com/fwlink/?LinkId=780597)或[離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=780601))

- 適用於所有作業系統的 .NET Framework 4.6.1 ([Web 安裝程式](https://go.microsoft.com/fwlink/?LinkId=671729)或[離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=671744))

- 適用於所有作業系統的 .NET Framework 4.6 ([Web 安裝程式](https://go.microsoft.com/fwlink/?LinkId=528222)或[離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=528232))

- 適用於所有作業系統的 .NET Framework 4.5.2 ([Web 安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=397703) 或 [離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=397706))

- 適用於所有作業系統的 .NET Framework 4.5.1 ([Web 安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=310158) 或 [離線安裝程式](https://go.microsoft.com/fwlink/p/?LinkId=310159))

- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)

 重要注意事項：

> [!NOTE]
> 片語「.NET Framework 4.5 和其小數點版本」指的是 .NET Framework 4.5 及所有更新版本。

- 從 .NET Framework 4.5.1 至 [!INCLUDE[net_current](../../../includes/net-current-version.md)] 的 .NET Framework 版本是 .NET Framework 4.5 的就地更新；亦即，它們會使用相同的執行階段版本，但組件版本會更新並包含新的型別和成員。

- .NET Framework 4.5 及其小數點版本是以 .NET Framework 4 為基礎累加建置。 當您在已安裝 .NET Framework 4 的系統上安裝 .NET Framework 4.5 或其小數點版本時，第 4 版組件就會被新版本取代。

- 如果您參考應用程式中的 Microsoft [Out-of-Band 封裝](../get-started/the-net-framework-and-out-of-band-releases.md) ，應用程式封裝中就會包含該組件。

- 您必須具有系統管理員權限才能安裝 .NET Framework 4.5 及其小數點版本。

- .NET Framework 4.5 隨附於 [!INCLUDE[win8](../../../includes/win8-md.md)] 和 [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] 中，因此在這些作業系統上不需要隨您的應用程式再次部署它。 同樣地，.NET Framework 4.5.1 會隨附於 [!INCLUDE[win81](../../../includes/win81-md.md)] 和 Windows Server 2012 R2 中。 所有作業系統中都不包含 .NET Framework 4.5.2。 .NET Framework 4.6 隨附於 Windows 10 中，.NET Framework 4.6.1 隨附於 Windows 10 年 11 月更新中，而 .NET Framework 4.6.2 則隨附於 Windows 10 年度更新版中。  .NET Framework 4.7 隨附於 Windows 10 Creators Update 中，.NET Framework 4.7.1 隨附於 Windows 10 Fall Creators Update 中，.NET Framework 4.7.2 則隨附於 Windows 10 2018 年 10 月更新與 Windows 10 2018 年 4 月更新中。 .NET Framework 4.8 已隨附於 Windows 10 2019 年 5 月更新中。 如需硬體和軟體需求的完整清單，請參閱[系統需求](../get-started/system-requirements.md)。

- 從 .NET Framework 4.5 開始，您的使用者可以在安裝過程中檢視執行中的 .NET Framework 應用程式清單，並輕鬆地將它們關閉。 這有助於避免系統因安裝 .NET Framework 而重新啟動。 請參閱 [減少系統重新啟動](reducing-system-restarts.md)。

- 解除安裝 .NET Framework 4.5 或其小數點版本的其中一個，也會移除已存在的 .NET Framework 4 檔案。 如果您想要回到 .NET Framework 4，則必須重新安裝它及其所有更新。 (請參閱 [安裝 .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5a4x27ek(v=vs.100)))。

- .NET Framework 4.5 可轉散發套件已於 2012 年 10 月 9 日更新，更正了與數位憑證時間戳記錯誤相關的問題，這個問題會造成 Microsoft 所產生和簽署之檔案中的數位簽章提前過期。 如果您先前安裝了日期為 2012 年 8 月 16 日的 .NET Framework 4.5 可轉散發套件，我們建議您使用 [Microsoft 下載中心](https://go.microsoft.com/fwlink/p/?LinkId=245484)最新的可轉散發套件進行更新。 如需這個問題的詳細資訊，請參閱 [Microsoft 安全性摘要報告 2749655](https://docs.microsoft.com/security-updates/SecurityAdvisories/2012/2749655)。

如需系統管理員如何在網路上部署 .NET Framework 及其系統相依性的詳細資訊，請參閱[系統管理員部署手冊](guide-for-administrators.md)。

## <a name="deployment-options-for-your-app"></a>應用程式的部署選項

當您準備將應用程式發行到 Web 伺服器或其他集中位置供使用者進行安裝時，有數種部署方法可供您選擇。 其中有些方法是 Visual Studio 所提供。 下表列出應用程式的部署選項，並指定支援每個選項的 .NET Framework 可轉散發套件。 除了這些選項之外，您還可以為應用程式撰寫自訂安裝程式，如需詳細資訊，請參閱 [將 .NET Framework 安裝鏈結至您的應用程式安裝](#chaining)一節。

|應用程式的部署策略|可用的部署方法|可供使用的 .NET Framework 可轉散發套件|
|--------------------------------------|----------------------------------|-------------------------------------------|
|從 Web 安裝|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX 工具組](#wix)<br />- [手動安裝](#installing_manually)|[Web installer](#redistributable-packages)|
|從光碟安裝|- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [WiX 工具組](#wix)<br />- [手動安裝](#installing_manually)|[Offline installer](#redistributable-packages)|
|從區域網路安裝 (適用於企業應用程式)|- [ClickOnce](#clickonce-deployment)|[Web 安裝程式](#redistributable-packages) (如需相關限制，請參閱 [ClickOnce](#clickonce-deployment) ) 或 [離線安裝程式](#redistributable-packages)|

## <a name="redistributable-packages"></a>可轉散發套件

.NET Framework 可透過兩種可轉散發套件提供：Web 安裝程式 (啟動載入器) 和離線安裝程式 (獨立可轉散發套件)。 下表將比較這兩種套件。

||Web 安裝程式|離線安裝程式|
|-|-------------------|-----------------------|
|下載檔案|.NET Framework 4.8： <br/>[ndp48-web.exe](https://go.microsoft.com/fwlink/?LinkId=2085155)<br/><br/>.NET Framework 4.7.2： <br/>[NDP472-KB4054531-Web.exe](https://go.microsoft.com/fwlink/?LinkId=863262)<br/><br/>.NET Framework 4.7.1： <br/>[NDP471-KB4033344-Web.exe](https://go.microsoft.com/fwlink/?LinkId=852092)<br/><br/>.NET Framework 4.7： <br />[NDP47-KB3186500-Web.exe](https://go.microsoft.com/fwlink/?LinkId=825298) <br /><br />.NET Framework 4.6.2： <br />[NDP462-KB3151802-Web.exe](https://go.microsoft.com/fwlink/?LinkId=780596)<br /><br /> .NET Framework 4.6.1：<br />[NDP461-KB3102438-Web.exe](https://go.microsoft.com/fwlink/?LinkId=671728)<br /><br /> .NET Framework 4.6：<br />[NDP46-KB3045560-Web.exe](https://go.microsoft.com/fwlink/?LinkId=528222)<br /><br /> .NET Framework 4.5.2： <br />[NDP452-KB2901954-Web.exe](https://go.microsoft.com/fwlink/?LinkId=397707)<br /><br /> .NET Framework 4.5.1： <br />[NDP451-KB2859818-Web.exe](https://go.microsoft.com/fwlink/?LinkId=322115)<br /><br /> .NET Framework 4.5： <br />[dotNetFx45_Full_setup.exe](https://go.microsoft.com/fwlink/?LinkId=225704)|.NET Framework 4.8： <br/>[NDP48-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?linkid=2088631)<br/><br/>.NET Framework 4.7.2： <br/>[NDP472-KB4054530-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=863265)<br/><br/>.NET Framework 4.7.1： <br />[NDP471-KB4033342-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=852104) <br /><br />.NET Framework 4.7： <br />[NDP47-KB3186497-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=825302) <br /><br />.NET Framework 4.6.2： <br />[NDP462-KB3151800-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=780600)<br /><br /> .NET Framework 4.6.1： <br />[NDP461-KB3102436-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=671743)<br /><br /> .NET Framework 4.6： <br />[NDP46-KB3045557-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=528232)<br /><br /> .NET Framework 4.5.2： <br />[NDP452-KB2901907-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=397708)<br /><br /> .NET Framework 4.5.1： <br />[NDP451-KB2858728-x86-x64-AllOS-ENU.exe](https://go.microsoft.com/fwlink/?LinkId=322116)<br /><br /> .NET Framework 4.5： <br />[dotNetFx45_Full_x86_x64.exe](https://go.microsoft.com/fwlink/?LinkId=225702)|
|是否需要網際網路連線？|是|否|
|下載大小|較小 (僅包含目標平台的安裝程式)*|較大*|
|語言套件|包含**|除非您使用以所有作業系統為目標的套件，否則必須 [單獨安裝](#chain_langpack)。|
|部署方法|支援所有方法：<br /><br />- [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [手動安裝](#installing_manually)<br />- [自訂安裝 (鏈結)](#chaining)|支援所有方法：<br /><br /> - [ClickOnce](#clickonce-deployment)<br />- [InstallAware](#installaware-deployment)<br />- [InstallShield](#installshield-deployment)<br />- [Windows Installer XML (WiX)](#wix)<br />- [手動安裝](#installing_manually)<br />- [自訂安裝 (鏈結)](#chaining)|
|下載 ClickOnce 部署的位置|Microsoft 下載中心：<br /><br /> - [.NET Framework 4.8](https://go.microsoft.com/fwlink/?LinkId=2085155) <br/> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863262) <br/> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852092) <br/> - [.NET Framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825298) <br/> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780596)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671728)<br />- [.NET Framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528222)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/?LinkId=397703)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310158)<br />- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|您的伺服器或 Microsoft 下載中心：<br /><br /> - [.NET Framework 4.8](https://go.microsoft.com/fwlink/?linkid=2088631)<br /> - [.NET Framework 4.7.2](https://go.microsoft.com/fwlink/?LinkId=863265)<br /> - [.NET Framework 4.7.1](https://go.microsoft.com/fwlink/?LinkId=852104)<br /> - [.NET Framework 4.7](https://go.microsoft.com/fwlink/?LinkId=825302)<br /> - [.NET Framework 4.6.2](https://go.microsoft.com/fwlink/?LinkId=780600)<br />- [.NET Framework 4.6.1](https://go.microsoft.com/fwlink/?LinkId=671743)<br />- [.NET Framework 4.6](https://go.microsoft.com/fwlink/?LinkId=528232)<br />- [.NET Framework 4.5.2](https://go.microsoft.com/fwlink/p/?LinkId=397706)<br />- [.NET Framework 4.5.1](https://go.microsoft.com/fwlink/p/?LinkId=310159)<br />- [.NET Framework 4.5](https://go.microsoft.com/fwlink/p/?LinkId=245484)|

\* 離線安裝程式比較大，因為其中包含適用所有目標平台的元件。 當您完成執行安裝程式後，Windows 作業系統只會快取所使用的安裝程式。 如果在安裝完成之後刪除離線安裝程式，則使用的磁碟空間與 Web 安裝程式所使用的磁碟空間相同。 如果用來建立應用程式安裝程式的工具 (例如，[InstallAware](#installaware-deployment) 或 [InstallShield](#installshield-deployment)) 提供了安裝程式檔案資料夾，而這個資料夾會在安裝完成後移除，則將離線安裝程式放在安裝程式資料夾中，便可自動刪除離線安裝程式。

\*\* 如果您使用 Web 安裝程式搭配自訂安裝程式，則可以使用以使用者的多語系使用者介面 (MUI) 設定為基礎的預設語言設定，或是使用命令列的 `/LCID` 選項指定另一個語言套件。 例如，請參閱 [使用預設的 .NET Framework UI 進行鏈結](#chaining_default) 一節。

## <a name="deployment-methods"></a>部署方法

 可用的部署方法有四種：

- 您可以設定 .NET Framework 的相依性。 您可以使用下列其中一種方法，在應用程式安裝中將 .NET Framework 指定為必要條件：

  - 使用 [ClickOnce 部署](#clickonce-deployment) (Visual Studio 所提供)

  - 建立 [InstallAware 專案](#installaware-deployment) (有免費版本可供 Visual Studio 使用者使用)

  - 建立 [InstallShield 專案](#installshield-deployment) (Visual Studio 所提供)

  - 使用 [Windows Installer XML (WiX) 工具組](#wix)

- 您可以要求使用者 [手動安裝 .NET Framework](#installing_manually)。

- 您可以在應用程式安裝中鏈結 (包含) .NET Framework 安裝程序，並決定如何處理 .NET Framework 安裝經驗：

  - [使用預設 UI](#chaining_default)。 讓 .NET Framework 安裝程式提供安裝經驗。

  - [自訂 UI](#chaining_custom) 以提供一致的安裝經驗，並監控 .NET Framework 安裝進度。

以下各節將詳細討論這些部署方法。

## <a name="setting-a-dependency-on-the-net-framework"></a>設定 .NET Framework 的相依性

如果您使用 ClickOnce、InstallAware、InstallShield 或 WiX 來部署應用程式，便可以加入 .NET Framework 的相依性，讓它隨應用程式一併安裝。

### <a name="clickonce-deployment"></a>ClickOnce 部署

ClickOnce 部署適用於以 Visual Basic 和 Visual C# 建立的專案，但不適用於 Visual C++ 建立的專案。

在 Visual Studio 中，選擇 ClickOnce 部署並加入 .NET Framework 的相依性：

1. 開啟您要發行的應用程式專案。

2. 在 [方案總管] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。

3. 選擇 [ **發行** ] 窗格。

4. 選擇 [ **必要條件** ] 按鈕。

5. 在 [ **必要條件** ] 對話方塊中，確定已選取 [ **建立安裝程式以安裝必要條件元件** ] 核取方塊。

6. 在必要條件清單中，找出並選取您用來建置專案的 .NET Framework 版本。

7. 選擇選項以指定必要條件的來源位置，然後選擇 [ **確定**]。

     如果您提供 .NET Framework 下載位置的 URL，就可以指定 Microsoft 下載中心網站或是您自己的網站。 如果您要將可轉散發套件放在自己的伺服器上，該套件必須是離線安裝程式，而不是 Web 安裝程式。 您只能連結至 Microsoft 下載中心上的 Web 安裝程式。 URL 也可以指定要用來散發您的應用程式的光碟。

8. 在 [ **屬性頁** ] 對話方塊中，選擇 [ **確定**]。

<a name="installaware"></a>

### <a name="installaware-deployment"></a>InstallAware 部署

InstallAware 可以從單一來源來建立 Windows 應用程式 (APPX)、Windows Installer (MSI)、機器碼 (EXE) 與 App-V (Application Virtualization) 套件。 輕鬆地在您的安裝程式中[包含任何版本的 .NET Framework](https://www.installaware.com/one-click-pre-requisite-installer.htm) \(英文\)，並可選擇[編輯預設的指令碼](https://www.installaware.com/msicode.htm) \(英文\) 來自訂安裝。 例如，InstallAware 會在 Windows 7 上預先安裝憑證。若無此憑證，.NET Framework 4.7 安裝程式將會失敗。 如需有關 InstallAware 的詳細資訊，請參閱[適用於 Windows Installer 的 InstallAware](https://www.installaware.com/) \(英文\) 網站。

### <a name="installshield-deployment"></a>InstallShield 部署

在 Visual Studio 中，選擇 InstallShield 部署並加入 .NET Framework 的相依性：

1. 在 Visual Studio 功能表列上，選擇 [ **檔案**]、[ **新增**]、[ **專案**]。

2. 在 [ **新增專案** ] 對話方塊的左窗格中，依序選擇 [ **其他專案類型**]、[ **安裝和部署**]、[ **InstallShield LE**]。

3. 在 [ **名稱** ] 方塊中輸入您的專案名稱，然後選擇 [ **確定**]。

4. 如果您初次建立安裝程式和部署專案，請選擇 [移至 InstallShield] 或 [啟用 InstallShield 限量版]，以下載您 Microsoft Visual Studio 版本的 InstallShield 限量版。 重新啟動 Visual Studio。

5. 移至 [ **專案助理** ] 精靈，並選擇 [ **應用程式檔案** ] 以加入 [專案輸出]。 您可以使用這個精靈設定其他專案屬性。

6. 移至 [ **安裝需求** ] 然後選取作業系統以及要安裝的 .NET Framework 版本。

7. 開啟安裝專案的捷徑功能表，然後選擇 [ **建置**]。

<a name="wix"></a>

### <a name="windows-installer-xml-wix-deployment"></a>Windows Installer XML (WiX) 部署

Windows Installer XML (WiX) 工具組會從 XML 原始程式碼建置 Windows 安裝套件。 WiX 支援命令列環境，該環境可整合至您的建置程序中，用來建置 MSI 與 MSM 安裝封裝。 您可以使用 WiX [將 .NET Framework 指定為必要條件](http://wixtoolset.org/documentation/manual/v3/howtos/redistributables_and_install_checks/install_dotnet.html)，或是 [建立 Chainer](http://wixtoolset.org/documentation/manual/v3/xsd/wix/exepackage.html) ，以便完全掌控 .NET Framework 部署經驗。 如需 WiX 的詳細資訊，請參閱 [Windows Installer XML (WiX) 工具組](http://wixtoolset.org/) 網站。

<a name="installing_manually"></a>

## <a name="installing-the-net-framework-manually"></a>手動安裝 .NET Framework

在某些情況下，隨應用程式自動安裝 .NET Framework 並不是那麼實際。 在這種情況下，您可以讓使用者自己安裝 .NET Framework。 可轉散發套件可隨 [兩種套件](#redistributable-packages)提供。 所以請在安裝過程中提供指示，讓使用者知道應該如何找到和安裝 .NET Framework。

<a name="chaining"></a>

## <a name="chaining-the-net-framework-installation-to-your-apps-setup"></a>將 .NET Framework 安裝鏈結至您的應用程式安裝

如果您要為應用程式建立自訂安裝程式，則可以在應用程式的安裝程序中鏈結 (包含) .NET Framework 安裝程序。 鏈結提供了兩個用於安裝 .NET Framework 的 UI 選項：

- 使用 .NET Framework 安裝程式所提供的預設 UI。

- 建立 .NET Framework 安裝的自訂 UI，以便與您的應用程式安裝程式保持一致。

這兩種方法都可讓您使用 Web 安裝程式或離線安裝程式。 每個套件都有其優點：

- 如果您使用 Web 安裝程式，.NET Framework 安裝程序將決定必要的安裝套件，並且只從 Web 下載及安裝該套件。

- 如果您使用離線安裝程式，您可以將一組完整的 .NET Framework 安裝套件包含在您的轉散發媒體中，如此使用者就不需要在安裝過程中從 Web 下載任何其他檔案。

<a name="chaining_default"></a>

### <a name="chaining-by-using-the-default-net-framework-ui"></a>使用預設的 .NET Framework UI 進行鏈結

若要以無訊息模式鏈結 .NET Framework 安裝程序並且讓 .NET Framework 安裝程式提供 UI，請將下列命令加入至您的安裝程式：

`<.NET Framework redistributable> /q /norestart /ChainingPackage <PackageName>`

例如，如果您的可執行程式為 Contoso.exe，而您想要以無訊息模式安裝 .NET Framework 4.5 離線可轉散發套件，請使用下列命令：

`dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage Contoso`

您可以使用其他命令列選項自訂安裝。 例如：

- 若要提供一種方法讓使用者關閉執行中的 .NET Framework 應用程式，以減少系統重新啟動的次數，可設定被動模式並使用 `/showrmui` 選項，如下所示：

    `dotNetFx45_Full_x86_x64.exe /norestart /passive /showrmui /ChainingPackage Contoso`

     這個命令可讓重新啟動管理員顯示訊息方塊，讓使用者有機會先關閉 .NET Framework 應用程式再安裝 .NET Framework。

- 如果您要使用 Web 安裝程式，則可以使用 `/LCID` 選項指定語言套件。 例如，若要將 .NET Framework 4.5 Web 安裝程式鏈結至 Contoso 安裝程式，並且安裝日文語言套件，請將下列命令加入至您的應用程式安裝程序：

    `dotNetFx45_Full_setup.exe /q /norestart /ChainingPackage Contoso /LCID 1041`

     如果您省略 `/LCID` 選項，安裝程式將會安裝符合使用者 MUI 設定的語言套件。

    > [!NOTE]
    > 不同語言套件的發行日期可能不同。 如果下載中心未提供您指定的語言套件，安裝程式將會安裝不含語言套件的 .NET Framework。 如果使用者電腦上已安裝 .NET Framework，則安裝程式只會安裝語言套件。

如需選項的完整清單，請參閱 [命令列選項](#command-line-options) 一節。

如需常見的傳回碼，請參閱 [傳回碼](#return-codes) 一節。

<a name="chaining_custom"></a>

### <a name="chaining-by-using-a-custom-ui"></a>使用自訂 UI 進行鏈結

如果您有自訂安裝套件，您可能想要以無訊息模式啟動並追蹤 .NET Framework 安裝程式，同時顯示您自己的安裝進度檢視。 如果您想要這樣做，請確定您的程式碼涵蓋下列內容：

- 檢查 [.NET Framework 的硬體和軟體需求](../get-started/system-requirements.md)。

- [偵測](#detect_net) 使用者電腦上是否已安裝正確的 .NET Framework 版本。

    > [!IMPORTANT]
    > 在判斷是否已安裝正確版本的 .NET Framework 時，您應該檢查是否已安裝目標版本「或」 更新的版本，而不是是否已安裝您的目標版本。 換句話說，您應該評估從登錄擷取的版本機碼是否大於或等於您的目標版本的版本機碼，而「不是」 它是否等於目標版本的版本機碼。

- [偵測](#detecting-the-language-packs) 使用者電腦上是否已安裝語言套件。

- 如果您想要控制部署，請以無訊息模式啟動並追蹤 .NET Framework 安裝程序 (請參閱[如何：取得 .NET Framework 4.5 安裝程式的進度](how-to-get-progress-from-the-dotnet-installer.md))。

- 如果您要部署離線安裝程式，請 [分別鏈結語言套件](#chain_langpack)。

- 使用 [命令列選項](#command-line-options)自訂部署。 例如，如果您要鏈結 .NET Framework Web 安裝程式，但是想要覆寫預設語言套件，請使用 `/LCID` 選項，如前一節所述。

- [疑難排解](#troubleshooting)。

<a name="detect_net"></a>

### <a name="detecting-the-net-framework"></a>偵測 .NET Framework

.NET Framework 安裝程式會在安裝成功時寫入登錄機碼。 您可以測試是否已安裝 .NET Framework 4.5 或更新版本，方法是檢查登錄中的 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` 資料夾是否有名為 `Release` 的 `DWORD` 值。 (請注意，"NET Framework Setup" 不是以句號開頭。)若這個機碼存在，表示該電腦上已安娤 .NET Framework 4.5 或更新版本。 `Release` 的值會指出所安裝的 .NET Framework 版本。

> [!IMPORTANT]
> 當您嘗試偵測是否有特定版本時，您應該檢查是否有值  **大於或等於** 版本關鍵字值。

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Version|Release DWORD 的值|
|-------------|--------------------------------|
|安裝在 Windows 10 2019 年 5 月更新上的 .NET Framework 4.8|528040|
|安裝在 Windows 10 2019 年 5 月更新以外的所有 OS 版本上的 .NET Framework 4.8|528049|
|Windows 10 2018 年 4 月更新及 Windows Server，版本 1803 上安裝的 .NET Framework 4.7.2|461808|
|Windows 10 2018 年 4 月更新及 Windows Server 1803 版以外所有 OS 版本上安裝的 .NET Framework 4.7.2。 這包括 Windows 10 2018 年 10 月更新。 |461814|
|Windows 10 Fall Creators Update 及 Windows Server，版本 1709 上安裝的 .NET Framework 4.7.1|461308|
|Windows 10 Fall Creators Update 及 Windows Server，版本 1709 以外所有 OS 版本上安裝的 .NET Framework 4.7.1|461310|
|Windows 10 Creators Update 上安裝的 .NET Framework 4.7|460798|
|.NET Framework 4.7 安裝在 Windows 10 Creators Update 以外的所有作業系統版本|460805|
|安裝於 Windows 10 Anniversary Edition 和 Windows Server 2016 上的 .NET Framework 4.6.2|394802|
|安裝於 Windows 10 Anniversary Edition 和 Windows Server 2016 以外的所有 OS 版本上的 .NET Framework 4.6.2|394806|
|安裝在 Windows 10 11 月更新上的 .NET Framework 4.6.1|394254|
|安裝在 Windows 10 11 月更新以外的所有 OS 版本上的 .NET Framework 4.6.1|394271|
|安裝在 Windows 10 上的 .NET Framework 4.6|393295|
|安裝在 Windows 10 以外的所有 OS 版本上的 .NET Framework 4.6|393297|
|.NET Framework 4.5.2|379893|
|隨 [!INCLUDE[win81](../../../includes/win81-md.md)] 或 Windows Server 2012 R2 安裝的 .NET Framework 4.5.1|378675|
|安裝在 [!INCLUDE[win8](../../../includes/win8-md.md)]、Windows 7 上的 .NET Framework 4.5.1|378758|
|.NET Framework 4.5|378389|

### <a name="detecting-the-language-packs"></a>刪除語言套件

您可以測試是否安裝特定的語言套件，方法是檢查登錄中 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\\*LCID* 資料夾內名為 `Release` 的 DWORD 值。 (請注意，"NET Framework Setup" 不是以句號開頭。)*LCID* 可指定地區設定識別碼，請參閱[支援的語言](#supported-languages)，以取得這些項目的清單。

例如，若要偵測是否已安裝完整的日文語言套件（LCID = 1041），請從登錄中取出下列已命名的值：

| | |
|-|-|
| Key | HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\1041 |
| 名稱 | 版本 |
| 類型 | DWORD |

若要判斷是否已針對 .NET Framework 從 4.5 到 4.7.2 的特定版本安裝語言套件的最終發行版本，請檢查 RELEASE 機碼 DWORD 的值，如前一節[偵測 .NET Framework](#detect_net) 中所述。

<a name="chain_langpack"></a>

### <a name="chaining-the-language-packs-to-your-app-setup"></a>將語言套件鏈結至您的應用程式安裝

.NET Framework 提供了一組獨立的語言套件可執行檔，其中包含特定文化特性的當地語系化資源。 語言套件可從 Microsoft 下載中心取得：

- [.NET Framework 4.8 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=2086170)

- [.NET Framework 4.7.2 語言套件](https://go.microsoft.com/fwlink/?LinkId=863275)

- [.NET Framework 4.7.1 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=852090)

- [.NET Framework 4.7 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=825306)

- [.NET Framework 4.6.2 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=780604)

- [.NET Framework 4.6.1 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=671747)

- [.NET Framework 4.6 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=528314)

- [.NET Framework 4.5.2 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=397701)

- [.NET Framework 4.5.1 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=322101)

- [.NET Framework 4.5 語言套件](https://go.microsoft.com/fwlink/p/?LinkId=245451)

> [!IMPORTANT]
> 語言套件並不包含執行應用程式所需的 .NET Framework 元件，因此在安裝語言套件之前，必須先使用 Web 或離線安裝程式安裝 .NET Framework。

從 .NET Framework 4.5.1 開始，套件名稱會採用 NDP<`version`>-KB<`number`>-x86-x64-AllOS-<`culture`>.exe 的格式，其中 `version` 是 .NET Framework 的版本號碼、`number` 是 Microsoft 知識庫文章編號，而 `culture` 則指定[國家/地區](#supported-languages)。 `NDP452-KB2901907-x86-x64-AllOS-JPN.exe`就是其中一個套件的範例。 封裝名稱列在本文章稍早的 [Redistributable Packages](#redistributable-packages) 一節。

若要隨 .NET Framework 離線安裝程式安裝語言套件，您必須將它鏈結至您的應用程式安裝。 例如，若要同時部署 .NET Framework 4.5.1 離線安裝程式與日文語言套件，請使用下列命令：

`NDP451-KB2858728-x86-x64-AllOS-JPN.exe /q /norestart /ChainingPackage <ProductName>`

如果您使用 Web 安裝程式，則不需要鏈結語言套件，安裝程式將會安裝符合使用者 MUI 設定的語言套件。 如果您要安裝不同的語言，可以使用 `/LCID` 選項指定語言套件。

如需命令列選項的完整清單，請參閱 [命令列選項](#command-line-options) 一節。

### <a name="troubleshooting"></a>疑難排解

#### <a name="return-codes"></a>傳回碼

下表列出 .NET Framework 可轉散發安裝程式最常見的傳回碼。 所有版本的安裝程式的傳回碼都相同。 如需詳細資訊的連結，請參閱下一節。

|傳回碼|說明|
|-----------------|-----------------|
|0|安裝已順利完成。|
|1602|使用者已取消安裝。|
|1603|安裝期間發生嚴重錯誤。|
|1641|需要重新開機才能完成安裝。 這個訊息表示成功。|
|3010|需要重新開機才能完成安裝。 這個訊息表示成功。|
|5100|使用者的電腦不符合系統需求。|

#### <a name="download-error-codes"></a>下載錯誤碼

請參閱下列內容：

- [背景智慧型傳送服務 (BITS) 錯誤碼](https://go.microsoft.com/fwlink/?LinkId=180946)

- [URL Moniker 錯誤碼](https://go.microsoft.com/fwlink/?LinkId=180947)

- [WinHttp 錯誤碼](https://go.microsoft.com/fwlink/?LinkId=180948)

#### <a name="other-error-codes"></a>其他錯誤碼

請參閱下列內容：

- [Windows 安裝程式錯誤碼](https://go.microsoft.com/fwlink/?LinkId=180949)

- [Windows Update 代理程式結果碼](https://go.microsoft.com/fwlink/?LinkId=180951)

## <a name="uninstalling-the-net-framework"></a>解除安裝 .NET Framework

從 [!INCLUDE[win8](../../../includes/win8-md.md)] 開始，您可以使用 [控制台] 中的 [開啟或關閉 Windows 功能]，將 .NET Framework 4.5 或其小數點版本解除安裝。 在舊版 Windows 中，您可以使用 [控制台] 中的 [新增或移除程式]，將 .NET Framework 4.5 或其小數點版本解除安裝。

> [!IMPORTANT]
> 針對 Windows 7 和舊版作業系統，解除安裝 .NET Framework 4.5.1、4.5.2、4.6、4.6.1、4.6.2、4.7、4.7.1、4.7.2, 或 4.8 不會還原 .NET Framework 4.5 檔案，而解除安裝 .NET Framework 4.5 不會還原 .NET Framework 4 檔案。 如果您想要還原為舊版，則必須重新安裝舊版及其所有更新。

## <a name="appendix"></a>附錄

### <a name="command-line-options"></a>命令列選項

下表列出您將 .NET Framework 4.5 可轉散發套件鏈結至您的應用程式安裝程式時，可以包含的選項。

|選項|說明|
|------------|-----------------|
|**/CEIPConsent**|覆寫預設的行為並傳送匿名意見給 Microsoft 以協助改善未來的部署經驗。 只有當安裝程式提示同意，同時使用者授與權限傳送匿名意見給 Microsoft 時，才能使用此選項。|
|**/chainingpackage** `packageName`|指定執行鏈結之可執行檔的名稱。 此資訊會以匿名意見的形式傳送給 Microsoft 以協助改善未來的部署經驗。<br /><br /> 如果封裝名稱包含空格，請使用雙引號做為分隔符號，例如： **/chainingpackage "Lucerne Publishing"** 。 如需鏈結套件的範例，請參閱 MSDN Library 中的 [從安裝套件取得進度資訊](https://go.microsoft.com/fwlink/?LinkId=181926) 。|
|**/LCID**  `LCID`<br /><br /> 其中， `LCID` 可指定地區設定識別碼 (請參閱 [支援的語言](#supported-languages))。|安裝 `LCID` 指定的語言套件並強制以該語言顯示 UI (除非已設定無訊息模式)。<br /><br /> 對於 Web 安裝程式，此選項會從 Web 鏈結安裝語言套件。 **注意：** 此選項只適用於 Web 安裝程式。|
|**/log** `file` &#124; `folder`|指定記錄檔的位置。 預設為程序的暫存資料夾，而預設檔案名稱將會根據套件。 如果副檔名是 .txt，則會產生文字記錄檔。 如果您指定其他副檔名或未指定副檔名，則會建立 HTML 記錄檔。|
|**/msioptions**|指定針對 .msi 和 .msp 項目傳遞的選項，例如： `/msioptions "PROPERTY1='Value'"`。|
|**/norestart**|避免安裝程式自動重新開機。 如果您使用此選項，則鏈結應用程式必須擷取傳回碼並處理重新開機 (請參閱 MSDN Library 中的 [從安裝套件取得進度資訊](https://go.microsoft.com/fwlink/?LinkId=179606) )。|
|**/passive**|設定被動模式。 顯示進度列，表示安裝正在進行，但不會對使用者顯示任何提示或錯誤訊息。 在此模式中，當安裝程式進行鏈結時，鏈結套件必須處理 [傳回碼](#return-codes)。|
|**/pipe**|建立通訊通道，讓鏈結套件能夠取得進度。|
|**/promptrestart**|(僅限被動模式) 如果安裝程式需要重新啟動，則會提示使用者。 如果需要重新啟動，此選項會需要使用者互動。|
|**/q**|設定無訊息模式。|
|**/repair**|觸發修復功能。|
|**/serialdownload**|強制在套件下載完成後才進行安裝。|
|**/showfinalerror**|設定被動模式。 只有在安裝失敗時才顯示錯誤。 但如果安裝未成功，此選項需要使用者互動。|
|**/showrmui**|只可搭配 **/passive** 選項使用。 顯示訊息方塊，提示使用者關閉目前正在執行的 .NET Framework 應用程式。 此訊息方塊在被動與非被動模式中的行為相同。|
|**/uninstall**|解除安裝 .NET Framework 可轉散發套件。|

### <a name="supported-languages"></a>支援的語言

下表列出可供 .NET Framework 4.5 及其小數點版本使用的 .NET Framework 語言套件。

|LCID|語言 – 國家/地區|culture|
|----------|--------------------------------|-------------|
|1025|阿拉伯文 - 沙烏地阿拉伯|ar|
|1028|中文 – 繁體|zh-Hant|
|1029|捷克文|cs|
|1030|丹麥文|da|
|1031|德文 – 德國|de|
|1032|希臘文|el|
|1035|芬蘭文|fi|
|1036|法文 – 法國|fr|
|1037|Hebrew|he|
|1038|匈牙利文|hu|
|1040|義大利文 – 義大利|it|
|1041|日文|ja|
|1042|韓文|ko|
|1043|荷蘭文 – 荷蘭|nl|
|1044|挪威文 (巴克摩)|否|
|1045|波蘭文|pl|
|1046|葡萄牙文 – 巴西|pt-BR|
|1049|俄文|ru|
|1053|瑞典文|sv|
|1055|土耳其文|tr|
|2052|中文 – 簡體|zh-Hans|
|2070|葡萄牙文 (葡萄牙)|pt-PT|
|3082|西班牙文 - 西班牙 (現代排序)|es|

## <a name="see-also"></a>另請參閱

- [系統管理員部署手冊](guide-for-administrators.md)
- [系統需求](../get-started/system-requirements.md)
- [安裝適用於開發人員的 .NET Framework](../install/guide-for-developers.md)
- [疑難排解 .NET Framework 安裝和解除安裝遭封鎖的問題](../install/troubleshoot-blocked-installations-and-uninstallations.md)
- [在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數](reducing-system-restarts.md)
- [如何：取得 .NET Framework 4.5 安裝程式的進度](how-to-get-progress-from-the-dotnet-installer.md)
