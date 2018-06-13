---
title: '&lt;繫結&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: d72b3a34e0696df944b2338c89f167c8bfa06400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392248"
---
# <a name="ltbindinggt"></a><span data-ttu-id="8ddab-102">&lt;繫結&gt;</span><span class="sxs-lookup"><span data-stu-id="8ddab-102">&lt;binding&gt;</span></span>
<span data-ttu-id="8ddab-103">您可以使用 `binding` 項目來設定 Windows Communication Foundation (WCF) 所提供的各種預先定義繫結。</span><span class="sxs-lookup"><span data-stu-id="8ddab-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="8ddab-104">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8ddab-104">System-Provided Binding</span></span>  
 <span data-ttu-id="8ddab-105">系統提供的繫結會隱藏 WCF 訊息堆疊的複雜性。</span><span class="sxs-lookup"><span data-stu-id="8ddab-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="8ddab-106">使用系統提供之繫結的應用程式不需要對堆疊有完整控制權。</span><span class="sxs-lookup"><span data-stu-id="8ddab-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="8ddab-107">在每個系統提供之繫結上公開的屬性，最適合繫結所處理的使用案例。</span><span class="sxs-lookup"><span data-stu-id="8ddab-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="8ddab-108">每個系統提供之繫結的組態區段可定義用於設定繫結的多個組態。</span><span class="sxs-lookup"><span data-stu-id="8ddab-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="8ddab-109">每個組態是由唯一的名稱來識別。</span><span class="sxs-lookup"><span data-stu-id="8ddab-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="8ddab-110">您無法在系統提供的繫結中加入項目或屬性。</span><span class="sxs-lookup"><span data-stu-id="8ddab-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="8ddab-111">若要這麼做，您應實作自訂繫結，如本主題的「自訂繫結」一節所述。</span><span class="sxs-lookup"><span data-stu-id="8ddab-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="8ddab-112">您可以定義完全仿照系統提供之繫結的自訂繫結，並在其中加入一些使用者應用程式要有控制權的設定。</span><span class="sxs-lookup"><span data-stu-id="8ddab-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="8ddab-113">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="8ddab-113">Custom Binding</span></span>  
 <span data-ttu-id="8ddab-114">自訂繫結會提供對於 WCF 訊息堆疊的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="8ddab-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="8ddab-115">個別繫結定義訊息堆疊的方式，是依據堆疊項目在堆疊中的出現順序來指定其組態項目。</span><span class="sxs-lookup"><span data-stu-id="8ddab-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="8ddab-116">每個項目都會定義及設定堆疊的一個項目。</span><span class="sxs-lookup"><span data-stu-id="8ddab-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="8ddab-117">各個自訂繫結中一定要出現一個而且是唯一一個 `transport` 項目。</span><span class="sxs-lookup"><span data-stu-id="8ddab-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="8ddab-118">如果沒有這個項目，訊息堆疊就不完整。</span><span class="sxs-lookup"><span data-stu-id="8ddab-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="8ddab-119">項目在堆疊中的出現順序很重要，因為這是作業套用至訊息的順序。</span><span class="sxs-lookup"><span data-stu-id="8ddab-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="8ddab-120">建議的堆疊項目順序如下所示：</span><span class="sxs-lookup"><span data-stu-id="8ddab-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="8ddab-121">交易 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8ddab-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="8ddab-122">可信賴傳訊 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8ddab-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="8ddab-123">安全性 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="8ddab-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="8ddab-124">編碼器</span><span class="sxs-lookup"><span data-stu-id="8ddab-124">Encoder</span></span>  
  
5.  <span data-ttu-id="8ddab-125">Transport</span><span class="sxs-lookup"><span data-stu-id="8ddab-125">Transport</span></span>  
  
 <span data-ttu-id="8ddab-126">自訂繫結是由其 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="8ddab-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ddab-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ddab-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="8ddab-128">繫結</span><span class="sxs-lookup"><span data-stu-id="8ddab-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8ddab-129">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="8ddab-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="8ddab-130">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8ddab-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
