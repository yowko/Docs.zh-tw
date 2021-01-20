---
title: 部署現代化傳統型應用程式
description: 部署新式桌面應用程式所需知道的一切。
ms.date: 05/12/2020
ms.openlocfilehash: ba47f09b27adf270734bbfff285fe44dd4175d29
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98615850"
---
# <a name="deploying-modern-desktop-applications"></a>部署現代化傳統型應用程式

當您開發桌面應用程式時，要考慮的一件事就是您的應用程式要如何封裝及部署到使用者的電腦上。 封裝、部署和安裝的問題是，它通常會落在 IT 專業人員的範圍內，而不是與開發人員在意不同的事物。

這幾天，我們全都熟悉 DevOps 的概念，讓開發人員和 IT 專業人員能夠密切合作將應用程式移至生產環境。 但是，如果您在桌上型電腦上有10年的時間，您可能會看到下列案例。 開發人員團隊合作，以符合專案期限。 商務人員緊張，因為他們需要在許多使用者的電腦上工作，才能執行公司。 在「D 天」，專案經理會向每位開發人員檢查其程式碼是否正常運作，而且一切都沒問題，因此可以寄送。 然後，套件小組會產生應用程式的安裝程式、將其散發給每個使用者電腦，以及一組測試使用者執行應用程式。 他們會嘗試，因為在顯示任何 UI 之前，應用程式會擲回一個例外狀況，指出「物件 ~ 失敗」的方法。 緊急情況會開始流經空氣，並將簡短的調查點帶到已引進協力廠商控制項的年輕開發人員，也就是「在開發電腦上工作」。

傳統上，安裝桌面應用程式有兩個主要原因：

- 缺乏開發和 IT 小組之間的密切合作文化。
- 缺乏穩固的封裝和部署技術可建立。

事實上，我們一直以來都致歉您安裝了應用程式，因為：

- 它最後會對您的電腦造成一些不想要的副作用。
- 某些先前安裝的應用程式會停止運作。

此外，您也無法藉由卸載應用程式，將系統還原為其原始狀態。 我們習慣在這種情況下，我們創造了「DLL Hell」或「Winrot」等詞彙。

在本章中，我們將討論 MSIX。 MSIX 是 Microsoft 的全新技術，其會嘗試抓住最優秀的技術，為未來的封裝技術提供穩固的基礎。

封裝技術與現代化有何用途？ 其實，封裝是企業 IT 的基礎，在那裡投資了許多資金。 現代化不僅與使用最新的技術有關。 這也與您的公司將功能交付給用戶端之前，縮短了商務需求的定義時間。

## <a name="the-modern-application-lifecycle"></a>新式應用程式生命週期

現今，開發人員會撰寫並建立應用程式的程式碼，然後將產生的資產傳遞給 IT 專業人員。 然後，IT 專業人員會重新設定應用程式，並將它重新封裝（通常是在 MSI 中，或更新的應用程式-V 封裝格式）。 然後會透過不同的通道和工具來部署應用程式。 這種方法的其中一個主要問題，通常稱為「封裝 paralysis」。 問題在於，每次有應用程式更新或作業系統更新時，此週期都會重複。

您可以看到此程式反映在下圖中：

