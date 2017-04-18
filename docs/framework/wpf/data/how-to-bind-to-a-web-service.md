---
title: "如何：繫結至 Web 服務 | Microsoft Docs"
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
  - "資料繫結, Web 服務"
  - "資料繫結, Web 服務"
  - "Web 服務繫結"
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: 6
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 6
---
# 如何：繫結至 Web 服務
這個範例顯示如何繫結至 Web 服務方法呼叫所傳回的物件。  
  
## 範例  
 這個範例會使用 [MSDN\/TechNet 發行系統 \(MTPS\) 內容服務](http://go.microsoft.com/fwlink/?LinkId=95677) \(英文\) 擷取指定的文件所支援的語言清單。  
  
 在呼叫 Web 服務之前，您必須先建立其參考。  若要使用 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] 建立 MTPS 服務的 Web 參考，請遵循下列步驟：  
  
1.  在 [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] 中開啟專案。  
  
2.  在 \[**專案**\] 功能表中，按一下 \[**加入 Web 參考**\]。  
  
3.  在對話方塊中，將 \[**URL**\] 設為 [http:\/\/services.msdn.microsoft.com\/contentservices\/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。  
  
4.  按 \[**執行**\]，再按 \[**加入參考**\]。  
  
 接著，您會呼叫 Web 服務方法，並將適當控制項或視窗的 <xref:System.Windows.FrameworkElement.DataContext%2A> 設為傳回的物件。  MTPS 服務的 **GetContent** 方法會採用 **getContentRequest** 物件的參考。  因此，下列範例會先設定要求物件：  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 在設定 <xref:System.Windows.FrameworkElement.DataContext%2A> 後，您可以針對由 <xref:System.Windows.FrameworkElement.DataContext%2A> 所設定而成的物件設定其屬性的繫結。  在這個範例中，<xref:System.Windows.FrameworkElement.DataContext%2A> 會設為 **GetContent** 方法所傳回的 **getContentResponse** 物件。  在下列範例中，<xref:System.Windows.Controls.ItemsControl> 會繫結至並顯示 **availableVersionsAndLocales** 的 **locale** 值 **getContentResponse**。  
  
 [!code-xml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 如需 **getContentResponse** 結構的詳細資訊，請參閱[內容服務文件](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx) \(英文\)。  
  
## 請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)