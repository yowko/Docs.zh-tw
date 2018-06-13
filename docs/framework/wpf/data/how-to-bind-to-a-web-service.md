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
ms.openlocfilehash: 75d9d5b6981f868c7a172edd7f23cf923fedd525
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557286"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="49038-102">如何：繫結至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="49038-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="49038-103">這個範例示範如何繫結至 Web 服務方法呼叫所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="49038-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="49038-104">範例</span><span class="sxs-lookup"><span data-stu-id="49038-104">Example</span></span>  
 <span data-ttu-id="49038-105">這個範例會使用[MSDN/TechNet 發佈系統 (MTPS) 內容服務](http://go.microsoft.com/fwlink/?LinkId=95677)擷取所指定的文件支援的語言清單。</span><span class="sxs-lookup"><span data-stu-id="49038-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](http://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="49038-106">呼叫 Web 服務之前，您需要建立它的參考。</span><span class="sxs-lookup"><span data-stu-id="49038-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="49038-107">若要建立 Web 參考加入為 MTPS 服務會使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="49038-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="49038-108">開啟您的專案中[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="49038-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="49038-109">從**專案**功能表上，按一下 **加入 Web 參考**。</span><span class="sxs-lookup"><span data-stu-id="49038-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="49038-110">在對話方塊中，設定**URL**至[ http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl ](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。</span><span class="sxs-lookup"><span data-stu-id="49038-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="49038-111">按**移**然後**將參考加入**。</span><span class="sxs-lookup"><span data-stu-id="49038-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="49038-112">接下來，您可以呼叫 Web 服務方法，並設定<xref:System.Windows.FrameworkElement.DataContext%2A>適當的控制項或視窗中傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="49038-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="49038-113">**GetContent** MTPS 服務方法會採用參考**getContentRequest**物件。</span><span class="sxs-lookup"><span data-stu-id="49038-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="49038-114">因此，下列範例會先設定要求物件：</span><span class="sxs-lookup"><span data-stu-id="49038-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="49038-115">之後<xref:System.Windows.FrameworkElement.DataContext%2A>已設定，建立物件的屬性繫結<xref:System.Windows.FrameworkElement.DataContext%2A>已設定為。</span><span class="sxs-lookup"><span data-stu-id="49038-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="49038-116">在此範例中，<xref:System.Windows.FrameworkElement.DataContext%2A>設**getContentResponse**所傳回物件**GetContent**方法。</span><span class="sxs-lookup"><span data-stu-id="49038-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="49038-117">在下列範例中，<xref:System.Windows.Controls.ItemsControl>繫結，而且會顯示**地區設定**值**availableVersionsAndLocales**的**getContentResponse**。</span><span class="sxs-lookup"><span data-stu-id="49038-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="49038-118">如需結構的資訊**getContentResponse**，請參閱[內容的服務文件](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx)。</span><span class="sxs-lookup"><span data-stu-id="49038-118">For information about the structure of **getContentResponse**, see [Content Service documentation](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49038-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49038-119">See Also</span></span>  
 [<span data-ttu-id="49038-120">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="49038-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="49038-121">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="49038-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="49038-122">讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="49038-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
