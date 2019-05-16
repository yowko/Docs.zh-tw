---
title: Windows Form 中的自動縮放比例
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: cacda830a2501dcd127248955848d207d80bbe2c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636986"
---
# <a name="automatic-scaling-in-windows-forms"></a>自動縮放 Windows Form

自動縮放功能允許某部電腦上以特定顯示解析度或系統字型所設計的表單和其控制項，可以在另一部電腦上以不同的顯示解析度或系統字型正確地顯示。 如此可確保表單和其控制項利用智慧方式調整大小，以便與使用者和其他開發人員電腦上的原生視窗和其他應用程式保持一致。 對自動縮放和視覺化樣式的.NET framework 的支援可讓.NET Framework 應用程式，以維護一致的外觀與風格相較於每個使用者的電腦上的原生 Windows 應用程式。

大部分的情況下，作為自動調整的運作中應該有.NET Framework 版本 2.0 和更新版本。 不過，字型配置變更可能會造成問題。 如需如何解決此問題的範例，請參閱[How to:回應 Windows Forms 應用程式中的字型配置變更](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md)。

## <a name="need-for-automatic-scaling"></a>自動縮放的需求

如果沒有自動縮放功能，專為某種顯示解析度或字型所設計的應用程式會在該解析度或字型變更時，看起來太小或太大。 例如，如果應用程式在設計時使用新細明體 9 點做為基準，然後未經調整便在系統字型為新細明體 12 點的電腦上執行，則會看起來太小。 文字項目 (例如標題、功能表、文字方塊內容等) 的顯示將會比其他應用程式還要小。 此外，含有文字之使用者介面 (UI) 項目 (例如標題列、功能表和許多控制項) 的大小會取決於所使用的字型。 在這個範例中，這些項目看起來也會相對較小。

當應用程式是專為特定顯示解析度而設計時，就會發生類似的情況。 最常見的顯示解析度為 96 為 dots per inch (DPI)，而這就等於 100%顯示縮放比例，但支援 125%、 150%、 200%的更高解析度顯示畫面 (哪些分別等於 120，第 144 和 192 DPI) 和更新版本會變得更為普遍。 如果未經調整，專為某種解析度所設計的應用程式 (特別是圖形應用程式) 以另一種解析度執行時，便會看起來太大或太小。

自動縮放功能會根據相對字型大小或顯示解析度，自動調整表單和其控制項的大小，以改善這些問題。 Windows 作業系統支援使用稱為對話方塊單位的相對測量單位，來自動縮放對話方塊。 對話方塊單位是以系統字型以及其與像素的關聯性為依據，並可透過 Win32 SDK 函式 `GetDialogBaseUnits` 來判斷。 當使用者變更 Windows 所使用的佈景主題時，所有對話方塊都會隨著自動調整。 此外，.NET Framework 支援自動調整，根據預設系統字型或顯示解析度。 您可以選擇性地停用應用程式中的自動縮放功能。

## <a name="original-support-for-automatic-scaling"></a>自動縮放的原始支援

1.0 和 1.1 版的.NET Framework 支援自動調整的方式直接根據 UI 中，以 Win32 SDK 值表示所使用的 Windows 預設字型**DEFAULT_GUI_FONT**。 這種字型通常只有在顯示解析度變更時才會變更。 之前會使用下列機制來實作自動縮放：

1. 在設計階段，<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 屬性 (現在已被取代) 會設定為開發人員電腦上預設系統字型的高度和寬度。

2. 在執行階段，使用者電腦的預設系統字型會用來初始化 <xref:System.Windows.Forms.Form> 類別的 <xref:System.Windows.Forms.Control.Font%2A> 屬性。

3. 在顯示表單之前，會呼叫 <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> 方法來縮放表單。 這個方法會從 <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 和 <xref:System.Windows.Forms.Control.Font%2A> 計算相對縮放比例，然後呼叫 <xref:System.Windows.Forms.Control.Scale%2A> 方法實際縮放表單和其子系。

4. <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 的值已更新，後續對 <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> 的呼叫不會繼續調整表單的大小。

雖然這項機制在大部分情況下便已足夠，但是仍有下列限制：

- 因為<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>屬性以整數值表示基準字型大小，會發生捨入錯誤，更為明顯，表單特別是當透過多個解決方法。

- 自動縮放只會在 <xref:System.Windows.Forms.Form> 類別中實作，並不會在 <xref:System.Windows.Forms.ContainerControl> 類別中實作。 因此，只有在使用者控制項是以與表單相同的解析度所設計，並且在設計階段置於表單中時，使用者控制項才能正確縮放。

- 多位開發人員只能在其電腦解析度都相同時，才能同時設計表單和其子控制項。 同樣地，它也會根據與父表單關聯的解析度來繼承表單。

