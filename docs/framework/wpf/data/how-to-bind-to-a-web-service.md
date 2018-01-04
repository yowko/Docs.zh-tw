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
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="f98df-102">如何：繫結至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="f98df-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="f98df-103">這個範例示範如何繫結至 Web 服務方法呼叫所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="f98df-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f98df-104">範例</span><span class="sxs-lookup"><span data-stu-id="f98df-104">Example</span></span>  
 <span data-ttu-id="f98df-105">這個範例會使用[MSDN/TechNet 發佈系統 (MTPS) 內容服務](http://go.microsoft.com/fwlink/?LinkId=95677)擷取所指定的文件支援的語言清單。</span><span class="sxs-lookup"><span data-stu-id="f98df-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](http://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="f98df-106">呼叫 Web 服務之前，您需要建立它的參考。</span><span class="sxs-lookup"><span data-stu-id="f98df-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="f98df-107">若要建立 Web 參考加入為 MTPS 服務會使用[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="f98df-107">To create a Web reference to the MTPS service using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], follow the following steps:</span></span>  
  
1.  <span data-ttu-id="f98df-108">開啟您的專案中[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f98df-108">Open your project in [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="f98df-109">從**專案**功能表上，按一下 **加入 Web 參考**。</span><span class="sxs-lookup"><span data-stu-id="f98df-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3.  <span data-ttu-id="f98df-110">在對話方塊中，設定**URL**至[http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。</span><span class="sxs-lookup"><span data-stu-id="f98df-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4.  <span data-ttu-id="f98df-111">按**移**然後**將參考加入**。</span><span class="sxs-lookup"><span data-stu-id="f98df-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="f98df-112">接下來，您可以呼叫 Web 服務方法，並設定<xref:System.Windows.FrameworkElement.DataContext%2A>適當的控制項或視窗中傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="f98df-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="f98df-113">**GetContent** MTPS 服務方法會採用參考**getContentRequest**物件。</span><span class="sxs-lookup"><span data-stu-id="f98df-113">The **GetContent** method of the MTPS service takes a reference to the **getContentRequest** object.</span></span> <span data-ttu-id="f98df-114">因此，下列範例會先設定要求物件：</span><span class="sxs-lookup"><span data-stu-id="f98df-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="f98df-115">之後<xref:System.Windows.FrameworkElement.DataContext%2A>已設定，建立物件的屬性繫結<xref:System.Windows.FrameworkElement.DataContext%2A>已設定為。</span><span class="sxs-lookup"><span data-stu-id="f98df-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="f98df-116">在此範例中，<xref:System.Windows.FrameworkElement.DataContext%2A>設**getContentResponse**所傳回物件**GetContent**方法。</span><span class="sxs-lookup"><span data-stu-id="f98df-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the **getContentResponse** object returned by the **GetContent** method.</span></span> <span data-ttu-id="f98df-117">在下列範例中，<xref:System.Windows.Controls.ItemsControl>繫結，而且會顯示**地區設定**值**availableVersionsAndLocales**的**getContentResponse**。</span><span class="sxs-lookup"><span data-stu-id="f98df-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the **locale** values of **availableVersionsAndLocales** of **getContentResponse**.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="f98df-118">如需結構的資訊**getContentResponse**，請參閱[內容的服務文件](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx)。</span><span class="sxs-lookup"><span data-stu-id="f98df-118">For information about the structure of **getContentResponse**, see [Content Service documentation](http://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f98df-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="f98df-119">See Also</span></span>  
 [<span data-ttu-id="f98df-120">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="f98df-120">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="f98df-121">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="f98df-121">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="f98df-122">讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="f98df-122">Make Data Available for Binding in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)
