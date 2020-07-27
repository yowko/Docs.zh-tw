---
title: 在 UI 自動化片段提供者中啟用巡覽
description: 閱讀示範如何在使用者介面自動化提供者中，針對片段內的專案啟用導覽的範例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: bf9e43e9d70b9191fba93e5efa4eae544196c735
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168492"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a><span data-ttu-id="89b4d-103">在 UI 自動化片段提供者中啟用巡覽</span><span class="sxs-lookup"><span data-stu-id="89b4d-103">Enable Navigation in a UI Automation Fragment Provider</span></span>
> [!NOTE]
> <span data-ttu-id="89b4d-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="89b4d-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="89b4d-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="89b4d-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="89b4d-106">本主題包含範例程式碼，顯示如何針對片段內的項目，在使用者介面自動化提供者中啟用巡覽。</span><span class="sxs-lookup"><span data-stu-id="89b4d-106">This topic contains example code that shows how to enable navigation in a UI Automation provider for an element that is within a fragment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89b4d-107">範例</span><span class="sxs-lookup"><span data-stu-id="89b4d-107">Example</span></span>  
 <span data-ttu-id="89b4d-108">下列範例程式碼針對清單內的清單項目實作 <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> 。</span><span class="sxs-lookup"><span data-stu-id="89b4d-108">The following example code implements <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> for a list item within a list.</span></span> <span data-ttu-id="89b4d-109">父項目是清單方塊項目，同層級項目則是清單集合中的其他項目。</span><span class="sxs-lookup"><span data-stu-id="89b4d-109">The parent element is the list box element, and the sibling elements are other items in the list collection.</span></span> <span data-ttu-id="89b4d-110">針對無效的方向，此方法會傳回 `null` (在 Visual Basic 中為`Nothing` )；在這個案例中，因為項目沒有子系，所以會傳回 <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> 和 <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>。</span><span class="sxs-lookup"><span data-stu-id="89b4d-110">The method returns `null` (`Nothing` in Visual Basic) for directions that are not valid; in this case, <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> and <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>, because the element has no children.</span></span>  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="89b4d-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89b4d-111">See also</span></span>

- [<span data-ttu-id="89b4d-112">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="89b4d-112">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="89b4d-113">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="89b4d-113">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
