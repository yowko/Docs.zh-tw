---
title: "如何：使用應用程式資源 | Microsoft Docs"
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
  - "應用程式資源"
  - "資源, 應用程式資源"
ms.assetid: 507ea937-5191-406b-8797-0a3d9f94156d
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 如何：使用應用程式資源
這個範例顯示如何使用應用程式資源。  
  
## 範例  
 下列範例顯示應用程式定義檔案。  應用程式定義檔案定義了資源區段 \(<xref:System.Windows.Application.Resources%2A> 屬性的值\)。  應用程式中的所有其他頁面都可以存取在應用程式層級定義的資源。  在這個案例中，資源是已宣告的樣式。  因為加入了控制項範本的完整樣式可能會很長，所以這個範例省略了在樣式的 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 屬性的 setter 中定義的控制項範本。  
  
 [!code-xml[ResourcesApplication#PreTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#pretemplateresource)]  
[!code-xml[ResourcesApplication#PostTemplateResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/app.xaml#posttemplateresource)]  
  
 下列範例顯示的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 頁面會參考上一個範例在應用程式層級定義的資源。  這個資源是由 [StaticResource 標記延伸](../../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)參考，後者會指定所要求資源的唯一資源索引鍵。  因為在目前頁面中找不到索引鍵為 "GelButton" 的資源，所以所要求資源的資源查閱範圍會繼續擴及到目前頁面以外的地方，並擴及到已定義的應用程式層級資源。  
  
 [!code-xml[ResourcesApplication#ConsumingPage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourcesApplication/CS/page1.xaml#consumingpage)]  
  
## 請參閱  
 [XAML 資源](../../../../docs/framework/wpf/advanced/xaml-resources.md)   
 [應用程式管理概觀](../../../../docs/framework/wpf/app-development/application-management-overview.md)   
 [HOW TO 主題](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)