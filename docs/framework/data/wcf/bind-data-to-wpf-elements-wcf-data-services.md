---
title: HOW TO：將資料系結至 Windows Presentation Foundation 元素（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: d6538ab0-0abe-426a-b9d9-e6f3a5ca2016
ms.openlocfilehash: 44f3361aa56d9f15e62852000accd0b4d4d8eb43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791138"
---
# <a name="how-to-bind-data-to-windows-presentation-foundation-elements-wcf-data-services"></a>作法：將資料系結至 Windows Presentation Foundation 元素（WCF Data Services）
藉[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]由，您可以將 Windows Presentation Foundation （WPF）專案（例如<xref:System.Windows.Controls.ListBox> <xref:System.Data.Services.Client.DataServiceCollection%601>或<xref:System.Windows.Controls.ComboBox> ）系結至的實例，以處理控制項所引發的事件，以<xref:System.Data.Services.Client.DataServiceContext>保持與變更同步處理的內容對控制項中的資料進行。 如需詳細資訊，請參閱[將資料系結至控制項](binding-data-to-controls-wcf-data-services.md)。  
  
 本主題中的範例使用 Northwind 範例資料服務和自動產生的用戶端資料服務類別。 當您完成[WCF Data Services 快速入門](quickstart-wcf-data-services.md)時，會建立此服務和用戶端資料類別。  
  
## <a name="example"></a>範例  
 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 (XAML) 頁面的程式碼後置頁面。 載入視窗時， <xref:System.Data.Services.Client.DataServiceCollection%601>會根據傳回客戶的查詢結果（依國家/地區篩選）來建立。 此分頁結果的所有頁面都會載入 (包含相關的訂單)，並且會繫結至 <xref:System.Windows.FrameworkElement.DataContext%2A> (WPF 視窗的根配置控制項) 的 <xref:System.Windows.Controls.StackPanel> 屬性。 如需詳細資訊，請參閱[載入延](loading-deferred-content-wcf-data-services.md)後的內容。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddata)]
 [!code-vb[Astoria Northwind Client#BindPagedData](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddata)]  
  
## <a name="example"></a>範例  
 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xaml[Astoria Northwind Client#BindPagedDataXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml#bindpageddataxaml)]  
  
## <a name="example"></a>範例  
 下列範例取自用於定義 WPF 中 `SalesOrders` 視窗之可延伸應用程式標記語言 (XAML) 頁面的程式碼後置頁面。 載入視窗時， <xref:System.Data.Services.Client.DataServiceCollection%601>會根據傳回具有相關物件之客戶的查詢結果（依國家/地區篩選）來建立。 此結果繫結至 <xref:System.Windows.FrameworkElement.DataContext%2A> (WPF 視窗的根配置控制項) 的 <xref:System.Windows.Controls.StackPanel> 屬性。  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#wpfdatabinding)]
 [!code-vb[Astoria Northwind Client#WpfDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#wpfdatabinding)]  
  
## <a name="example"></a>範例  
 下列 XAML 會在 WPF 中定義前一個範例的 `SalesOrders` 視窗。  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#wpfdatabindingxaml)]
