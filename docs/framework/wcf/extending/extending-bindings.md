---
title: "擴充繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending bindings [WCF]
ms.assetid: 5e40d306-b3c1-4429-80c4-fbb1d956856c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 692e51fc6276fbee0c1764c0040a251fe32b2c9f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="extending-bindings"></a><span data-ttu-id="55ecc-102">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="55ecc-102">Extending Bindings</span></span>
<span data-ttu-id="55ecc-103">繫結會指定連接端點所需的傳輸、編碼和通訊協定。</span><span class="sxs-lookup"><span data-stu-id="55ecc-103">Bindings specify the transport, encoding, and protocol required to connect to an endpoint.</span></span> <span data-ttu-id="55ecc-104">繫結延伸和自訂繫結會實作所需的自訂通訊功能，以支援應用程式功能。</span><span class="sxs-lookup"><span data-stu-id="55ecc-104">Binding extensions and custom bindings implement custom communication functionality required to support application features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55ecc-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="55ecc-105">In This Section</span></span>  
  
|<span data-ttu-id="55ecc-106">主題</span><span class="sxs-lookup"><span data-stu-id="55ecc-106">Topic</span></span>|<span data-ttu-id="55ecc-107">說明</span><span class="sxs-lookup"><span data-stu-id="55ecc-107">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="55ecc-108">繫結和繫結項目</span><span class="sxs-lookup"><span data-stu-id="55ecc-108">Bindings and Binding Elements</span></span>](../../../../docs/framework/wcf/extending/bindings-and-binding-elements.md)|<span data-ttu-id="55ecc-109">描述繫結、繫結項目，以及如何使用並擴充繫結。</span><span class="sxs-lookup"><span data-stu-id="55ecc-109">Describes bindings, binding elements, and how they are used and extended.</span></span>|  
|[<span data-ttu-id="55ecc-110">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="55ecc-110">Custom Bindings</span></span>](../../../../docs/framework/wcf/extending/custom-bindings.md)|<span data-ttu-id="55ecc-111">描述如何透過系統定義和協力廠商的繫結項目，使用 <xref:System.ServiceModel.Channels.CustomBinding> 類別來建立自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="55ecc-111">Describes how to use the <xref:System.ServiceModel.Channels.CustomBinding> class to create custom bindings using system-defined and third-party binding elements.</span></span>|  
|[<span data-ttu-id="55ecc-112">建立使用者定義繫結</span><span class="sxs-lookup"><span data-stu-id="55ecc-112">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)|<span data-ttu-id="55ecc-113">描述如何建立其他人可以使用的繫結和繫結項目。</span><span class="sxs-lookup"><span data-stu-id="55ecc-113">Describes how to create bindings and binding elements that can be used by others.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="55ecc-114">參考資料</span><span class="sxs-lookup"><span data-stu-id="55ecc-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="55ecc-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="55ecc-115">Related Sections</span></span>  
 [<span data-ttu-id="55ecc-116">建立 BindingElement</span><span class="sxs-lookup"><span data-stu-id="55ecc-116">Creating a BindingElement</span></span>](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md)  
  
 [<span data-ttu-id="55ecc-117">設定和中繼資料支援</span><span class="sxs-lookup"><span data-stu-id="55ecc-117">Configuration and Metadata Support</span></span>](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md)
