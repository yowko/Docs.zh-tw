---
title: Windows 表單表單功能改進
description: 瞭解 .NET 核心 Windows 窗體嘗試與 .NET 框架 Windows 窗體相比提高可存取性的方式。
ms.date: 04/20/2020
helpviewer_keywords:
- Windows Forms accessibility
- accessibility
author: M-Lipin
ms.openlocfilehash: 30eb8b3bd0aaf646ea23f4f036e822f9bba78dc4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739749"
---
# <a name="accessibility-improvements-in-windows-forms-controls-for-net-core-30"></a>.NET Core 3.0 的 Windows 表單元件中的輔助功能改進

Windows 窗體正在繼續改進其使用輔助功能技術的方式,以便更好地支援 Windows 窗體客戶。 這些改善包括下列變更：

- 與輔助功能用戶端應用程式(包括講述人)互動的各個領域的更改。
- 對可存取階層進行了變更 (改善 UI 自動化樹狀的瀏覽)。
- 鍵盤導航中的更改。

> [!IMPORTANT]
> 在 .NET 框架 4.7.1 到 .NET 框架 4.8 中所做的輔助功能更改包含在 .NET Core 3.0 及以上,默認情況下已啟用。 . NET 框架支援相容換機,允許應用程式選擇退出新的輔助功能行為。 另一方面,.NET Core 不支援這些設置,並且不允許應用程式選擇退出輔助功能行為。
  
從 .NET Core 3.0 開始,Windows 窗體應用程式將受益於所有新的輔助功能(在 .NET 框架 4.7.1 - 4.8 中介紹),無需其他配置。

## <a name="listbox-accessibility-support"></a>清單框輔助功能支援

以下變更適用於<xref:System.Windows.Forms.ListBox>控制項:

- 啟用了用於`ListBox`控制的 UI 自動化支援。
- 通過將`ListBox`添加<xref:System.Windows.Automation.ScrollItemPattern>`ListBox`到 項以及通過增強輔助功能事件籌集和處理以及通過專案進行講述人導航(上限鎖定導航不正確,並且不會無意中將導航扔到控件之外),從而改進了輔助功能支援。

## <a name="checkedlistbox-accessibility-support"></a>選取清單框輔助功能支援

以下變更適用於<xref:System.Windows.Forms.CheckedListBox>控制項:

- 由項目`CheckedListBox`的輔助功能屬性提供的更正邊界。
- 改進了`ListBox``CheckedListBox`整體和可訪問性:更正了屬性值和事件模型。

## <a name="combobox-accessibility-support"></a>組合盒輔助功能支援

以下變更適用於<xref:System.Windows.Forms.ComboBox>控制項:

- 更新了獲取`ComboBox`項的輔助物件以啟用為專案生成I而不是從項獲取哈希代碼的過程,如果函數被覆蓋,<xref:System.Object.GetHashCode%2A>這可能不安全。

## <a name="datagridview-accessibility-support"></a>資料格線檢視輔助功能支援

以下變更適用於<xref:System.Windows.Forms.DataGridView>控制項:

- 由列`DataGridView.Bounds`、行、單元格和相應標頭的輔助功能屬性更正,提高了邊界矩形計算的性能。 考慮到整個控制項的邊界及其視口,將正確表示所有可訪問邊界。
- 為可`Value.IsReadOnly`存取的用戶端應用程式提供更正的屬性值。 該屬性現在顯示單元格`IsReadOnly`的正確狀態。
- 修復了第一次<xref:System.Windows.Forms.DataGridView.CellParsing>單元格更改的事件引發問題。 單元格值可以更改,沒有任何問題,包括第一`DataGridView`個控制交互。
- 使用`DataGridView`Windows 高對比度主題時,改進了背景顏色對比度。 使用`DataGridView`HC#1、HC+2 和 HC 黑色主題時更改預設回顏色。

## <a name="propertygrid-accessibility-support"></a>屬性格格輔助功能支援

