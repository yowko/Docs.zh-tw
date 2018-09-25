---
title: 停用 Visual Studio 中的 DPI 感知
description: 討論在 HDPI 監視器上的 Windows Form 設計工具，以及如何執行 Visual Studio 做為 DPI 感知的處理序的限制。
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 226ec3f683913102e8f5202ffaa100945e629e0a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082509"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>停用 Visual Studio 中的 DPI 感知

Visual Studio 是為 dots per inch (DPI) 感知應用程式，這表示顯示標尺自動。 如果應用程式指出不 DPI 感知，作業系統會調整為點陣圖的應用程式。 此行為也稱為 DPI 虛擬化。 應用程式仍然會認為它正在執行 100%縮放比例，或 96 dpi。

## <a name="windows-forms-designer-on-hdpi-monitors"></a>在 HDPI 監視器上的 Windows Form 設計工具

**Windows Form 設計工具**Visual Studio 中沒有縮放支援。 這會導致顯示問題，當您開啟中的某些表單**Windows Form 設計工具**在 hdpi () 監視的高 dpi。 如需範例，控制項可能會出現重疊，如下圖所示：

![HDPI 監視器上的 Windows Form 設計工具](media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

在 Visual Studio 2017 版本 15.8 和更新版本，當您開啟中的表單**Windows Form 設計工具**在 HDPI 監視器中，Visual Studio 會顯示黃色列的參考設計工具的頂端：

![在以 DPI 感知的模式重新啟動 Visual Studio 中的資訊列](media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

訊息讀取**主顯示器上的縮放比例設為 200%(192 dpi)。設計師視窗中，這可能造成轉譯問題。**

如果您不使用設計工具中，而且不需要調整表單的配置，您可以略過的資訊列，並繼續運作，在程式碼編輯器，或在其他類型的設計工具。 只有**Windows Form 設計工具**會受到影響。 如果您需要在中運作**Windows Form 設計工具**下, 一節可協助您[解決此問題](#to-resolve-the-problem)。

## <a name="to-resolve-the-problem"></a>若要解決此問題

有三個選項可以解決顯示問題。

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>重新啟動 Visual Studio 做為 DPI 感知的處理序

您可以選取黃色的資訊列上的選項重新啟動 Visual Studio 做為 DPI 感知的處理序。 這是最好的解決問題。

Visual Studio 執行時做為 DPI 感知的處理序，設計工具的版面配置問題解決，但是字型可能會模糊。 Visual Studio 會顯示不同的黃色參考用訊息，指出 DPI 感知處理程序的形式執行時**Visual Studio 正在執行做為 DPI 感知的處理序。WPF 與 XAML 設計工具可能無法正確顯示。** 資訊列也會提供選項，以**做為 DPI 感知的處理序重新啟動 Visual Studio**。

> [!NOTE]
> - 如果您有浮動工具視窗，在 Visual Studio 中的，當您選取要做為 DPI 感知的處理序重新啟動選項，這些工具視窗的位置可能會變更。
> - 如果您使用預設的 Visual Basic 設定檔，或如果您有**儲存新專案建立時**中的選項取消選取**工具** > **選項** > **專案和方案**，Visual Studio 無法重新開啟專案，做為 DPI 感知的處理序重新啟動時。 不過，您可以開啟專案，選取它底下**檔案** > **最新的專案和方案**。

請務必重新啟動 Visual Studio 做為 DPI 感知的處理序，當您完成在工作時**Windows Form 設計工具**。 當它做為 DPI 感知的處理序執行時，字型可以看得很吃力，和您可能會看到其他設計工具中的問題，例如**XAML 設計工具**。 如果您關閉並重新開啟 Visual Studio，它 DPI 感知的模式中執行時，它會變成 DPI 感知一次。 您也可以按一下**做為 DPI 感知的處理序重新啟動 Visual Studio**資訊列中的選項。

### <a name="add-a-registry-entry"></a>新增登錄項目

您可以藉由修改登錄，以將 Visual Studio 標記為 DPI 感知。 開啟**登錄編輯程式** ，並新增一個項目**您可以 NT\CurrentVersion\AppCompatFlags\Layers**子機碼：

**項目**: %programfiles (x86) %\Microsoft Visual Studio\2017\your-edition\Common7\IDE\devenv.exe

**型別**: REG_SZ

**值**: DPIUNAWARE

> [!NOTE]
> Visual Studio 會保留在 DPI 感知的模式，直到您移除登錄項目。

### <a name="set-your-display-scaling-setting-to-100"></a>設定您的顯示縮放比例為 100%的設定

若要設定您 Windows 10 中的縮放比例設定為 100%的顯示，請輸入**顯示設定**在 [搜尋] 方塊中，然後選取工作列**變更顯示設定**。 在 **設定**視窗中，將**變更的文字、 應用程式和其他項目大小**來**100%**。

設定您的顯示器設為 100%縮放比例可能不想要因為它可以讓使用者介面太小而無法使用。

## <a name="see-also"></a>另請參閱

- [自動縮放 Windows Form](automatic-scaling-in-windows-forms.md)