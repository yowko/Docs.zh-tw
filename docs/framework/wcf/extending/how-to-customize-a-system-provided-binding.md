---
title: 作法：自訂系統提供的繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 6b92382b4a37168c33f9e97077ad292d27ea5bc3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797019"
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="c5461-102">HOW TO：自訂系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="c5461-102">How to: Customize a System-Provided Binding</span></span>
<span data-ttu-id="c5461-103">Windows Communication Foundation （WCF）包含數個系統提供的系結，可讓您設定基礎繫結項目的某些屬性，但不是所有屬性。</span><span class="sxs-lookup"><span data-stu-id="c5461-103">Windows Communication Foundation (WCF) includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="c5461-104">本主題示範如何設定繫結項目上的屬性來建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="c5461-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="c5461-105">如需如何直接建立和設定繫結項目的詳細資訊，而不使用系統提供的系結，請參閱[自訂](custom-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="c5461-105">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](custom-bindings.md).</span></span>  
  
 <span data-ttu-id="c5461-106">如需建立和擴充自訂系結的詳細資訊，請參閱[擴充](extending-bindings.md)系結。</span><span class="sxs-lookup"><span data-stu-id="c5461-106">For more information about creating and extending custom bindings, see [Extending Bindings](extending-bindings.md).</span></span>  
  
 <span data-ttu-id="c5461-107">在 WCF 中，所有系結都是由*綁定*項所組成。</span><span class="sxs-lookup"><span data-stu-id="c5461-107">In WCF all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="c5461-108">每個繫結項目均衍生自 <xref:System.ServiceModel.Channels.BindingElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="c5461-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="c5461-109">諸如 <xref:System.ServiceModel.BasicHttpBinding> 的系統提供繫結，會建立並設定自有的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="c5461-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="c5461-110">本主題說明如何存取與變更這些繫結項目的屬性，而這些屬性並未直接在繫結上公開 (特別是 <xref:System.ServiceModel.BasicHttpBinding> 類別)。</span><span class="sxs-lookup"><span data-stu-id="c5461-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="c5461-111">個別的繫結項目會包含在由<xref:System.ServiceModel.Channels.BindingElementCollection>類別表示的集合中，並依此順序新增：交易流程，可靠會話，安全性，複合雙工，單向，資料流程安全性，訊息編碼和傳輸。</span><span class="sxs-lookup"><span data-stu-id="c5461-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="c5461-112">請注意，並非每個繫結都需要所列的所有繫結項目。</span><span class="sxs-lookup"><span data-stu-id="c5461-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="c5461-113">使用者定義的繫結項目也可以出現在此繫結項目集合中，而且必須依照前述順序。</span><span class="sxs-lookup"><span data-stu-id="c5461-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="c5461-114">例如，使用者定義的傳輸必須是繫結項目集合中的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="c5461-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="c5461-115"><xref:System.ServiceModel.BasicHttpBinding> 類別包含三個繫結項目：</span><span class="sxs-lookup"><span data-stu-id="c5461-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1. <span data-ttu-id="c5461-116">一種選擇性的安全性繫結項目，可以是搭配 HTTP 傳輸 (訊息層級安全性) 一起使用的 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 類別，或是當傳輸層提供安全性時所使用的 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> 類別 (這時會使用 HTTPS 傳輸)。</span><span class="sxs-lookup"><span data-stu-id="c5461-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2. <span data-ttu-id="c5461-117">必要的訊息編碼器繫結項目，可以是 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 或 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="c5461-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3. <span data-ttu-id="c5461-118">必要的傳輸繫結項目，可以是 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 或 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="c5461-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="c5461-119">在此範例中，我們會建立系結的實例、從它產生*自訂*系結、檢查自訂系結中的繫結項目，以及當我們找到 HTTP 繫結項目時`KeepAliveEnabled` ，將`false`其屬性設定為。</span><span class="sxs-lookup"><span data-stu-id="c5461-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="c5461-120">`KeepAliveEnabled` 屬性不會直接在 `BasicHttpBinding` 上公開，因此我們必須建立自訂繫結以向下巡覽至繫結項目並設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="c5461-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="c5461-121">若要修改系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="c5461-121">To modify a system-provided binding</span></span>  
  
1. <span data-ttu-id="c5461-122">建立 <xref:System.ServiceModel.BasicHttpBinding> 類別的執行個體，並將其安全性模式設為訊息層級。</span><span class="sxs-lookup"><span data-stu-id="c5461-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. <span data-ttu-id="c5461-123">從繫結中建立自訂繫結，並從其中一個自訂繫結的屬性中建立 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別。</span><span class="sxs-lookup"><span data-stu-id="c5461-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <span data-ttu-id="c5461-124">對 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別執行迴圈，並在找到 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 類別時，將其 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> 屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c5461-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c5461-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5461-125">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="c5461-126">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="c5461-126">Custom Bindings</span></span>](custom-bindings.md)
