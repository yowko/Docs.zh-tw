---
title: "如何：繫結至 Web 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b035f5922722a05759ff1e13514cc760a57d668
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-a-web-service"></a>如何：繫結至 Web 服務
這個範例示範如何繫結至 Web 服務方法呼叫所傳回的物件。  
  
## <a name="example"></a>範例  
 這個範例會使用[MSDN/TechNet 發佈系統 (MTPS) 內容服務](http://go.microsoft.com/fwlink/?LinkId=95677)擷取所指定的文件支援的語言清單。  
  
 呼叫 Web 服務之前，您需要建立它的參考。 若要建立 Web 參考加入為 MTPS 服務會使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，請遵循下列步驟：  
  
1.  開啟您的專案中[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]。  
  
2.  從**專案**功能表上，按一下 **加入 Web 參考**。  
  
3.  在對話方塊中，設定**URL**至[http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。  
  
4.  按**移**然後**將參考加入**。  
  
 接下來，您可以呼叫 Web 服務方法，並設定<xref:System.Windows.FrameworkElement.DataContext%2A>適當的控制項或視窗中傳回的物件。 **GetContent** MTPS 服務方法會採用參考**getContentRequest**物件。 因此，下列範例會先設定要求物件：  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 之後<xref:System.Windows.FrameworkElement.DataContext%2A>已設定，建立物件的屬性繫結<xref:System.Windows.FrameworkElement.DataContext%2A>已設定為。 在此範例中，<xref:System.Windows.FrameworkElement.DataContext%2A>設**getContentResponse**所傳回物件**GetContent**方法。 在下列範例中，<xref:System.Windows.Controls.ItemsControl>繫結，而且會顯示**地區設定**值**availableVersionsAndLocales**的**getContentResponse**。  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 如需結構的資訊**getContentResponse**，請參閱[內容的服務文件](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx)。  
  
## <a name="see-also"></a>請參閱  
 [資料繫結概觀](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [繫結來源概觀](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [讓資料可於 XAML 中繫結](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
