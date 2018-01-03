---
title: "建立用戶端 UI 自動化提供者"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, creating client-side provider
- client-side UI Automation provider, creating
ms.assetid: d91edaf2-be28-41ec-a508-af421cb43c3d
caps.latest.revision: "11"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6b788d679d29a9af838b91c7b4468e10a1a8411e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="create-a-client-side-ui-automation-provider"></a>建立用戶端 UI 自動化提供者
> [!NOTE]
>  這份文件適用於想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空間中定義之 Managed <xref:System.Windows.Automation> 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新資訊，請參閱 [Windows Automation API：使用者介面自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題包含範例程式碼，說明如何實作用戶端的使用者介面自動化提供者。  
  
## <a name="example"></a>範例  
 下列範例程式碼可以建置在 [!INCLUDE[TLA#tla_dll](../../../includes/tlasharptla-dll-md.md)] 中，它會實作一個非常簡單的主控台視窗用戶端提供者。 這個程式碼並沒有任何實際用途，只是用來示範設定提供者組件的基本步驟 (這個組件可由使用者介面自動化用戶端應用程式註冊)。  
  
 [!code-csharp[UIAClientSideProvider_snip#101](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/CSProviderProgram.cs#101)]
 [!code-vb[UIAClientSideProvider_snip#101](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/csproviderprogram.vb#101)]  
  
## <a name="see-also"></a>請參閱  
 [UI 自動化提供者概觀](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [註冊用戶端提供者組件](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)
