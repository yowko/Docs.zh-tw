---
title: "如何：在巡覽記錄中前移或後移 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "記錄, 巡覽, 向前巡覽"
  - "巡覽, 在巡覽記錄中 (向前)"
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：在巡覽記錄中前移或後移
這個範例說明如何巡覽向前或向後巡覽記錄中的項目。  
  
## 範例  
 您必須從下列主機中的內容執行的程式碼可巡覽向前或向後巡覽記錄中，一次一個項目。  
  
-   <xref:System.Windows.Navigation.NavigationWindow>使用<xref:System.Windows.Navigation.NavigationService>  
  
-   <xref:System.Windows.Controls.Frame>使用<xref:System.Windows.Navigation.NavigationService>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 您可以瀏覽往前一個項目之前，您首先必須檢查有項目向前巡覽記錄中檢查 **CanGoForward** 屬性。  若要瀏覽往前一個項目，您呼叫 **GoForward** 方法。  下列範例說明了這個程序：  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 您可以瀏覽之前一個項目，您必須先核取項目中沒有向後巡覽記錄來檢查 **CanGoBack** 屬性。  若要瀏覽上一步\] 其中一個項目，您呼叫 **GoBack** 方法。  下列範例說明了這個程序：  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 **CanGoForward**，  **GoForward**，  **CanGoBack**，以及 **GoBack** 由實作<xref:System.Windows.Navigation.NavigationWindow>， <xref:System.Windows.Controls.Frame>，以及<xref:System.Windows.Navigation.NavigationService>。  
  
> [!NOTE]
>  如果您呼叫 **GoForward**，向前巡覽記錄中沒有任何項目，或如果您呼叫 **GoBack**，並向後巡覽記錄中沒有任何項目<xref:System.InvalidOperationException>就會擲回。