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
ms.openlocfilehash: d752f4815de16daa466302881116e80aceec6edf
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040912"
---
# <a name="how-to-bind-to-a-web-service"></a><span data-ttu-id="7aae2-102">如何：繫結至 Web 服務</span><span class="sxs-lookup"><span data-stu-id="7aae2-102">How to: Bind to a Web Service</span></span>
<span data-ttu-id="7aae2-103">這個範例示範如何系結至 Web 服務方法呼叫所傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="7aae2-103">This example shows how to bind to objects returned by Web service method calls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7aae2-104">範例</span><span class="sxs-lookup"><span data-stu-id="7aae2-104">Example</span></span>  
 <span data-ttu-id="7aae2-105">這個範例會使用[MSDN/TechNet 發行系統（MTPS）內容服務](https://go.microsoft.com/fwlink/?LinkId=95677)來抓取指定檔所支援的語言清單。</span><span class="sxs-lookup"><span data-stu-id="7aae2-105">This example uses the [MSDN/TechNet Publishing System (MTPS) Content Service](https://go.microsoft.com/fwlink/?LinkId=95677) to retrieve the list of languages supported by a specified document.</span></span>  
  
 <span data-ttu-id="7aae2-106">在您呼叫 Web 服務之前，您必須先建立對它的參考。</span><span class="sxs-lookup"><span data-stu-id="7aae2-106">Before you call a Web service, you need to create a reference to it.</span></span> <span data-ttu-id="7aae2-107">若要使用 Visual Studio 建立 MTPS 服務的 Web 參考，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7aae2-107">To create a Web reference to the MTPS service using Visual Studio, follow the following steps:</span></span>  
  
1. <span data-ttu-id="7aae2-108">在 Visual Studio 中開啟專案。</span><span class="sxs-lookup"><span data-stu-id="7aae2-108">Open your project in Visual Studio.</span></span>  
  
2. <span data-ttu-id="7aae2-109">從 [**專案**] 功能表中，按一下 [**加入 Web 參考**]。</span><span class="sxs-lookup"><span data-stu-id="7aae2-109">From the **Project** menu, click **Add Web Reference**.</span></span>  
  
3. <span data-ttu-id="7aae2-110">在對話方塊中，將**URL**設定為[http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl)。</span><span class="sxs-lookup"><span data-stu-id="7aae2-110">In the dialog box, set the **URL** to [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).</span></span>  
  
4. <span data-ttu-id="7aae2-111">按 [**移至**]，然後按一下 [**新增參考**]。</span><span class="sxs-lookup"><span data-stu-id="7aae2-111">Press **Go** and then **Add Reference**.</span></span>  
  
 <span data-ttu-id="7aae2-112">接下來，您可以呼叫 Web 服務方法，並將適當控制項或視窗的 <xref:System.Windows.FrameworkElement.DataContext%2A> 設定為傳回的物件。</span><span class="sxs-lookup"><span data-stu-id="7aae2-112">Next, you call the Web service method and set the <xref:System.Windows.FrameworkElement.DataContext%2A> of the appropriate control or window to the returned object.</span></span> <span data-ttu-id="7aae2-113">MTPS 服務的 `GetContent` 方法會接受 `getContentRequest` 物件的參考。</span><span class="sxs-lookup"><span data-stu-id="7aae2-113">The `GetContent` method of the MTPS service takes a reference to the `getContentRequest` object.</span></span> <span data-ttu-id="7aae2-114">因此，下列範例會先設定 request 物件：</span><span class="sxs-lookup"><span data-stu-id="7aae2-114">Therefore, the following example first sets up a request object:</span></span>  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 <span data-ttu-id="7aae2-115">設定 <xref:System.Windows.FrameworkElement.DataContext%2A> 之後，您可以建立已設定 <xref:System.Windows.FrameworkElement.DataContext%2A> 之物件屬性的系結。</span><span class="sxs-lookup"><span data-stu-id="7aae2-115">After the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set, you can create bindings to the properties of the object that the <xref:System.Windows.FrameworkElement.DataContext%2A> has been set to.</span></span> <span data-ttu-id="7aae2-116">在此範例中，<xref:System.Windows.FrameworkElement.DataContext%2A> 設定為 `GetContent` 方法所傳回的 `getContentResponse` 物件。</span><span class="sxs-lookup"><span data-stu-id="7aae2-116">In this example, the <xref:System.Windows.FrameworkElement.DataContext%2A> is set to the `getContentResponse` object returned by the `GetContent` method.</span></span> <span data-ttu-id="7aae2-117">在下列範例中，<xref:System.Windows.Controls.ItemsControl> 系結至，並顯示 `getContentResponse``availableVersionsAndLocales` 的 `locale` 值。</span><span class="sxs-lookup"><span data-stu-id="7aae2-117">In the following example, the <xref:System.Windows.Controls.ItemsControl> binds to and displays the `locale` values of `availableVersionsAndLocales` of `getContentResponse`.</span></span>  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 <span data-ttu-id="7aae2-118">如需 `getContentResponse`結構的詳細資訊，請參閱[內容服務檔](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx)。</span><span class="sxs-lookup"><span data-stu-id="7aae2-118">For information about the structure of `getContentResponse`, see [Content Service documentation](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7aae2-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="7aae2-119">See also</span></span>

- [<span data-ttu-id="7aae2-120">資料繫結概觀</span><span class="sxs-lookup"><span data-stu-id="7aae2-120">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="7aae2-121">繫結來源概觀</span><span class="sxs-lookup"><span data-stu-id="7aae2-121">Binding Sources Overview</span></span>](binding-sources-overview.md)
- [<span data-ttu-id="7aae2-122">讓資料可於 XAML 中繫結</span><span class="sxs-lookup"><span data-stu-id="7aae2-122">Make Data Available for Binding in XAML</span></span>](how-to-make-data-available-for-binding-in-xaml.md)
