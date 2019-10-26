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
ms.openlocfilehash: 72638101b73e6b43fa225885b2e1f27d87b22826
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920151"
---
# <a name="how-to-bind-to-a-web-service"></a>如何：繫結至 Web 服務
這個範例示範如何系結至 Web 服務方法呼叫所傳回的物件。  
  
## <a name="example"></a>範例  
 這個範例會使用[MSDN/TechNet 發行系統（MTPS）內容服務](https://go.microsoft.com/fwlink/?LinkId=95677)來抓取指定檔所支援的語言清單。  
  
 在您呼叫 Web 服務之前，您必須先建立對它的參考。 若要使用 Visual Studio 建立 MTPS 服務的 Web 參考，請遵循下列步驟：  
  
1. 在 Visual Studio 中開啟專案。  
  
2. 從 [**專案**] 功能表中，按一下 [**加入 Web 參考**]。  
  
3. 在對話方塊中，將**URL**設定為[http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。  
  
4. 按 [**移至**]，然後按一下 [**新增參考**]。  
  
 接下來，您可以呼叫 Web 服務方法，並將適當控制項或視窗的 <xref:System.Windows.FrameworkElement.DataContext%2A> 設定為傳回的物件。 MTPS 服務的**GetContent**方法會接受**getContentRequest**物件的參考。 因此，下列範例會先設定 request 物件：  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 設定 <xref:System.Windows.FrameworkElement.DataContext%2A> 之後，您可以建立已設定 <xref:System.Windows.FrameworkElement.DataContext%2A> 之物件屬性的系結。 在此範例中，<xref:System.Windows.FrameworkElement.DataContext%2A> 設定為**GetContent**方法所傳回的**getContentResponse**物件。 在下列範例中，<xref:System.Windows.Controls.ItemsControl> 系結至，並顯示**GetContentResponse** **availableVersionsAndLocales**的**地區**設定值。  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 如需**getContentResponse**結構的詳細資訊，請參閱[內容服務檔](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx)。  
  
## <a name="see-also"></a>請參閱

- [資料繫結概觀](data-binding-overview.md)
- [繫結來源概觀](binding-sources-overview.md)
- [讓資料可於 XAML 中繫結](how-to-make-data-available-for-binding-in-xaml.md)
