---
title: 如何：將資料繫結至 Windows Presentation Foundation 項目 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: d6f50fb849d958ae1109324f1055b84451bde5a9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191628"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>如何：將資料繫結至 Windows Presentation Foundation 項目 (WCF 資料服務)

使用 WCF Data Services，您可以將 Windows Presentation Foundation (WPF) 專案（例如 <xref:System.Windows.Controls.ListBox> 或）系結 <xref:System.Windows.Controls.ComboBox> 至的實例，以 <xref:System.Data.Services.Client.DataServiceCollection%601> 處理控制項所引發的事件，讓與 <xref:System.Data.Services.Client.DataServiceContext> 控制項中對資料所做的變更保持同步。 如需詳細資訊，請參閱 [將資料系結至控制項](binding-data-to-controls-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 此服務和用戶端資料類別會在您完成 [WCF Data Services 快速入門](quickstart-wcf-data-services.md)時建立。  
  
## <a name="example"></a>範例  

 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 (XAML) 頁面的程式碼後置頁面。 載入視窗時， <xref:System.Data.Services.Client.DataServiceCollection%601> 會根據傳回客戶的查詢結果（依國家/地區篩選）來建立。 此分頁結果的所有頁面都會載入 (包含相關的訂單)，並且會繫結至 <xref:System.Windows.FrameworkElement.DataContext%2A> (WPF 視窗的根配置控制項) 的 <xref:System.Windows.Controls.StackPanel> 屬性。 如需詳細資訊，請參閱 [載入延遲的內容](loading-deferred-content-wcf-data-services.md)。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>範例  

 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>範例  

 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 (XAML) 頁面的程式碼後置頁面。 載入視窗時， <xref:System.Data.Services.Client.DataServiceCollection%601> 會根據傳回客戶相關物件的查詢結果（依國家/地區篩選）來建立。 此結果繫結至 <xref:System.Windows.FrameworkElement.DataContext%2A> (WPF 視窗的根配置控制項) 的 <xref:System.Windows.Controls.StackPanel> 屬性。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>範例  

 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
