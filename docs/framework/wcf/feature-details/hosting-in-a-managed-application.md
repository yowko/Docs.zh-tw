---
title: 在 Managed 應用程式中裝載
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e2afa9e868c1f561aed699a2bdf7d09c17898b3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="hosting-in-a-managed-application"></a><span data-ttu-id="771c0-102">在 Managed 應用程式中裝載</span><span class="sxs-lookup"><span data-stu-id="771c0-102">Hosting in a Managed Application</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="771c0-103"> 服務可以裝載於任何 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 應用程式中。</span><span class="sxs-lookup"><span data-stu-id="771c0-103"> services can be hosted in any [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application.</span></span> <span data-ttu-id="771c0-104">自我裝載服務是最彈性的裝載選項，因為它只需要最基本的基礎結構就可部署。</span><span class="sxs-lookup"><span data-stu-id="771c0-104">Self-hosting services is the most flexible hosting option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="771c0-105">但是，它同時也是最不穩固的裝載選項，因為 Managed 應用程式無法在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中提供其他裝載選項的進階裝載與管理功能，例如網際網路資訊服務 (IIS) 和 Windows 服務。</span><span class="sxs-lookup"><span data-stu-id="771c0-105">However, it is also the least robust hosting option, because managed applications do not provide the advanced hosting and management features of other hosting options in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], such as Internet Information Services (IIS) and Windows services.</span></span>  
  
 <span data-ttu-id="771c0-106">若要建立自我裝載服務，請建立並開啟 <xref:System.ServiceModel.ServiceHost>的執行個體，以便啟動服務來接聽訊息。</span><span class="sxs-lookup"><span data-stu-id="771c0-106">To create a self-hosted service, create and open an instance of the <xref:System.ServiceModel.ServiceHost>, which starts a service listening for messages.</span></span> <span data-ttu-id="771c0-107">如需詳細資訊，請參閱[How to： 裝載中受管理的應用程式的 WCF 服務](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)。</span><span class="sxs-lookup"><span data-stu-id="771c0-107">For more information, see [How to: Host a WCF Service in a Managed Application](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="771c0-108">如需如何定義合約、 實作合約，以及裝載內部的受管理的應用程式服務的完整範例，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)和[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)。</span><span class="sxs-lookup"><span data-stu-id="771c0-108">For a complete example on how to define a contract, implement the contract, and host a service inside of a managed application see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) and the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md).</span></span>  
  
 <span data-ttu-id="771c0-109">下列各節說明使用此裝載選項的常見案例。</span><span class="sxs-lookup"><span data-stu-id="771c0-109">The following sections describe common scenarios that use this hosting option.</span></span>  
  
## <a name="console-applications"></a><span data-ttu-id="771c0-110">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="771c0-110">Console Applications</span></span>  
 <span data-ttu-id="771c0-111">自我裝載所啟用的常見案例為在主控台應用程式中執行的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="771c0-111">Common scenarios that self-hosting enables are [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running inside console applications.</span></span> <span data-ttu-id="771c0-112">在服務的開發階段，於主控台應用程式中裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務一般來說是很有用的方式。</span><span class="sxs-lookup"><span data-stu-id="771c0-112">Hosting a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service inside a console application is typically useful during the development phase of the service.</span></span> <span data-ttu-id="771c0-113">這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。</span><span class="sxs-lookup"><span data-stu-id="771c0-113">This makes them easy to debug, easy to get trace information from to find out what is happening inside of the application, and easy to move around by copying them to new locations.</span></span>  
  
## <a name="rich-client-applications"></a><span data-ttu-id="771c0-114">豐富型用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="771c0-114">Rich Client Applications</span></span>  
 <span data-ttu-id="771c0-115">其他自我裝載啟用的常見案例是豐富型用戶端應用程式，例如 Windows Presentation Foundation (WPF) 或 Windows Forms (WinForms) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="771c0-115">Other common scenarios that self-hosting enables are rich client applications, such as those based on Windows Presentation Foundation (WPF) or Windows Forms (WinForms).</span></span> <span data-ttu-id="771c0-116">這個裝載選項同時可讓豐富型用戶端應用程式 (例如， [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 和 WinForms 應用程式) 更容易與外界通訊。</span><span class="sxs-lookup"><span data-stu-id="771c0-116">This hosting option also makes it easy for rich client applications, such as [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] and WinForms applications, to communicate with the outside world.</span></span> <span data-ttu-id="771c0-117">例如，使用 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 做為使用者介面，並同時裝載 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務以允許其他用戶端與其連線並共用資訊的對等共同作業用戶端。</span><span class="sxs-lookup"><span data-stu-id="771c0-117">For example, a peer-to-peer collaboration client that uses [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] for its user interface and also hosts a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that allows other clients to connect to it and share information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="771c0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="771c0-118">See Also</span></span>  
 [<span data-ttu-id="771c0-119">裝載服務</span><span class="sxs-lookup"><span data-stu-id="771c0-119">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)  
 [<span data-ttu-id="771c0-120">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="771c0-120">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
