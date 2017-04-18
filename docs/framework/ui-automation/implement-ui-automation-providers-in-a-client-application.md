---
title: "Implement UI Automation Providers in a Client Application | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "client-side UI Automation provider, implementation within applications"
  - "UI Automation, implementing client-side provider within application"
ms.assetid: f325f0d8-1715-41ea-85ca-45b82ffea8bc
caps.latest.revision: 6
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 6
---
# Implement UI Automation Providers in a Client Application
> [!NOTE]
>  這份文件適用於想要使用 <xref:System.Windows.Automation> 命名空間中定義之 Managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 類別的 .NET Framework 開發人員。 如需 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 的最新資訊，請參閱 [Windows Automation API：UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 本主題包含範例程式碼，說明如何在應用程式內實作用戶端的使用者介面自動化提供者。  
  
 這個情況較不常見。 通常，使用者介面自動化用戶端應用程式會使用伺服器端提供者，或位於 DLL 中的用戶端提供者。  
  
## 範例  
 下列範例程式碼會實作簡單的主控台視窗提供者。 這個程式碼並沒有太大的功用，只是用來展示在用戶端程式碼中設定提供者，以及使用 <xref:System.Windows.Automation.ClientSettings.RegisterClientSideProviders%2A> 註冊的基本步驟。  
  
 [!code-csharp[UIAClientSideProvider_snip#201](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClientSideProvider_snip/CSharp/ClientImplementationProgram.cs#201)]
 [!code-vb[UIAClientSideProvider_snip#201](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClientSideProvider_snip/visualbasic/clientimplementationprogram.vb#201)]  
  
## 請參閱  
 [UI Automation Providers Overview](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)   
 [Register a Client\-Side Provider Assembly](../../../docs/framework/ui-automation/register-a-client-side-provider-assembly.md)   
 [Create a Client\-Side UI Automation Provider](../../../docs/framework/ui-automation/create-a-client-side-ui-automation-provider.md)   
 [Client\-Side UI Automation Provider Implementation](../../../docs/framework/ui-automation/client-side-ui-automation-provider-implementation.md)