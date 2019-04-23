---
title: HOW TO：自訂系統提供的繫結
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
ms.openlocfilehash: 0c5474a65bee7d3d290372e79f8423ea9986235f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301174"
---
# <a name="how-to-customize-a-system-provided-binding"></a><span data-ttu-id="7e67b-102">HOW TO：自訂系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="7e67b-102">How to: Customize a System-Provided Binding</span></span>
<span data-ttu-id="7e67b-103">Windows Communication Foundation (WCF) 包含數個系統提供繫結可讓您設定部分屬性，基礎的繫結項目，而非全部的屬性。</span><span class="sxs-lookup"><span data-stu-id="7e67b-103">Windows Communication Foundation (WCF) includes several system-provided bindings that allow you to configure some of the properties of the underlying binding elements, but not all of the properties.</span></span> <span data-ttu-id="7e67b-104">本主題示範如何設定繫結項目上的屬性來建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="7e67b-104">This topic demonstrates how to set properties on the binding elements to create a custom binding.</span></span>  
  
 <span data-ttu-id="7e67b-105">如需如何直接建立並設定繫結項目，而不使用系統提供繫結的詳細資訊，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="7e67b-105">For more information about how to directly create and configure binding elements without using the system-provided bindings, see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
 <span data-ttu-id="7e67b-106">如需有關建立和擴充自訂繫結的詳細資訊，請參閱 <<c0> [ 擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="7e67b-106">For more information about creating and extending custom bindings, see [Extending Bindings](../../../../docs/framework/wcf/extending/extending-bindings.md).</span></span>  
  
 <span data-ttu-id="7e67b-107">在 WCF 中的所有繫結組成*繫結項目*。</span><span class="sxs-lookup"><span data-stu-id="7e67b-107">In WCF all bindings are made up of *binding elements*.</span></span> <span data-ttu-id="7e67b-108">每個繫結項目均衍生自 <xref:System.ServiceModel.Channels.BindingElement> 類別。</span><span class="sxs-lookup"><span data-stu-id="7e67b-108">Each binding element derives from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="7e67b-109">諸如 <xref:System.ServiceModel.BasicHttpBinding> 的系統提供繫結，會建立並設定自有的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="7e67b-109">System-provided bindings such as <xref:System.ServiceModel.BasicHttpBinding> create and configure their own binding elements.</span></span> <span data-ttu-id="7e67b-110">本主題說明如何存取與變更這些繫結項目的屬性，而這些屬性並未直接在繫結上公開 (特別是 <xref:System.ServiceModel.BasicHttpBinding> 類別)。</span><span class="sxs-lookup"><span data-stu-id="7e67b-110">This topic shows you how to access and change the properties of these binding elements, which are not directly exposed on the binding; specifically, the <xref:System.ServiceModel.BasicHttpBinding> class.</span></span>  
  
 <span data-ttu-id="7e67b-111">表示集合中所包含的個別的繫結項目<xref:System.ServiceModel.Channels.BindingElementCollection>類別，並依此順序加入：交易流程、 可靠工作階段、 安全性、 複合雙工、 單向、 Stream Security、 訊息編碼，和傳輸。</span><span class="sxs-lookup"><span data-stu-id="7e67b-111">The individual binding elements are contained in a collection represented by the <xref:System.ServiceModel.Channels.BindingElementCollection> class and are added in this order: Transaction Flow, Reliable Session, Security, Composite Duplex, One-way, Stream Security, Message Encoding, and Transport.</span></span> <span data-ttu-id="7e67b-112">請注意，並非每個繫結都需要所列的所有繫結項目。</span><span class="sxs-lookup"><span data-stu-id="7e67b-112">Note that not all the binding elements listed are required in every binding.</span></span> <span data-ttu-id="7e67b-113">使用者定義的繫結項目也可以出現在此繫結項目集合中，而且必須依照前述順序。</span><span class="sxs-lookup"><span data-stu-id="7e67b-113">User-defined binding elements can also appear in this binding element collection and must appear in the same order as previously described.</span></span> <span data-ttu-id="7e67b-114">例如，使用者定義的傳輸必須是繫結項目集合中的最後一個項目。</span><span class="sxs-lookup"><span data-stu-id="7e67b-114">For example, a user-defined transport must be the last element of the binding element collection.</span></span>  
  
 <span data-ttu-id="7e67b-115"><xref:System.ServiceModel.BasicHttpBinding> 類別包含三個繫結項目：</span><span class="sxs-lookup"><span data-stu-id="7e67b-115">The <xref:System.ServiceModel.BasicHttpBinding> class contains three binding elements:</span></span>  
  
1. <span data-ttu-id="7e67b-116">一種選擇性的安全性繫結項目，可以是搭配 HTTP 傳輸 (訊息層級安全性) 一起使用的 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 類別，或是當傳輸層提供安全性時所使用的 <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> 類別 (這時會使用 HTTPS 傳輸)。</span><span class="sxs-lookup"><span data-stu-id="7e67b-116">An optional security binding element, either the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> class used with the HTTP transport (message level security) or the <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> class, which is used when the transport layer provides security, in which case the HTTPS transport is used.</span></span>  
  
2. <span data-ttu-id="7e67b-117">必要的訊息編碼器繫結項目，可以是 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> 或 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="7e67b-117">A required message encoder binding element, either <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> or <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.</span></span>  
  
3. <span data-ttu-id="7e67b-118">必要的傳輸繫結項目，可以是 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 或 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="7e67b-118">A required transport binding element, either <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, or <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.</span></span>  
  
 <span data-ttu-id="7e67b-119">在此範例中我們建立的繫結執行個體，產生*自訂繫結*，檢查 在自訂繫結、 繫結項目，並找到 HTTP 繫結項目，我們將其`KeepAliveEnabled`屬性`false`.</span><span class="sxs-lookup"><span data-stu-id="7e67b-119">In this example we create an instance of the binding, generate a *custom binding* from it, examine the binding elements in the custom binding, and when we find the HTTP binding element, we set its `KeepAliveEnabled` property to `false`.</span></span> <span data-ttu-id="7e67b-120">`KeepAliveEnabled` 屬性不會直接在 `BasicHttpBinding` 上公開，因此我們必須建立自訂繫結以向下巡覽至繫結項目並設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="7e67b-120">The `KeepAliveEnabled` property is not exposed directly on the `BasicHttpBinding`, so we must create a custom binding to navigate down to the binding element and set this property.</span></span>  
  
### <a name="to-modify-a-system-provided-binding"></a><span data-ttu-id="7e67b-121">若要修改系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="7e67b-121">To modify a system-provided binding</span></span>  
  
1. <span data-ttu-id="7e67b-122">建立 <xref:System.ServiceModel.BasicHttpBinding> 類別的執行個體，並將其安全性模式設為訊息層級。</span><span class="sxs-lookup"><span data-stu-id="7e67b-122">Create an instance of the <xref:System.ServiceModel.BasicHttpBinding> class and set its security mode to message-level.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2. <span data-ttu-id="7e67b-123">從繫結中建立自訂繫結，並從其中一個自訂繫結的屬性中建立 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別。</span><span class="sxs-lookup"><span data-stu-id="7e67b-123">Create a custom binding from the binding and create a <xref:System.ServiceModel.Channels.BindingElementCollection> class from one of the custom binding's properties.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3. <span data-ttu-id="7e67b-124">對 <xref:System.ServiceModel.Channels.BindingElementCollection> 類別執行迴圈，並在找到 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 類別時，將其 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> 屬性設為 `false`。</span><span class="sxs-lookup"><span data-stu-id="7e67b-124">Loop through the <xref:System.ServiceModel.Channels.BindingElementCollection> class, and when you find the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> class, set its <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property to `false`.</span></span>  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7e67b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e67b-125">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7e67b-126">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="7e67b-126">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)
