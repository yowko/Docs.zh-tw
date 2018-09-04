---
title: 從 UI 自動化提供者傳回屬性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- providers, UI Automation, returning properties
- properties, returned by UI Automation providers
- UI Automation, providers returning properties
ms.assetid: 5eba950e-b9e1-48eb-ab8e-b69db76bf589
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 3e24d9bebc891ecdae9d3a68d700d053194374ce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527063"
---
# <a name="return-properties-from-a-ui-automation-provider"></a><span data-ttu-id="415c7-102">從 UI 自動化提供者傳回屬性</span><span class="sxs-lookup"><span data-stu-id="415c7-102">Return Properties from a UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="415c7-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="415c7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="415c7-104">如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱 < [Windows Automation API： 使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。</span><span class="sxs-lookup"><span data-stu-id="415c7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="415c7-105">本主題包含範例程式碼，示範使用者介面自動化提供者如何將項目的屬性傳回給用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="415c7-105">This topic contains sample code that shows how a UI Automation provider can return properties of an element to client applications.</span></span>  
  
 <span data-ttu-id="415c7-106">對於任何未明確支援的屬性而言，提供者必須傳回 `null` (Visual Basic 中的`Nothing` )。</span><span class="sxs-lookup"><span data-stu-id="415c7-106">For any property it does not explicitly support, the provider must return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="415c7-107">如此可確保 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 會嘗試從另一個來源取得屬性，例如裝載視窗提供者。</span><span class="sxs-lookup"><span data-stu-id="415c7-107">This ensures that [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] attempts to obtain the property from another source, such as the host window provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="415c7-108">範例</span><span class="sxs-lookup"><span data-stu-id="415c7-108">Example</span></span>  
 [!code-csharp[UIAFragmentProvider_snip#117](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#117)]
 [!code-vb[UIAFragmentProvider_snip#117](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#117)]  
  
## <a name="see-also"></a><span data-ttu-id="415c7-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="415c7-109">See Also</span></span>  
 [<span data-ttu-id="415c7-110">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="415c7-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [<span data-ttu-id="415c7-111">伺服器端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="415c7-111">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
