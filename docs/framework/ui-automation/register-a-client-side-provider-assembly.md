---
title: 註冊用戶端提供者組件
description: 請參閱示範如何註冊包含用戶端消費者介面自動化提供者之 DLL 的範例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- registering client-side provider assemblies
- client-side provider assemblies, registering
- UI Automation, registering provider assemblies
- provider assemblies, registering
ms.assetid: a03af4d9-2771-43cc-b07b-d468dca23190
ms.openlocfilehash: 1c6f7685b796b544925207a22679e6a4da455844
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250459"
---
# <a name="register-a-client-side-provider-assembly"></a><span data-ttu-id="c5a4a-103">註冊用戶端提供者組件</span><span class="sxs-lookup"><span data-stu-id="c5a4a-103">Register a Client-Side Provider Assembly</span></span>

> [!NOTE]
> <span data-ttu-id="c5a4a-104">這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。</span><span class="sxs-lookup"><span data-stu-id="c5a4a-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="c5a4a-105">如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：UI 自動化](/windows/win32/winauto/entry-uiauto-win32)。</span><span class="sxs-lookup"><span data-stu-id="c5a4a-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="c5a4a-106">本主題說明如何註冊包含用戶端使用者介面自動化提供者的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c5a4a-106">This topic shows how to register a DLL that contains client-side UI Automation providers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5a4a-107">範例</span><span class="sxs-lookup"><span data-stu-id="c5a4a-107">Example</span></span>  

 <span data-ttu-id="c5a4a-108">下列範例示範如何註冊包含主控台視窗提供者的組件。</span><span class="sxs-lookup"><span data-stu-id="c5a4a-108">The following example shows how to register an assembly that contains a provider for a console window.</span></span>  
  
 [!code-csharp[UIAClientSideProvider_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSClientProgram.cs#102)]
 [!code-vb[UIAClientSideProvider_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csclientprogram.vb#102)]  
  
## <a name="see-also"></a><span data-ttu-id="c5a4a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5a4a-109">See also</span></span>

- [<span data-ttu-id="c5a4a-110">建立用戶端 UI 自動化提供者</span><span class="sxs-lookup"><span data-stu-id="c5a4a-110">Create a Client-Side UI Automation Provider</span></span>](create-a-client-side-ui-automation-provider.md)
