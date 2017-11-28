---
title: "Windows Communication Foundation 繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: bindings [WCF]
ms.assetid: 845df323-be53-4848-92ef-ba67a406484d
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b458c0491ec91cd528b40fb19e93b7948f8c059a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="windows-communication-foundation-bindings"></a><span data-ttu-id="d52b0-102">Windows Communication Foundation 繫結</span><span class="sxs-lookup"><span data-stu-id="d52b0-102">Windows Communication Foundation Bindings</span></span>
<span data-ttu-id="d52b0-103">繫結會指定 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務端點與其他端點通訊的方式。</span><span class="sxs-lookup"><span data-stu-id="d52b0-103">Bindings specify how a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service endpoint communicates with other endpoints.</span></span> <span data-ttu-id="d52b0-104">繫結的最基本功能，就是必須指定要使用的傳輸 (例如，HTTP 或 TCP)。</span><span class="sxs-lookup"><span data-stu-id="d52b0-104">At its most basic, a binding must specify the transport (for example, HTTP or TCP) to use.</span></span> <span data-ttu-id="d52b0-105">此外，您也可以透過繫結來設定其他特性，例如安全性與交易支援。</span><span class="sxs-lookup"><span data-stu-id="d52b0-105">You can also set other characteristics, such as security and transaction support, through bindings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d52b0-106">本章節內容</span><span class="sxs-lookup"><span data-stu-id="d52b0-106">In This Section</span></span>  
 [<span data-ttu-id="d52b0-107">WCF 繫結概觀</span><span class="sxs-lookup"><span data-stu-id="d52b0-107">WCF Bindings Overview</span></span>](../../../docs/framework/wcf/bindings-overview.md)  
 <span data-ttu-id="d52b0-108">有關 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 繫結的用途、系統提供哪些繫結，以及如何定義或修改這些繫結的概觀。</span><span class="sxs-lookup"><span data-stu-id="d52b0-108">Overview of what [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bindings do, what bindings the system provides, and how you can define or modify them.</span></span>  
  
 [<span data-ttu-id="d52b0-109">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d52b0-109">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)  
 <span data-ttu-id="d52b0-110">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 所附繫結的清單。</span><span class="sxs-lookup"><span data-stu-id="d52b0-110">A list of bindings included with [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="d52b0-111">這些繫結程序涵蓋了大部分的安全性與訊息模式需求。</span><span class="sxs-lookup"><span data-stu-id="d52b0-111">These bindings cover the majority of security and message pattern requirements.</span></span>  
  
 [<span data-ttu-id="d52b0-112">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="d52b0-112">Using Bindings to Configure Services and Clients</span></span>](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 <span data-ttu-id="d52b0-113">[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 繫結含有用戶端連線到服務端點時必須使用的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="d52b0-113">A [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] binding contains important information that clients must use to connect to service endpoints.</span></span>  
  
 [<span data-ttu-id="d52b0-114">設定服務的繫結</span><span class="sxs-lookup"><span data-stu-id="d52b0-114">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 <span data-ttu-id="d52b0-115">組態可讓系統管理員和安裝程式自訂服務端點的繫結。</span><span class="sxs-lookup"><span data-stu-id="d52b0-115">Configuration enables administrators and installers to customize the bindings for service endpoints.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d52b0-116">參考資料</span><span class="sxs-lookup"><span data-stu-id="d52b0-116">Reference</span></span>  
 <xref:System.ServiceModel.Channels>  
  
## <a name="related-sections"></a><span data-ttu-id="d52b0-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="d52b0-117">Related Sections</span></span>  
 [<span data-ttu-id="d52b0-118">端點： 位址、 繫結和合約</span><span class="sxs-lookup"><span data-stu-id="d52b0-118">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)  
  
 [<span data-ttu-id="d52b0-119">繫結</span><span class="sxs-lookup"><span data-stu-id="d52b0-119">Bindings</span></span>](../../../docs/framework/wcf/feature-details/bindings.md)  
  
## <a name="see-also"></a><span data-ttu-id="d52b0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d52b0-120">See Also</span></span>  
 [<span data-ttu-id="d52b0-121">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="d52b0-121">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