以下變更適用於<xref:System.Windows.Forms.PropertyGrid>控制項:

- 網格`PropertyGrid.Bounds`條目的輔助功能屬性已更正,提高了邊界矩形計算的性能。 現在,考慮到整個控件的邊界及其視口,所有可訪問性邊界都正確表示。
- 更正了輔助控制項的可存取名稱和說明,以不包含控制項類型名稱,並避免對控制項類型名稱進行雙重通知。

## <a name="toolstrip-accessibility-support"></a>工具條輔助功能支援

以下變更適用於<xref:System.Windows.Forms.ToolStrip>控制項:

- 改進了通過`ToolStrip``MenuStrip`和`StatusStrip`和項的導航。 更正`ToolStrip`和`MenuStrip`移位選項卡導航,在按下移位選項卡上箭頭時回迴圈功能表項,該箭頭將導航到底部功能表元素。
- 改進`MenuStrip`了可訪問導航、更正的功能表可存取控制類型,可為子功能表製作類型為"菜單"而不是"菜單專案"的子功能表。

## <a name="printpreviewcontrol-and-printpreviewdialog-accessibility-support"></a>預覽控制並列印預覽對話輔助功能支援

以下變更適用於列印控制項:

- 通過功能表項改進了可訪問導航(包括講述人導航)。
- 改進了高對比度主題支援,使控制元素更加對比。

## <a name="stringcollectioneditor-accessibility-support"></a>字串收集編輯器輔助功能支援

Windows 表單表設計器現在使用具有改進的輔助功能支援的字串集合編輯器。

## <a name="monthcalendar-accessibility-support-available-in-net-core-31"></a>月曆輔助功能支援(在 .NET 核心 3.1 中提供)

以下變更適用於<xref:System.Windows.Forms.MonthCalendar>控制項:

- 添加了 UI 自動化伺服器`MonthCalendar`提供者 來控制、添加了 UI 自動化網格模式和表模式提供程式。
- 變更_的表_可存取控制項類型到_行事曆_可存`MonthCalendar`取 控制項類型`MonthCalendar`,除非控制項具有定義 控制項可存取名稱的上述標籤控制項的情況,在此特定情況下,可存取控制項類型將成為_表_格 。
- 改進了所選控制日期的`MonthCalendar`公告。
- 改進`MonthCalendar`了對螢幕閱讀器和其他輔助功能工具的控制支援。 此時,用戶可以導航控制件元素並使用僅鍵盤輸入與這些元素進行交互。 使用「講述人」,使用 CAPS + 箭頭鍵通過控制元素導航,然後使用 CAPS = 輸入以調用元素預設操作。
- 使用對焦矩形改進`MonthCalendar`了子元素的箭頭鍵導航:講述人的藍色焦點矩形。
- 改進了控制項元素抓測操作`MonthCalendar`的可存取性`MonthCalendar`, 以便透過提供的座標獲取子可存取元素。

## <a name="tooltips-accessibility-available-in-net-core-31"></a>工具提示輔助功能(在 .NET 核心 3.1 中提供)

- 增加了通過螢幕閱讀器應用程式(如 NVDA 和講述人)宣佈工具提示文本的能力。 螢幕閱讀器應用程式現在可以宣佈任何 Windows 窗體控制項的鍵盤或滑鼠工具提示的文本,該控制項配置為顯示工具提示。

## <a name="ui-automation-support-for-datagridview-propertygrid-listbox-combobox-toolstrip-and-other-controls"></a>對 DataGridView、屬性網格、清單框、組合盒、工具條和其他控制項的 UI 自動化支援

在運行時為控件啟用 UI 自動化支援,但在設計期間不使用。 如需 UI 自動化的概觀，請參閱 [UI 自動化概觀](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview)。

## <a name="see-also"></a>另請參閱

- [協助功能最佳實作](../ui-automation/accessibility-best-practices.md)。
