---
title: 在用戶端應用程式中實作 UI 自動化提供者
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client-side UI Automation provider, implementation within applications
- UI Automation, implementing client-side provider within application
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
ms.openlocfilehash: b368ab3bc842fda5a99a64e0220093ebd60698b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609811"
---
# <a name="implement-ui-automation-providers-in-a-client-application"></a>在用戶端應用程式中實作 UI 自動化提供者
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需最新資訊[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]，請參閱[Windows Automation API:使用者介面自動化](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題包含範例程式碼，說明如何在應用程式內實作用戶端的使用者介面自動化提供者。  
  
 這個情況較不常見。 通常，使用者介面自動化用戶端應用程式會使用伺服器端提供者，或位於 DLL 中的用戶端提供者。  
  
## <a name="example"></a>範例  
 下列範例程式碼會實作簡單的主控台視窗提供者。 這個程式碼並沒有太大的功用，只是用來展示在用戶端程式碼中設定提供者，以及使用 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A>註冊的基本步驟。  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## <a name="see-also"></a>另請參閱

- [UI 自動化提供者概觀](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [註冊用戶端提供者組件](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
- [建立用戶端 UI 自動化提供者](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)
- [用戶端 UI 自動化提供者實作](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)
