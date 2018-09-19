---
title: 如何：繫結至 Web 服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 84c5aee8d2bc7d31ebcfee98930d9a0847c527d5
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46323865"
---
# <a name="how-to-bind-to-a-web-service"></a>如何：繫結至 Web 服務
此範例示範如何繫結至 Web 服務方法呼叫所傳回的物件。  
  
## <a name="example"></a>範例  
 這個範例會使用[MSDN/TechNet 發佈系統 (MTPS) 內容服務](https://go.microsoft.com/fwlink/?LinkId=95677)擷取所指定的文件支援的語言清單。  
  
 呼叫 Web 服務之前，您需要建立它的參考。 若要建立 Web 參考加入 MTPS 服務會使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，請遵循下列步驟：  
  
1.  開啟您的專案中[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]。  
  
2.  從**專案**功能表上，按一下**加入 Web 參考**。  
  
3.  在對話方塊中，將**URL**要[ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。  
  
4.  按下**移**，然後**將參考加入**。  
  
 接下來，您可以呼叫 Web 服務方法，並設定<xref:System.Windows.FrameworkElement.DataContext%2A>適當的控制項或視窗中傳回的物件。 **GetContent** MTPS 服務的方法，會參考**getContentRequest**物件。 因此，下列範例會先設定要求物件：  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 在後<xref:System.Windows.FrameworkElement.DataContext%2A>已設定，您可以建立繫結至物件的屬性，<xref:System.Windows.FrameworkElement.DataContext%2A>已設為。 在此範例中，<xref:System.Windows.FrameworkElement.DataContext%2A>設定為**getContentResponse**所傳回的物件**GetContent**方法。 在下列範例中，<xref:System.Windows.Controls.ItemsControl>繫結至並顯示**地區設定**的值**availableVersionsAndLocales**的**getContentResponse**。  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 如需結構的詳細資訊**getContentResponse**，請參閱[內容的服務文件](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx)。  
  
## <a name="see-also"></a>另請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
