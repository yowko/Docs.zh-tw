---
title: 建立用戶端 UI 自動化提供者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
ms.openlocfilehash: 722b6db8a777f0e945b91fa7fa27db0dd2858d7b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629541"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="97b03-102">建立用戶端 UI 自動化提供者</span><span class="sxs-lookup"><span data-stu-id="97b03-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
>  <span data-ttu-id="97b03-103">這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="97b03-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="97b03-104">如需的最新[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]資訊, [請參閱 Windows Automation API:使用者介面](https://go.microsoft.com/fwlink/?LinkID=156746)自動化。</span><span class="sxs-lookup"><span data-stu-id="97b03-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="97b03-105">本主題包含範例程式碼，說明如何實作用戶端的使用者介面自動化提供者。</span><span class="sxs-lookup"><span data-stu-id="97b03-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97b03-106">範例</span><span class="sxs-lookup"><span data-stu-id="97b03-106">Example</span></span>  
 <span data-ttu-id="97b03-107">下列程式碼範例可以內建在動態連結程式庫 (DLL) 中, 以在主控台視窗中執行非常簡單的用戶端提供者。</span><span class="sxs-lookup"><span data-stu-id="97b03-107">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="97b03-108">這個程式碼並沒有任何實際用途，只是用來示範設定提供者組件的基本步驟 (這個組件可由使用者介面自動化用戶端應用程式註冊)。</span><span class="sxs-lookup"><span data-stu-id="97b03-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="97b03-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97b03-109">See also</span></span>

- [<span data-ttu-id="97b03-110">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="97b03-110">UI Automation Providers Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [<span data-ttu-id="97b03-111">註冊用戶端提供者組件</span><span class="sxs-lookup"><span data-stu-id="97b03-111">Register a Client-Side Provider Assembly</span></span>](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