![顯示新式 IT 生命週期的圖表](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

公司需要將此封裝週期分成三個獨立週期的方法：

- OS 更新
- 應用程式更新
- 自訂

![顯示新式 IT 良性週期的圖表](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

上圖顯示您可以：

- 更新基礎作業系統，而不需要重新封裝您的應用程式。
- 從中進行自訂，而不需要重新封裝原始開發人員套件。

這項最新的改變將引導我們到新式和新式 IT 生命週期，如下圖所示：

![顯示使用 Microsoft 工具之應用程式生命週期的圖表](./media/deploy-modern-applications/microsoft-it-tools.png)

開發人員會建立應用程式，並產生可供 IT 專業人員使用並設定的 MSIX 套件，而不需要重新封裝。 除了 MSIX 技術，Microsoft 還建立了可讓 IT 自訂和設定套件的工具，而不需要重新封裝。

## <a name="msix-the-next-generation-of-deployment"></a>MSIX：新一代的部署

在 MSIX 之前，有數種封裝技術可供使用，像是安裝程式、MSI、ClickOnce、App-v 和腳本。 這兩種技術都有自己的優勢，而 Microsoft 決定挑選最適合建立 MSIX。 MSIX 是以這些現有技術的基礎為基礎，可挑選各項技術的最佳基礎：

- App-v = \> 容器化
- ClickOnce = \> 自動更新
- MSI = \> 容易散發

透過 MSIX，您可以取得一項安裝程式技術，其中包含所有這些功能。

![顯示影響組建 MSIX 之不同技術的圖表](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a>MSIX 的優點

#### <a name="never-regret-installing-an-app"></a>永不致歉安裝應用程式

MSIX 提供可預測、可靠且安全的部署。 封裝資訊清單中包含的宣告方法可讓 OS 追蹤應用程式所需的每個資產。 它也提供真正的全新卸載且沒有副作用。

#### <a name="disk-space-optimization"></a>磁碟空間優化

MSIX 已優化，可減少應用程式對使用者電腦磁碟空間的使用量。 它會建立檔案的單一實例存放區。 也就是說，如果您有兩個具有相同 DLL 的不同套件，則不會安裝 DLL 兩次。 平臺會處理這個問題，因為它知道特定應用程式所安裝的所有檔案都有其宣告式本質。 它也可讓您將不同版本的 DLL 並存運作。

使用資源套件時，您可以輕鬆地建立多語系應用程式，而 OS 會負責安裝使用的應用程式。

#### <a name="network-optimization"></a>網路優化

MSIX 會偵測位元組區塊層級的檔案差異，並啟用稱為差異更新的功能。 這表示，只會在應用程式更新上下載已更新的位元組區塊。

![顯示 MSIX 如何管理差異更新的圖表](./media/deploy-modern-applications/msix-managing-updates.png)

使用串流安裝時，使用者可以快速開始處理您的應用程式，而應用程式的其他部分則會在背景下載。 這項功能可為您的使用者提供吸引人的體驗。

使用選擇性套件功能時，您可以在應用程式部署上達成元件化，以便在需要時下載。

#### <a name="simple-packaging-and-deployment"></a>簡單的封裝和部署

AppManifest 會宣告版本控制、裝置目標，並以標準方式針對每個應用程式進行識別。 它也提供一種方式來簽署您的資產，以提供穩固的安全性基礎。

#### <a name="os-managed"></a>作業系統管理

作業系統會處理安裝、更新和移除應用程式的所有進程。 應用程式會針對每個使用者安裝，但只會下載一次，將磁片使用量降到最低。 Microsoft 正在努力提供 Windows 7 上的 MSIX 經驗。

#### <a name="windows-provides-integrity-for-the-app"></a>Windows 提供應用程式的完整性

使用數位簽章時，您可以確保不會從不受信任的來源安裝應用程式。 MSIX 也會防止篡改，因為：

- 它會保留檔雜湊的記錄。
- 它會偵測在安裝之後是否已修改檔案。

#### <a name="works-for-the-entire-app-catalog"></a>適用于整個應用程式類別目錄

MSIX 的其中一個最酷事項，就是適用于整個應用程式類別目錄、Windows Forms、WPF、MFC/ATL、Delphi，即使您想要執行 xCopy 部署、ClickOnce 或前往存放區，也可以使用相同的 MSIX 套件。

### <a name="tools"></a>工具

#### <a name="windows-application-packaging-project"></a>Windows 應用程式封裝專案

您可以使用 Visual Studio 中的 **Windows 應用程式封裝專案**，為傳統型應用程式產生套件。 然後，您可以將該套件發佈至 Microsoft Store 或側載到一或多部電腦上。

#### <a name="msix-packaging-tool"></a>MSIX 封裝工具

MSIX 封裝工具可讓您將現有的 Win32 應用程式重新封裝成 MSIX 格式。 它同時提供互動式 UI 和命令列以進行轉換，讓您能夠在不需要原始程式碼的情況下轉換應用程式。

![MSIX 封裝工具](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a>套件支援架構

套件支援架構是開放原始碼套件，可在您沒有原始程式碼的存取權時，協助您將修正套用至現有的 Win32 應用程式，讓它可以在 MSIX 容器中執行。 套件支援架構有助於讓應用程式遵循最新執行階段環境的最佳做法。

#### <a name="app-installer"></a>應用程式安裝程式

應用程式安裝程式可以按兩下應用程式套件，以允許安裝 Windows 10 的應用程式。 這表示使用者不需要使用 PowerShell 或其他開發人員工具來部署 Windows 10 應用程式。 應用程式安裝程式也可以從網頁、選用套件及相關集合中安裝應用程式。

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a>如何從現有的 Win32 桌面應用程式建立 MSIX 套件

讓我們逐一完成從現有的 Win32 應用程式建立 MSIX 套件的程式。 在此範例中，我們將使用 Windows Forms 應用程式。

若要開始，請將新的專案新增至您的方案，選取 Windows 應用程式封裝專案，並為其命名。

![加入新的 Windows 應用程式封裝專案](./media/deploy-modern-applications/add-packaging-project.png)

您將會看到封裝專案的結構，並記下稱為「 *應用程式*」的特殊資料夾。 在此資料夾內，您可以指定要包含在封裝中的應用程式。 它可以是一個以上。

![封裝專案的結構](./media/deploy-modern-applications/packaging-project.png)

在 [ *應用程式* ] 資料夾上按一下滑鼠右鍵，然後從 Visual Studio 方案中選取您要封裝的 Windows Forms 專案。

![將 Windows Forms 專案新增至封裝專案](./media/deploy-modern-applications/add-winforms-project.png)

至此，您可以編譯和產生封裝，但讓我們來檢驗一下一些東西。 為了獲得更好的使用者體驗，Visual Studio 可以自動產生新式應用程式所需的所有視覺資產，以處理磚列和 [開始] 功能表的圖示和磚資產。 開啟 *package.appxmanifest* 檔案以存取資訊清單設計工具。 然後，只要按一下 [ **建立**]，就可以從專案上的指定影像產生所有視覺資產。

![Visual Studio 中資訊清單設計工具的螢幕擷取畫面](./media/deploy-modern-applications/manifest-designer.png)

如果您開啟 *package.appxmanifest* 檔案的程式碼，您可以看到幾個有趣的事情。

右側 `<Package>` 有一個 `<Identity>` 節點。 這是您的已封裝應用程式要取得其身分識別的位置，這會由作業系統管理。

![身分識別節點](./media/deploy-modern-applications/identity-node.png)

在 `<Capabilities>` 節點中，您可以找到應用程式所需的所有需求，特別注意，它會 `<rescap:Capability Name="runFullTrust" \>` 告訴 OS 以完全信任模式執行應用程式，因為它是 Win32 應用程式。

![功能節點](./media/deploy-modern-applications/capabilities-node.png)

將封裝專案設定為方案的啟始專案，然後選取 [ *執行*]。 這將會：

- 編譯 Windows Forms 應用程式。
- 從組建結果建立 MSIX 套件。
- 部署套件。
- 將它安裝在開發電腦的本機上。
- 啟動應用程式。

![我們已安裝的應用程式](./media/deploy-modern-applications/our-installed-application.png)

透過這種方式，您可以使用 MSIX 完全整合到 Windows 10 的全新安裝和卸載體驗。

最後一個階段是關於如何將 MSIX 封裝部署到另一部電腦。

以滑鼠右鍵按一下封裝專案，選取 [ **儲存** ] 功能表，然後選取 [ **建立應用程式套件** ] 選項。

然後，您可以選擇建立要上傳至存放區的封裝，或建立用於側載的封裝。 在大部分的現代化案例中，您會選擇要 **建立側載的套件**。

![設定套件](./media/deploy-modern-applications/configuring-packages.png)

您可以選取想要作為目標的不同架構，因為您可以將任意數量包含在相同的 MSIX 套件中。

最後一個步驟是宣告您想要部署最終安裝資產的位置。

![設定更新設定](./media/deploy-modern-applications/configure-update-settings.png)

您可以選擇在企業檔案伺服器上使用共用 UNC 路徑的 web 伺服器。 請注意這些設定，以指定您要如何更新應用程式。 我們將在下一節討論應用程式更新。

如需詳細的逐步指南，請參閱 [使用 Visual Studio 從原始程式碼封裝桌面應用程式](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)。

## <a name="auto-updates-in-msix"></a>MSIX 中的自動更新

Windows 儲存區具有使用 Windows Update 的絕佳更新機制。 在大部分的企業案例中，您不會使用存放區來散發您的桌面應用程式。 因此，您需要類似的方式來設定應用程式的更新，並將其提取給您的使用者。

使用 Windows 10 功能和 MSIX 套件的組合，您可以為您的使用者提供絕佳的更新體驗。 事實上，使用者根本不需要具備技術技術，但仍可從流暢的應用程式更新體驗中獲益。

您可以使用兩種不同的方式來設定更新與使用者互動：

- 使用者提示更新：作業系統會顯示一些自動產生的絕佳 UI，以通知使用者即將安裝應用程式。 它會根據您在安裝檔案中指定的屬性來建立這個 UI。

- 背景中的無訊息更新。 使用這個選項時，您的使用者不需要察覺更新。

您也可以設定當應用程式啟動或定期執行更新時，您要執行更新的時間。 由於有側載功能，您甚至可以在應用程式執行時取得這些更新。

當您使用此類部署時，會建立一個稱為 *appinstaller* 的特殊檔案。 這個簡單的檔案包含下列各節：

- *Appinstaller* 檔案的位置
- 應用程式的主要 MSIX 套件屬性
- 更新行為

![appinstaller 檔案](./media/deploy-modern-applications/appinstaller-file.png)

隨著這個檔案的組合，Microsoft 已經設計了一個特殊的 URL 通訊協定，從連結啟動安裝程式：

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

此通訊協定適用于所有瀏覽器，並在 Windows 10 上以絕佳的使用者體驗啟動安裝程式。 由於作業系統會管理安裝程式，因此它會知道此應用程式的安裝位置，並且會追蹤進程所影響的所有檔案。

MSIX 會建立用於安裝的使用者介面，以自動顯示封裝的某些屬性。 這可讓您針對每個應用程式提供常見的安裝體驗。

當您產生新的 MSIX 套件，並將它移至部署伺服器之後，您只需要編輯 *appinstaller* 檔案來反映這些變更，主要是版本以及新 MSIX 檔的路徑。 使用者下一次啟動應用程式時，系統會偵測到變更，並在背景下載新版本的檔案。 完成這項操作時，系統會為您的使用者以透明的方式在新的應用程式啟動時執行安裝。

>[!div class="step-by-step"]
>[[上一步]](example-migration.md)
