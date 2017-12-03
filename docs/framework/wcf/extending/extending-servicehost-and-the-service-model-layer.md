---
title: "擴充 ServiceHost 與服務模型層"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending service models [WCF]
ms.assetid: 954c138a-1cd0-45a0-8abe-e4d2b8ff5400
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67ed4be3211af141af87da2406e81ff5e2fbb767
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="extending-servicehost-and-the-service-model-layer"></a><span data-ttu-id="2c96e-102">擴充 ServiceHost 與服務模型層</span><span class="sxs-lookup"><span data-stu-id="2c96e-102">Extending ServiceHost and the Service Model Layer</span></span>
<span data-ttu-id="2c96e-103">服務模型層負責從基礎通道提取傳入訊息，將它們以應用程式碼轉譯成方法叫用，然後將結果傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="2c96e-103">The service model layer is responsible for pulling incoming messages out of the underlying channels, translating them into method invocations in application code, and sending the results back to the caller.</span></span> <span data-ttu-id="2c96e-104">服務模型延伸會修改或實作涉及用戶端或發送器功能、自訂行為、訊息與參數攔截以及其他擴充性功能的執行或通訊行為與功能。</span><span class="sxs-lookup"><span data-stu-id="2c96e-104">Service model extensions modify or implement execution or communication behavior and features involving client or dispatcher functionality, custom behaviors, message and parameter interception, and other extensibility functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2c96e-105">本章節內容</span><span class="sxs-lookup"><span data-stu-id="2c96e-105">In This Section</span></span>  
 [<span data-ttu-id="2c96e-106">擴充用戶端</span><span class="sxs-lookup"><span data-stu-id="2c96e-106">Extending Clients</span></span>](../../../../docs/framework/wcf/extending/extending-clients.md)  
 <span data-ttu-id="2c96e-107">說明可攔截與修改用戶端執行階段的介面，以及您可在用戶端應用程式中插入自訂擴充功能的類別。</span><span class="sxs-lookup"><span data-stu-id="2c96e-107">Describes the interfaces that can intercept and modify the client runtime, as well as the classes into which you can insert your custom extensions in client applications.</span></span> <span data-ttu-id="2c96e-108">例如，您可以執行自訂用戶端訊息記錄，以及執行自訂訊息序列化等等。</span><span class="sxs-lookup"><span data-stu-id="2c96e-108">For example, you can perform custom client message logging, perform custom message serialization, and so on.</span></span>  
  
 [<span data-ttu-id="2c96e-109">擴充發送器</span><span class="sxs-lookup"><span data-stu-id="2c96e-109">Extending Dispatchers</span></span>](../../../../docs/framework/wcf/extending/extending-dispatchers.md)  
 <span data-ttu-id="2c96e-110">說明可攔截與修改服務執行階段的介面，以及您可在服務應用程式中插入自訂擴充功能的類別。</span><span class="sxs-lookup"><span data-stu-id="2c96e-110">Describes the interfaces that can intercept and modify the service runtime, as well as the classes into which you can insert your custom extensions in service applications.</span></span> <span data-ttu-id="2c96e-111">例如，您可執行自訂服務記錄、服務端訊息驗證，以及自訂分派等等。</span><span class="sxs-lookup"><span data-stu-id="2c96e-111">For example, you can perform custom service logging, service-side message validation, custom dispatching, and so on.</span></span>  
  
 [<span data-ttu-id="2c96e-112">延伸的物件</span><span class="sxs-lookup"><span data-stu-id="2c96e-112">Extensible Objects</span></span>](../../../../docs/framework/wcf/extending/extensible-objects.md)  
 <span data-ttu-id="2c96e-113">描述 5 項可擴充物件以及 <xref:System.ServiceModel.IExtensibleObject%601> 模式。</span><span class="sxs-lookup"><span data-stu-id="2c96e-113">Describes the five extensible objects and the <xref:System.ServiceModel.IExtensibleObject%601> pattern.</span></span> <span data-ttu-id="2c96e-114">可延伸物件模式是用於以新功能延伸現有的執行階段類別，或將新狀態新增至物件。</span><span class="sxs-lookup"><span data-stu-id="2c96e-114">The extensible object pattern is used to either extend existing runtime classes with new functionality or to add new state to an object.</span></span> <span data-ttu-id="2c96e-115">附加至其中一個可擴充物件的擴充功能會在處理程序中的各種不同階段啟用行為，以存取附加至它們可存取之一般可擴充物件的共用狀態與功能。</span><span class="sxs-lookup"><span data-stu-id="2c96e-115">Extensions, attached to one of the extensible objects, enable behaviors at very different stages in processing to access shared state and functionality attached to a common extensible object that they can access.</span></span>  
  
 [<span data-ttu-id="2c96e-116">設定與擴充執行階段行為</span><span class="sxs-lookup"><span data-stu-id="2c96e-116">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)  
 <span data-ttu-id="2c96e-117">若要變更在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 執行階段的設定值或插入擴充功能，請使用 [行為]。</span><span class="sxs-lookup"><span data-stu-id="2c96e-117">To change settings on or insert extensions in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime, you use Behaviors.</span></span> <span data-ttu-id="2c96e-118">WCF 包括控制節流、執行個體以及其他許多服務與作業方面的系統實作行為。</span><span class="sxs-lookup"><span data-stu-id="2c96e-118">WCF includes system-implemented behaviors for controlling throttling, instancing, and many other aspects of services and operations.</span></span> <span data-ttu-id="2c96e-119">此章節說明如何建立您自己的自訂行為，以及如何讓它們供程式設計以及使用組態檔時使用。</span><span class="sxs-lookup"><span data-stu-id="2c96e-119">This section describes how to create your own custom behaviors and how to make them available for use both programmatically and using configuration files.</span></span>  
  
 [<span data-ttu-id="2c96e-120">使用 ServiceHostFactory 擴充裝載</span><span class="sxs-lookup"><span data-stu-id="2c96e-120">Extending Hosting Using ServiceHostFactory</span></span>](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 <span data-ttu-id="2c96e-121">說明如何擴充 <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>，以及使用 <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> 類別自訂主機環境。</span><span class="sxs-lookup"><span data-stu-id="2c96e-121">Describes how to extend <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>, <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, and use the <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType> classes to customize the host environment.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="2c96e-122">參考資料</span><span class="sxs-lookup"><span data-stu-id="2c96e-122">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2c96e-123">相關章節</span><span class="sxs-lookup"><span data-stu-id="2c96e-123">Related Sections</span></span>
