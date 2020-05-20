---
title: 部署現代化傳統型應用程式
description: 部署新式桌面應用程式所需瞭解的一切。
ms.date: 05/12/2020
ms.openlocfilehash: 4a4d93caf1c2f8f58d48ee3199bbe6983fa939f4
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423254"
---
# <a name="deploying-modern-desktop-applications"></a>部署現代化傳統型應用程式

當您開發桌面應用程式時，要考慮的一件事是如何將應用程式封裝並部署到使用者的電腦。 封裝、部署和安裝的問題是，它通常是在 IT 專業人員的範圍內，負責與開發人員不同的事物。

這幾天，我們全都熟悉 DevOps 概念，讓開發人員和 IT 專業人員能夠密切地工作，將應用程式移至生產環境。 但如果您在桌上型電腦上已有超過10年的時間，您可能會看到下列案例。 開發人員小組會一起工作，以符合專案的截止時間。 商務人員擔心，因為他們需要在許多使用者的電腦上工作，才能執行公司。 在「D 天」，專案經理會向每位開發人員檢查其程式碼是否正常運作，而且一切都沒問題，因此可以出貨。 然後，套件小組會產生應用程式的設定、將其散發給每個使用者電腦，以及一組執行應用程式的測試使用者。 他們會嘗試，因為在顯示任何 UI 之前，應用程式會擲回例外狀況，指出「方法 ~ 物件 ~ 失敗」。 驚慌會開始流經空中，而簡短的調查則是指引進了協力廠商控制項的年輕開發人員，這當然是「在開發電腦上工作」。

傳統上，安裝桌面應用程式有兩個主要原因：

- 開發人員與 IT 小組之間缺乏密切的共同作業文化特性。
- 缺乏穩固的封裝和部署技術，我們可以建立。

事實上，我們一直在致歉您已安裝應用程式的情況，因為：

- 最後，它會在您的電腦上產生一些不想要的副作用。
- 某些先前安裝的應用程式停止運作。

此外，您也無法藉由卸載應用程式，將系統還原到其原始狀態。 我們一直在此情況下，我們已 alistair 創造「DLL Hell」或「Winrot」之類的詞彙。

在本章中，我們將討論 MSIX。 MSIX 是 Microsoft 的全新技術，會嘗試抓住先前的技術，為未來的封裝技術提供堅實的基礎。

封裝技術對現代化有何作用？ 事實上，封裝是企業 IT 的基礎，投資了許多錢。 現代化不僅與使用最新技術有關。 它也與您在公司將功能傳遞給用戶端之前，從定義商務需求到市場的時間之間縮短上市的時機。

## <a name="the-modern-application-lifecycle"></a>現代化應用程式生命週期

現在，開發人員會撰寫並建立應用程式的程式碼，然後將產生的資產傳遞給 IT 專業人員。 然後，IT 專業人員會重新設定應用程式，並將它重新封裝，通常是在 MSI 中，或最近採用 App-v 封裝格式。 然後，應用程式會透過不同的通道和工具進行部署。 這種方法的其中一個主要問題，通常稱為「封裝 paralysis」。 問題在於，每次有應用程式更新或作業系統更新時，此週期都會重複。

您可以看到下列圖片所反映的程式：

