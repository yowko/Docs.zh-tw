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
ms.openlocfilehash: 79accd23392ff9e1e8157348f7a1042ee2b3cc47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433661"
---
# <a name="create-a-client-side-ui-automation-provider"></a><span data-ttu-id="f5c75-102">建立用戶端 UI 自動化提供者</span><span class="sxs-lookup"><span data-stu-id="f5c75-102">Create a Client-Side UI Automation Provider</span></span>
> [!NOTE]
> <span data-ttu-id="f5c75-103">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="f5c75-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f5c75-104">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="f5c75-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f5c75-105">本主題包含範例程式碼，說明如何實作用戶端的使用者介面自動化提供者。</span><span class="sxs-lookup"><span data-stu-id="f5c75-105">This topic contains example code that shows how to implement a client-side UI Automation provider.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5c75-106">範例</span><span class="sxs-lookup"><span data-stu-id="f5c75-106">Example</span></span>  
 <span data-ttu-id="f5c75-107">下列程式碼範例可以內建在動態連結程式庫（DLL）中，以在主控台視窗中執行非常簡單的用戶端提供者。</span><span class="sxs-lookup"><span data-stu-id="f5c75-107">The following example code can be built into a dynamic-link library (DLL) that implements a very simple client-side provider for a console window.</span></span> <span data-ttu-id="f5c75-108">這個程式碼並沒有任何實際用途，只是用來示範設定提供者組件的基本步驟 (這個組件可由使用者介面自動化用戶端應用程式註冊)。</span><span class="sxs-lookup"><span data-stu-id="f5c75-108">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider assembly that can be registered by a UI Automation client application.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a><span data-ttu-id="f5c75-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5c75-109">See also</span></span>

- [<span data-ttu-id="f5c75-110">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="f5c75-110">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="f5c75-111">註冊用戶端提供者組件</span><span class="sxs-lookup"><span data-stu-id="f5c75-111">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