- 它與不相容所導入的.NET Framework 2.0 版中，這類的新版配置管理員<xref:System.Windows.Forms.FlowLayoutPanel>和<xref:System.Windows.Forms.TableLayoutPanel>。

- 它不支援直接根據顯示解析度進行縮放，但這是與 [!INCLUDE[compact](../../../includes/compact-md.md)] 相容的必要條件。

雖然這項機制會保留在.NET Framework 2.0 版為了與舊版相容，但它已被取代的更強大的縮機制，接下來所述。 因此，<xref:System.Windows.Forms.Form.AutoScale%2A>、<xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>、<xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> 和特定 <xref:System.Windows.Forms.Control.Scale%2A> 多載會標記為已過時。

> [!NOTE]
> 當您升級至.NET Framework 2.0 版的舊版程式碼，您可以安全地刪除這些成員的參考。

## <a name="current-support-for-automatic-scaling"></a>目前支援自動調整

.NET Framework 2.0 版引進下列變更 Windows Form 自動縮放 surmounts 先前的限制：

- 縮放的基礎支援已移至 <xref:System.Windows.Forms.ContainerControl> 類別，因此表單、原生複合控制項和使用者控制項都能獲得一致的縮放支援。 同時也加入新成員 <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>、<xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>、<xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> 和 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>。

- <xref:System.Windows.Forms.Control> 類別也具有幾個新成員，以便可以參與縮放並支援在相同表單上使用混合縮放比例。 <xref:System.Windows.Forms.Control.Scale%2A>、<xref:System.Windows.Forms.Control.ScaleChildren%2A> 和 <xref:System.Windows.Forms.Control.GetScaledBounds%2A> 成員尤其支援縮放比例。

- 補充的系統字型支援已新增根據螢幕解析度進行縮放的支援，如 <xref:System.Windows.Forms.AutoScaleMode> 列舉所定義。 這種模式與 [!INCLUDE[compact](../../../includes/compact-md.md)] 支援的自動縮放相容，因此可更輕鬆地進行應用程式移轉。

- 自動縮放實作已新增與配置管理員 (例如 <xref:System.Windows.Forms.FlowLayoutPanel> 和 <xref:System.Windows.Forms.TableLayoutPanel>) 的相容性。

- 縮放比例現在以浮點值表示 (通常使用 <xref:System.Drawing.SizeF> 結構)，因此已實際減少捨入錯誤。

> [!CAUTION]
> 不支援 DPI 和字型縮放模式的任意混合。 雖然您可以使用某種模式 (例如 DPI) 縮放使用者控制項，並使用另一種模式 (字型) 將控制項置於表單上，而不會有任何問題，但是將某種模式中的基底表單與從另一種模式的衍生表單混合，可能會導致無法預期的結果。

### <a name="automatic-scaling-in-action"></a>自動調整規模動作

Windows Form 現在使用下列邏輯來自動縮放表單和其內容：

1. 在設計階段，每個 <xref:System.Windows.Forms.ContainerControl> 會記錄縮放模式，以及各自在 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> 和 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 中的目前解析度。

2. 在執行階段，實際的解析度會儲存在 <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> 屬性中。 <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> 屬性動態計算執行階段縮放解析和設計階段縮放解析間的比率。

3. 當表單載入時，如果 <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> 和 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 的值不同，則會呼叫 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> 方法以縮放控制項和其子系。 這個方法會暫止配置並呼叫 <xref:System.Windows.Forms.Control.Scale%2A> 方法，以執行實際的縮放。 之後，<xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 的值會更新以避免繼續縮放。

4. 在下列情況下，也會自動叫用 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>：

    - 為了在縮放模式為 <xref:System.Windows.Forms.AutoScaleMode.Font> 時回應 <xref:System.Windows.Forms.Control.OnFontChanged%2A> 事件。

    - 當繼續容器控制項的配置，並在 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> 或 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> 屬性中偵測到變更時。

    - 如上所指，當縮放父 <xref:System.Windows.Forms.ContainerControl> 時。 每個容器控制項會負責使用自已的縮放比例 (而非其父容器的縮放比例)，來縮放其子系。

5. 子控制項可以透過幾種方式，修改其縮放行為：

    - 可以覆寫 <xref:System.Windows.Forms.Control.ScaleChildren%2A> 屬性，以判斷是否應該縮放其子控制項。

    - 可以覆寫 <xref:System.Windows.Forms.Control.GetScaledBounds%2A> 方法，以調整控制項的縮放範圍，而不是縮放邏輯。

    - 可以覆寫 <xref:System.Windows.Forms.Control.ScaleControl%2A> 方法，以變更目前控制項的縮放邏輯。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [使用視覺化樣式呈現控制項](./controls/rendering-controls-with-visual-styles.md)
- [如何：避免自動縮放來改善效能](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)
