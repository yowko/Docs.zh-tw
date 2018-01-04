---
title: "開發通道"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 42c89ae71078a3ddfbe7e85273a6f62879781c80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="developing-channels"></a><span data-ttu-id="0c44c-102">開發通道</span><span class="sxs-lookup"><span data-stu-id="0c44c-102">Developing Channels</span></span>
<span data-ttu-id="0c44c-103">若要開發出可以搭配 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 使用的通訊協定和傳輸通道，應用程式層需要經過幾個步驟。</span><span class="sxs-lookup"><span data-stu-id="0c44c-103">To develop a protocol or transport channel that can be used with the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application layer requires several steps.</span></span> <span data-ttu-id="0c44c-104">本主題將說明這些步驟，並指引您前往特定主題以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0c44c-104">This topic describes those steps and points you to specific topics for more information.</span></span> <span data-ttu-id="0c44c-105">若要了解通道模型和本主題所述的各種類型，請參閱[通道模型概觀](../../../../docs/framework/wcf/extending/channel-model-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-105">To understand the channel model and the various types that are mentioned in this topic, see [Channel Model Overview](../../../../docs/framework/wcf/extending/channel-model-overview.md).</span></span> <span data-ttu-id="0c44c-106">如需完成的傳輸通道範例中，請參閱[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-106">For a complete transport channel sample, see [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).</span></span>  
  
## <a name="the-channel-development-task-list"></a><span data-ttu-id="0c44c-107">通道開發工作單位清單</span><span class="sxs-lookup"><span data-stu-id="0c44c-107">The Channel Development Task List</span></span>  
 <span data-ttu-id="0c44c-108">建立使用者定義通道的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="0c44c-108">The steps to create a user-defined channel are as follows.</span></span> <span data-ttu-id="0c44c-109">所有的通道都必須：</span><span class="sxs-lookup"><span data-stu-id="0c44c-109">All channels must:</span></span>  
  
1.  <span data-ttu-id="0c44c-110">決定您的 <xref:System.ServiceModel.Channels.IOutputChannel> 和 <xref:System.ServiceModel.Channels.IInputChannel> 所要支援的通道訊息交換模式 (<xref:System.ServiceModel.Channels.IDuplexChannel>、<xref:System.ServiceModel.Channels.IRequestChannel>、<xref:System.ServiceModel.Channels.IReplyChannel>、<xref:System.ServiceModel.Channels.IChannelFactory> 或 <xref:System.ServiceModel.Channels.IChannelListener>)，以及其是否支援這些介面的工作階段變化。</span><span class="sxs-lookup"><span data-stu-id="0c44c-110">Decide which of the channel Message Exchange Patterns (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, or <xref:System.ServiceModel.Channels.IReplyChannel>) your <xref:System.ServiceModel.Channels.IChannelFactory> and <xref:System.ServiceModel.Channels.IChannelListener> will support, as well as whether it will support the sessionful variations of these interfaces.</span></span> <span data-ttu-id="0c44c-111">如需詳細資訊，請參閱[選擇訊息交換模式](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-111">For details, see [Choosing a Message Exchange Pattern](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).</span></span>  
  
2.  <span data-ttu-id="0c44c-112">建立支援您訊息交換模式的通道處理站和接聽項 (<xref:System.ServiceModel.Channels.IChannelFactory> 和 <xref:System.ServiceModel.Channels.IChannelListener>)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-112">Create a channel factory and listener (<xref:System.ServiceModel.Channels.IChannelFactory> and <xref:System.ServiceModel.Channels.IChannelListener>) that support your message exchange pattern.</span></span> <span data-ttu-id="0c44c-113">如需有關開發處理站的詳細資訊，請參閱[用戶端： 通道處理站和通道](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-113">For details about developing factories, see [Client: Channel Factories and Channels](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md).</span></span> <span data-ttu-id="0c44c-114">如需有關開發接聽程式的詳細資訊，請參閱[服務： 通道接聽程式和通道](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-114">For details about developing listeners, see [Service: Channel Listeners and Channels](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).</span></span>  
  
3.  <span data-ttu-id="0c44c-115">確認是否已將任何的網路特定例外狀況標準化為 <xref:System.TimeoutException?displayProperty=nameWithType> 或適當的 <xref:System.ServiceModel.CommunicationException> 衍生類別。</span><span class="sxs-lookup"><span data-stu-id="0c44c-115">Ensure that any network-specific exceptions are normalized to either <xref:System.TimeoutException?displayProperty=nameWithType> or the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span> <span data-ttu-id="0c44c-116">如需詳細資訊，請參閱[處理的例外狀況和錯誤](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-116">For details, see [Handling Exceptions and Faults](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).</span></span>  
  
4.  <span data-ttu-id="0c44c-117">若要啟用應用程式層，請新增會將自訂通道加入到通道堆疊中的 <xref:System.ServiceModel.Channels.BindingElement>。</span><span class="sxs-lookup"><span data-stu-id="0c44c-117">To enable use from the application layer, add a <xref:System.ServiceModel.Channels.BindingElement> that adds the custom channel to a channel stack.</span></span> <span data-ttu-id="0c44c-118">如需詳細資訊，請參閱[建立 BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-118">For more information, see [Creating a BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).</span></span>  
  
 <span data-ttu-id="0c44c-119">在啟用更完整的應用程式層支援時，需要下列的額外步驟：</span><span class="sxs-lookup"><span data-stu-id="0c44c-119">The following additional steps are required to enable more complete support at the application layer:</span></span>  
  
1.  <span data-ttu-id="0c44c-120">新增繫結元素延伸區段，即可將新的繫結元素公開至組態系統。</span><span class="sxs-lookup"><span data-stu-id="0c44c-120">Add a binding element extension section to expose the new binding element to the configuration system.</span></span> <span data-ttu-id="0c44c-121">如需詳細資訊，請參閱[組態與中繼資料支援](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-121">For more information, see [Configuration and Metadata Support](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).</span></span>  
  
2.  <span data-ttu-id="0c44c-122">新增中繼資料延伸，即可將功能傳達給其他端點。</span><span class="sxs-lookup"><span data-stu-id="0c44c-122">Add metadata extensions to communicate capabilities to other endpoints.</span></span> <span data-ttu-id="0c44c-123">如需詳細資訊，請參閱[組態與中繼資料支援](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-123">For more information, see [Configuration and Metadata Support](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).</span></span>  
  
3.  <span data-ttu-id="0c44c-124">新增繫結，此繫結會根據妥善定義的設定檔來預先設定繫結項目的堆疊。</span><span class="sxs-lookup"><span data-stu-id="0c44c-124">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="0c44c-125">如需詳細資訊，請參閱[Creating User-Defined 繫結](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-125">For more information, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span></span>  
  
4.  <span data-ttu-id="0c44c-126">新增繫結區段和繫結組態項目，即可將繫結公開至組態系統。</span><span class="sxs-lookup"><span data-stu-id="0c44c-126">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="0c44c-127">如需詳細資訊，請參閱[組態與中繼資料支援](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)。</span><span class="sxs-lookup"><span data-stu-id="0c44c-127">For more information, see [Configuration and Metadata Support](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c44c-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="0c44c-128">See Also</span></span>  
 [<span data-ttu-id="0c44c-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="0c44c-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
