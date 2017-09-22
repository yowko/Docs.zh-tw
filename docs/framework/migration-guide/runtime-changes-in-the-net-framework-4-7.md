---
title: ".NET Framework 4.7 中的執行階段變更 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes,.NET Framework
- runtime changes,.NET Framework 4.7
- application compatibility
ms.assetid: 268eb334-7906-4e0b-a1e3-c74b745de2a5
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 321ec8f8293afad0f3da7fb6f907f45d404394cc
ms.lasthandoff: 04/18/2017

---
# <a name="runtime-changes-in-the-net-framework-47"></a>.NET Framework 4.7 中的執行階段變更

在某些罕見的情況下，執行階段變更可能會影響以舊版 .NET Framework 為目標，但在新版 .NET Framework 執行階段上執行的現有應用程式。 這些變更也包含在不同的 .NET Framework 執行階段環境中執行之應用程式間的行為差異。 .NET Framework 4.6.2 包含下列領域的變更：

- [Windows Presentation Foundation (WPF)](#WPF)

下表中的 [範圍] 一欄指定每項變更的重要性：

- 主要。 影響大量應用程式或需要大幅修改程式碼的重大變更。 請注意，重定目標變更不屬於此分類。

- 次要。 影響少量應用程式或需要稍微修改程式碼的變更。

- 邊緣。 在非常特定 (罕見) 的情況下影響應用程式的變更。

- 透明。 此變更對應用程式的開發人員或使用者的影響不明顯。 發生此變更的應用程式應該不需要修改。

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> Windows Presentation Foundation (WPF)

assetId:///M:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView(System.Int32)?qualifyHint=False&autoUpgrade=True

| 功能 | 變更 | 影響 | 範圍 |
|---|---|---|---|
| <xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> 方法 | 在.NET Framework 4.6.2 中，啟用資料行虛擬化，但尚未決定資料行寬度時，<xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> 方法會以非同步方式執行。 如果資料行在非同步作業完成之前遭到移除，會發生 <xref:System.ArgumentOutOfRangeException>。<br/></br>從 .NET Framework 4.7 開始，這種情況不會再擲回例外狀況。 | 這項變更會提升方法的可靠性。 | Edge | 
|<xref:System.Windows.Controls.Ribbon.RibbonGroup> 背景 | 在 .NET Framework 4.6.2 和舊版中，當地語系化版本上的 <xref:System.Windows.Controls.Ribbon.RibbonGroup> 背景使用透明筆刷繪製，而導致 UI 體驗不佳。 在 .NET Framework 4.7 中，WPF 會更新 <xref:System.Windows.Controls.Ribbon.RibbonGroup> 控制項的當地語系化資源，確保選取正確的筆刷。 | 若要使用新的行為，請升級至 .NET Framework 4.7。 | Edge |
| WPF 拼字檢查功能 | 從 .NET Framework 4.6.1 開始，WPF 應用程式中的拼字檢查功能有時會在應用程式關閉期間擲回 <xref:System.ObjectDisposedException>。 <br/><br/>在 .NET Framework 4.7 中，執行階段是依正常程序處理例外狀況，以確保應用程式都不會再受到負面影響。 請注意，在偵錯工具下執行的應用程式偶爾還是發生第一個例外狀況。  | 若要使用新的行為，請升級至 .NET Framework 4.7。   | Edge |

## <a name="see-also"></a>請參閱

[.NET Framework 4.7 中的應用程式相容性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-7.md)


