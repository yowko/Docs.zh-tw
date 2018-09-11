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
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264723"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="5f588-102">如何：繫結至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="5f588-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="5f588-103">此範例示範如何繫結至 Web 服務方法呼叫所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="5f588-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f588-104">範例</span><span class="sxs-lookup"><span data-stu-id="5f588-104">Example</span></span>  
 <span data-ttu-id="5f588-105">這個範例會使用[MSDN/TechNet 發佈系統 (MTPS) 內容服務](https://go.microsoft.com/fwlink/?LinkId=95677)擷取所指定的文件支援的語言清單。</span><span class="sxs-lookup"><span data-stu-id="5f588-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](https://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="5f588-106">呼叫 Web 服務之前，您需要建立它的參考。</span><span class="sxs-lookup"><span data-stu-id="5f588-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="5f588-107">若要建立 Web 參考加入 MTPS 服務會使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5f588-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="5f588-108">開啟您的專案中[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5f588-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="5f588-109">從**專案**功能表上，按一下**加入 Web 參考**。</span><span class="sxs-lookup"><span data-stu-id="5f588-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="5f588-110">在對話方塊中，將**URL**要[ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。</span><span class="sxs-lookup"><span data-stu-id="5f588-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="5f588-111">按下**移**，然後**將參考加入**。</span><span class="sxs-lookup"><span data-stu-id="5f588-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="5f588-112">接下來，您可以呼叫 Web 服務方法，並設定<xref:System.Windows.FrameworkElement.DataContext%2A>適當的控制項或視窗中傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="5f588-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="5f588-113">**GetContent** MTPS 服務的方法，會參考**getContentRequest**物件。</span><span class="sxs-lookup"><span data-stu-id="5f588-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="5f588-114">因此，下列範例會先設定要求物件：</span><span class="sxs-lookup"><span data-stu-id="5f588-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="5f588-115">在後<xref:System.Windows.FrameworkElement.DataContext%2A>已設定，您可以建立繫結至物件的屬性，<xref:System.Windows.FrameworkElement.DataContext%2A>已設為。</span><span class="sxs-lookup"><span data-stu-id="5f588-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="5f588-116">在此範例中，<xref:System.Windows.FrameworkElement.DataContext%2A>設定為**getContentResponse**所傳回的物件**GetContent**方法。</span><span class="sxs-lookup"><span data-stu-id="5f588-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="5f588-117">在下列範例中，<xref:System.Windows.Controls.ItemsControl>繫結至並顯示**地區設定**的值**availableVersionsAndLocales**的**getContentResponse**。</span><span class="sxs-lookup"><span data-stu-id="5f588-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="5f588-118">如需結構的詳細資訊**getContentResponse**，請參閱[內容的服務文件](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx)。</span><span class="sxs-lookup"><span data-stu-id="5f588-118">For information about the structure of **getContentResponse**, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f588-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f588-119">See Also</span></span>  
 [<span data-ttu-id="5f588-120">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="5f588-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="5f588-121">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="5f588-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="5f588-122">讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="5f588-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
