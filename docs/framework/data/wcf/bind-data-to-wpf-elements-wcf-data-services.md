---
title: HOW TO：將資料繫結至 Windows Presentation Foundation 項目 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: 1deb5bcc29e43720929951764d1fcfeee8e89f8c
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517391"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>HOW TO：將資料繫結至 Windows Presentation Foundation 項目 (WCF Data Services)
與[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，您可以將繫結 Windows Presentation Foundation (WPF) 項目這類<xref:System.Windows.Controls.ListBox>或<xref:System.Windows.Controls.ComboBox>的執行個體<xref:System.Data.Services.Client.DataServiceCollection%601>，處理要保留控制項所引發的事件<xref:System.Data.Services.Client.DataServiceContext>與變更保持同步對控制項中的資料。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成建立這項服務和用戶端資料類別[WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。  
  
## <a name="example"></a>範例  
 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 (XAML) 頁面的程式碼後置頁面。 載入視窗時，會根據傳回客戶 (按國家 (地區) 排序) 查詢的結果建立 <xref:System.Data.Services.Client.DataServiceCollection%601>。 此分頁結果的所有頁面都會載入 (包含相關的訂單)，並且會繫結至 <xref:System.Windows.FrameworkElement.DataContext%2A> (WPF 視窗的根配置控制項) 的 <xref:System.Windows.Controls.StackPanel> 屬性。 如需詳細資訊，請參閱 <<c0> [ 載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>範例  
 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>範例  
 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 (XAML) 頁面的程式碼後置頁面。 載入視窗時，會根據傳回客戶及相關物件 (按國家 (地區) 排序) 查詢的結果建立 <xref:System.Data.Services.Client.DataServiceCollection%601>。 此結果繫結至 <xref:System.Windows.FrameworkElement.DataContext%2A> (WPF 視窗的根配置控制項) 的 <xref:System.Windows.Controls.StackPanel> 屬性。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>範例  
 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
