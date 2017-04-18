---
title: "傳遞 URI 給 Windows 執行階段 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Windows 執行階段, 供下列項目的 .NET Framework 支援"
  - "Windows 執行階段, 將 URI 傳遞給"
ms.assetid: 3eb5ce6f-f304-4f87-8e81-0f25092f5ad4
caps.latest.revision: 10
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 10
---
# 傳遞 URI 給 Windows 執行階段
Windows Runtime 方法僅接受絕對 URI。 如果您傳遞相關 URI 至 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 方法，則會擲回 <xref:System.ArgumentException> 例外狀況。 原因如下：當您在 .NET Framework 程式碼中使用 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 時，[Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) 類別在 Intellisense 中會顯示成 <xref:System.Uri?displayProperty=fullName>。<xref:System.Uri?displayProperty=fullName> 類別允許相關的 URI，但 [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376) 類別不允許。 對於您公開在 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件中的方法也是如此。 如果您的元件公開採用 URI 的方法，則程式碼中的簽章包含 <xref:System.Uri?displayProperty=fullName>。 不過，對元件的使用者而言，簽章包含 [Windows.Foundation.Uri](http://go.microsoft.com/fwlink/p/?LinkId=238376)。 傳遞至元件的 URI 必須是絕對 URI。  
  
 此主題示範如何偵測絕對 URI，以及參考應用程式套件中的資源時，如何建立 URI。  
  
## 偵測及使用絕對 URI  
 使用 <xref:System.Uri.IsAbsoluteUri%2A?displayProperty=fullName> 屬性可在將 URI 傳遞至 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 之前，先確定 URI 是絕對的。 使用此屬性比攔截並處理 <xref:System.ArgumentException> 例外狀況更有效率。  
  
## 將絕對 URI 用於應用程式套件中的資源  
 如果您想要為應用程式套件中包含的資源指定 URI，可以使用 `ms-appx` 或 `ms-appx-web` 結構描述來建立絕對 URI。  
  
 下列範例示範如何同時使用 XAML 和程式碼，將 [WebView](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.aspx) 控制項的 [Source](http://msdn.microsoft.com/library/windows/apps/xaml/windows.ui.xaml.controls.webview.source.aspx) 屬性以及 [Image](http://msdn.microsoft.com/library/windows/apps/br242752.aspx) 控制項的 [Source](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.image.source.aspx) 屬性設定為 Pages 資料夾中所含的資源。  
  
 [!code-xml[System.URIToWindowsURI#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml#1)]  
[!code-csharp[System.URIToWindowsURI#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.uritowindowsuri/cs/mainpage.xaml.cs#2)]
[!code-vb[System.URIToWindowsURI#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.uritowindowsuri/vb/mainpage.xaml.vb#2)]  
  
 如需這些結構描述的詳細資訊，請參閱 Windows 開發人員中心的 [URI 配置](http://msdn.microsoft.com/library/windows/apps/jj655406.aspx)。  
  
## 請參閱  
 [適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)