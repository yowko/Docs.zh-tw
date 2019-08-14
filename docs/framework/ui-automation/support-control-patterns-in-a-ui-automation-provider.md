---
title: 支援 UI 自動化提供者的控制項模式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
ms.openlocfilehash: da423af259ac3ef88d5b52d576d3ab5ebb4f916e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971794"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>支援 UI 自動化提供者的控制項模式

> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。

本主題說明如何在使用者介面自動化提供者上實作一個或多個控制項模式，讓用戶端應用程式能夠操作控制項並從中取得資料。

## <a name="support-control-patterns"></a>支援控制項模式

1. 針對項目應該支援的控制項模式，實作適當的介面，例如適用於 <xref:System.Windows.Automation.Provider.IInvokeProvider> 的 <xref:System.Windows.Automation.InvokePattern>。

2. 在 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>實作中，傳回包含每個控制項介面實作的物件

## <a name="example"></a>範例

下列範例示範單一選取自訂清單方塊的 <xref:System.Windows.Automation.Provider.ISelectionProvider> 實作。 它會傳回三個屬性並取得目前選取的項目。

[!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
[!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]

## <a name="example"></a>範例

下列範例示範 <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> 的實作，它會傳回實作 <xref:System.Windows.Automation.Provider.ISelectionProvider>的類別。 大部分的清單方塊控制項也會支援其他模式, 但是在此範例中, 會針對`Nothing`所有其他模式識別碼傳回 null 參考 (在 Microsoft Visual Basic .net 中)。

[!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
[!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]

## <a name="see-also"></a>另請參閱

- [UI 自動化提供者概觀](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [伺服器端 UI 自動化提供者實作](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
