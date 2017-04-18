---
title: "HOW TO：將資料繫結至 Windows Presentation Foundation 項目 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "資料繫結 , WCF Data Services"
  - "WCF Data Services, 資料繫結 "
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# HOW TO：將資料繫結至 Windows Presentation Foundation 項目 (WCF Data Services)
使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 時，您可以將 Windows Presentation Foundation \(WPF\) 項目 \(例如 <xref:System.Windows.Controls.ListBox>``或 <xref:System.Windows.Controls.ComboBox>\) 繫結至 <xref:System.Data.Services.Client.DataServiceCollection%601> 的執行個體，此執行個體會處理控制項所引發的事件，讓 <xref:System.Data.Services.Client.DataServiceContext> 與控制項中對資料所進行的變更保持同步。  如需詳細資訊，請參閱[將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。  此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)時建立。  
  
## 範例  
 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 \(XAML\) 頁面的程式碼後置頁面。  載入視窗時，會根據傳回客戶 \(按國家 \(地區\) 排序\) 查詢的結果建立 <xref:System.Data.Services.Client.DataServiceCollection%601>。  此分頁結果的所有頁面都會載入 \(包含相關的訂單\)，並且會繫結至 <xref:System.Windows.Controls.StackPanel> \(WPF 視窗的根配置控制項\) 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性。  如需詳細資訊，請參閱[載入延後的內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## 範例  
 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## 範例  
 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 \(XAML\) 頁面的程式碼後置頁面。  載入視窗時，會根據傳回客戶及相關物件 \(按國家 \(地區\) 排序\) 查詢的結果建立 <xref:System.Data.Services.Client.DataServiceCollection%601>。  此結果繫結至 <xref:System.Windows.Controls.StackPanel> \(WPF 視窗的根配置控制項\) 的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## 範例  
 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]