![顯示現代化 IT 生命週期的圖表](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

公司需要將此封裝週期分成三個獨立週期的方法：

- OS 更新
- 應用程式更新
- 自訂

![顯示現代化 IT 良性週期的圖表](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

上圖顯示您可以：

- 更新基礎作業系統，而不需要重新封裝您的應用程式。
- 不需要重新封裝原始開發人員套件，即可從該專案進行自訂。

這項基本變更會將我們帶到新的和現代化的 IT 生命週期，如下圖所示：

![使用 Microsoft 工具顯示應用程式生命週期的圖表](./media/deploy-modern-applications/microsoft-it-tools.png)

開發人員建立應用程式並產生 MSIX 套件，IT 專業人員可以取用和設定，而不需要重新封裝。 除了 MSIX 技術之外，Microsoft 還建立了一些工具，讓它可以自訂和設定套件，而不需要重新封裝。

## <a name="msix-the-next-generation-of-deployment"></a>MSIX：新一代部署

在 MSIX 之前，有幾種封裝技術可供使用，像是安裝程式、MSI、ClickOnce、App-v 和腳本。 這兩種技術都有自己的優勢，而 Microsoft 決定挑選最棒的組建 MSIX。 MSIX 是建置於這些現有技術的基礎上，挑選出最佳的功能：

- App-v = \> 容器化
- ClickOnce = \> 自動更新
- MSI = \> 容易散發

透過 MSIX，您可以取得一項安裝程式技術，其中包含所有這些功能。

![此圖顯示對建立 MSIX 有影響的不同技術](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a>MSIX 的優點

#### <a name="never-regret-installing-an-app"></a>永不致歉安裝應用程式

MSIX 提供可預測、可靠且安全的部署。 封裝資訊清單中包含的宣告式方法可讓 OS 追蹤您應用程式所需的每個資產。 它也提供真正的全新卸載，而且沒有副作用。

#### <a name="disk-space-optimization"></a>磁碟空間優化

MSIX 已優化，可減少應用程式在使用者電腦磁碟空間上的使用量。 它會建立檔案的儲存單一版本。 也就是說，如果您有兩個不同的套件具有相同的 DLL，則不會安裝 DLL 兩次。 平臺會處理這個問題，因為它知道特定應用程式已安裝的所有檔案，因為它的宣告式本質。 它也可讓您讓不同版本的 DLL 並存運作。

使用資源套件時，您可以輕鬆地建立多語系應用程式，而 OS 會負責安裝所使用的。

#### <a name="network-optimization"></a>網路優化

MSIX 會偵測位元組區塊層級的檔案差異，並啟用稱為「差異更新」的功能。 這表示，只有更新的位元組區塊會在應用程式更新時下載。

![顯示 MSIX 如何管理差異更新的圖表](./media/deploy-modern-applications/msix-managing-updates.png)

使用串流安裝時，使用者可以快速開始使用您的應用程式，而應用程式的其他部分則會在背景下載。 這項功能可為您的使用者提供吸引人的體驗。

使用選擇性套件功能時，您可以在應用程式部署上達成元件化，以便在需要時下載。

#### <a name="simple-packaging-and-deployment"></a>簡單封裝和部署

此 AppManifest 會宣告每個應用程式的版本控制、裝置目標和識別（以標準方式表示）。 它也提供一種方式來簽署您的資產，以提供穩固的安全性基礎。

#### <a name="os-managed"></a>作業系統管理

OS 會處理所有用來安裝、更新和移除應用程式的進程。 應用程式會針對每個使用者安裝，但只下載一次，可將磁片使用量降到最低。 Microsoft 正致力於在 Windows 7 上提供 MSIX 體驗。

#### <a name="windows-provides-integrity-for-the-app"></a>Windows 提供應用程式的完整性

使用數位簽章時，您可以保證不會從不受信任的來源安裝應用程式。 MSIX 也會防止進行篡改，原因如下：

- 它會保留檔案雜湊的記錄。
- 它會偵測檔案在安裝後是否已修改。

#### <a name="works-for-the-entire-app-catalog"></a>適用于整個應用程式類別目錄

MSIX 的其中一個最酷事項是，它適用于整個應用程式類別目錄、Windows Forms、WPF、MFC/ATL、Delphi，即使您想要執行 xCopy 部署、ClickOnce 或前往存放區，您還是可以使用相同的 MSIX 封裝。

### <a name="tools"></a>工具

#### <a name="windows-application-packaging-project"></a>Windows 應用程式封裝專案

您可以使用 Visual Studio 中的 **Windows 應用程式封裝專案**   專案，為您的桌面應用程式產生套件。 然後，您可以將該套件發佈至 Microsoft Store，或將它側載到一或多部電腦上。

#### <a name="msix-packaging-tool"></a>MSIX 封裝工具

MSIX 封裝工具可讓您將現有的 Win32 應用程式重新封裝成 MSIX 格式。 它提供互動式 UI 和用於轉換的命令列，讓您能夠在不使用原始程式碼的情況下轉換應用程式。

![MSIX 封裝工具](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a>套件支援架構

封裝支援架構是一個開放原始碼套件，可在您無法存取原始程式碼時，協助您將修正套用至現有的 Win32 應用程式，以便在 MSIX 容器中執行。 套件支援架構有助於讓應用程式遵循最新執行階段環境的最佳做法。

#### <a name="app-installer"></a>應用程式安裝程式

應用程式安裝程式可讓您按兩下應用程式套件，以安裝 Windows 10 應用程式。 這表示使用者不需要使用 PowerShell 或其他開發人員工具來部署 Windows 10 應用程式。 應用程式安裝程式也可以從網頁、選用套件及相關集合中安裝應用程式。

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a>如何從現有的 Win32 桌面應用程式建立 MSIX 封裝

讓我們逐步完成從現有的 Win32 應用程式建立 MSIX 套件的流程。 在此範例中，我們將使用 Windows Forms 應用程式。

若要開始，請將新專案新增至您的方案，選取 Windows 應用程式封裝專案，並為其命名。

![加入新的 Windows 應用程式封裝專案](./media/deploy-modern-applications/add-packaging-project.png)

您會看到封裝專案的結構，並記下名為 [*應用程式*] 的特殊資料夾。 在此資料夾中，您可以指定要包含在封裝中的應用程式。 它可以是一個以上。

![封裝專案的結構](./media/deploy-modern-applications/packaging-project.png)

以滑鼠右鍵按一下 [*應用程式*] 資料夾，然後選取您想要從 Visual Studio 方案封裝的 Windows Forms 專案。

![將 Windows Forms 專案新增至封裝專案](./media/deploy-modern-applications/add-winforms-project.png)

此時，您可以編譯並產生封裝，但讓我們來檢查幾件事。 為了獲得更好的使用者體驗，Visual Studio 可以將現代化應用程式處理圖示和磚列和 [開始] 功能表的資產所需的所有視覺資產都自動產生。 開啟*package.appxmanifest.xml*檔案以存取資訊清單設計工具。 然後按一下 [**建立**]，即可從專案中顯示的指定影像產生所有視覺資產。

![Visual Studio 中的資訊清單設計工具的螢幕擷取畫面](./media/deploy-modern-applications/manifest-designer.png)

如果您開啟*package.appxmanifest.xml*檔案的程式碼，您可以看到幾個有趣的東西。

右邊 `<Package>` 有一個 `<Identity>` 節點。 這是您的封裝應用程式即將取得其身分識別的位置，這將由 OS 管理。

![身分識別節點](./media/deploy-modern-applications/identity-node.png)

在 `<Capabilities>` 節點中，您可以找到應用程式所需的所有需求，特別注意 `<rescap:Capability Name="runFullTrust" \>` ，這會告訴 OS 在完全信任模式中執行應用程式，因為它是 Win32 應用程式。

![功能節點](./media/deploy-modern-applications/capabilities-node.png)

將封裝專案設定為方案的啟始專案，然後選取 [*執行*]。 這將會：

- 編譯 Windows Forms 應用程式。
- 從組建結果建立 MSIX 套件。
- 部署封裝。
- 將它安裝在開發電腦的本機上。
- 啟動應用程式。

![已安裝的應用程式](./media/deploy-modern-applications/our-installed-application.png)

如此一來，您就擁有全新的安裝和卸載體驗，MSIX 已完全整合到 Windows 10。

最後階段是關於如何將 MSIX 套件部署到另一部電腦。

以滑鼠右鍵按一下封裝專案，選取 [**儲存**] 功能表，然後選取 [**建立應用程式套件**] 選項。

然後，您可以選擇建立要上傳至存放區的封裝，或建立用於側載的封裝。 在大部分的現代化案例中，您會選擇 [**我要建立側載的套件**]。

![設定封裝](./media/deploy-modern-applications/configuring-packages.png)

您可以在此選取您想要設為目標的不同架構，因為您可以視需要包含多個相同的 MSIX 套件。

最後一個步驟是宣告您要部署最終安裝資產的位置。

![設定更新設定](./media/deploy-modern-applications/configure-update-settings.png)

您可以選擇在企業檔案伺服器上使用共用 UNC 路徑的 web 伺服器。 請注意設定，以指定您想要如何更新應用程式。 我們將在下一節討論應用程式更新。

如需詳細的逐步指南，請參閱[使用 Visual Studio 從原始程式碼封裝桌面應用程式](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)。

## <a name="auto-updates-in-msix"></a>MSIX 中的自動更新

Windows Store 具有使用 Windows Update 的絕佳更新機制。 在大部分的企業案例中，您不會使用存放區來散發您的桌面應用程式。 因此，您需要類似的方式來設定應用程式的更新，並將其提取給您的使用者。

使用 Windows 10 功能和 MSIX 套件的組合，您可以為使用者提供絕佳的更新體驗。 事實上，使用者不需要是技術，但仍可從順暢的應用程式更新體驗中獲益。

您可以透過兩種不同的方式，設定您的更新以與使用者互動：

- 使用者提示更新： OS 會顯示一些自動產生的絕佳 UI，以通知使用者有關應用程式即將安裝的資訊。 它會根據您在安裝檔案上指定的屬性來建立此 UI。

- 背景中的無訊息更新。 使用此選項時，您的使用者不需要知道更新。

您也可以設定何時要在應用程式啟動或定期執行更新。 由於有側載功能，您甚至可以在應用程式執行時取得這些更新。

當您使用這種類型的部署時，會建立名為*appinstaller*的特殊檔案。 這個簡單的檔案包含下列區段：

- *Appinstaller*檔案的位置
- 應用程式的主要 MSIX 套件屬性
- 更新行為

![appinstaller 檔案](./media/deploy-modern-applications/appinstaller-file.png)

隨著此檔案的結合，Microsoft 已設計了特殊的 URL 通訊協定，可從連結啟動安裝程式：

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

此通訊協定適用于所有瀏覽器，並在 Windows 10 上以絕佳的使用者體驗啟動安裝程式。 由於作業系統會管理安裝程式，因此它會留意此應用程式的安裝位置，並追蹤該進程所影響的所有檔案。

MSIX 會建立用於安裝的使用者介面，以自動顯示封裝的某些屬性。 這可讓每個應用程式都有常見的安裝體驗。

當您產生新的 MSIX 套件並將它移至部署伺服器之後，您只需要編輯*appinstaller*檔案來反映這些變更，主要是版本以及新 MSIX 檔案的路徑。 下次使用者啟動應用程式時，系統會偵測到變更，並在背景下載新版本的檔案。 完成此動作時，系統會針對您的使用者，以透明的方式在新的應用程式啟動時執行安裝。

>[!div class="step-by-step"]
>[上一步](example-migration-core.md)
