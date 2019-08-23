---
title: 在 UI 自動化片段提供者中啟用巡覽
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: 6410a0f8a991f1dc21a298972182ec630723f627
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932602"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>在 UI 自動化片段提供者中啟用巡覽
> [!NOTE]
> 這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。  
  
 本主題包含範例程式碼，顯示如何針對片段內的項目，在使用者介面自動化提供者中啟用巡覽。  
  
## <a name="example"></a>範例  
 下列範例程式碼針對清單內的清單項目實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> 。 父項目是清單方塊項目，同層級項目則是清單集合中的其他項目。 針對無效的方向，此方法會傳回 `null` (在 Visual Basic 中為`Nothing` )；在這個案例中，因為項目沒有子系，所以會傳回 <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> 和 <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>。  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>另請參閱

- [UI 自動化提供者概觀](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [伺服器端 UI 自動化提供者實作](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
