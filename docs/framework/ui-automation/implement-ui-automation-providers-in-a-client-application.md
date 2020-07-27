---
title: 在用戶端應用程式中實作 UI 自動化提供者
description: 請參閱如何在應用程式中執行用戶端 UI 自動化提供者的範例。 請注意，這是不尋常的案例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: c604b68021886abdf06360bfb8afefe3640c12fe
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164114"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a><span data-ttu-id="c12cb-104">在用戶端應用程式中實作 UI 自動化提供者</span><span class="sxs-lookup"><span data-stu-id="c12cb-104">Implement UI Automation Providers in a Client Application</span></span>
> [!NOTE]
> <span data-ttu-id="c12cb-105">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="c12cb-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c12cb-106">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="c12cb-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c12cb-107">本主題包含範例程式碼，說明如何在應用程式內實作用戶端的使用者介面自動化提供者。</span><span class="sxs-lookup"><span data-stu-id="c12cb-107">This topic contains example code that shows how to implement a client-side UI Automation provider within an application.</span></span>  
  
 <span data-ttu-id="c12cb-108">這個情況較不常見。</span><span class="sxs-lookup"><span data-stu-id="c12cb-108">This is an uncommon scenario.</span></span> <span data-ttu-id="c12cb-109">通常，使用者介面自動化用戶端應用程式會使用伺服器端提供者，或位於 DLL 中的用戶端提供者。</span><span class="sxs-lookup"><span data-stu-id="c12cb-109">Most often, a UI Automation client application uses server-side providers, or client-side providers that reside in a DLL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c12cb-110">範例</span><span class="sxs-lookup"><span data-stu-id="c12cb-110">Example</span></span>  
 <span data-ttu-id="c12cb-111">下列範例程式碼會實作簡單的主控台視窗提供者。</span><span class="sxs-lookup"><span data-stu-id="c12cb-111">The following example code implements a simple provider for a console window.</span></span> <span data-ttu-id="c12cb-112">這個程式碼並沒有太大的功用，只是用來展示在用戶端程式碼中設定提供者，以及使用 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>註冊的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="c12cb-112">The code does not have any useful functionality, but is intended to demonstrate the basic steps in setting up a provider within client code and registering it by using <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="c12cb-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c12cb-113">See also</span></span>

- [<span data-ttu-id="c12cb-114">UI 自動化提供者概觀</span><span class="sxs-lookup"><span data-stu-id="c12cb-114">UI Automation Providers Overview</span></span>](ui-automation-providers-overview.md)
- [<span data-ttu-id="c12cb-115">註冊用戶端提供者組件</span><span class="sxs-lookup"><span data-stu-id="c12cb-115">Register a Client-Side Provider Assembly</span></span>](register-a-client-side-provider-assembly.md)
- [<span data-ttu-id="c12cb-116">建立用戶端 UI 自動化提供者</span><span class="sxs-lookup"><span data-stu-id="c12cb-116">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
- [<span data-ttu-id="c12cb-117">用戶端 UI 自動化提供者實作</span><span class="sxs-lookup"><span data-stu-id="c12cb-117">Client-Side UI Automation Provider Implementation</span></span>](client-side-ui-automation-provider-implementation.md)
