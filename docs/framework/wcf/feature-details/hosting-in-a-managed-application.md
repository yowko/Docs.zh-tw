---
title: 在 Managed 應用程式中裝載
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 1895f6622f7c528979badd741f5994970bbd1a8c
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169799"
---
# <a name="hosting-in-a-managed-application"></a><span data-ttu-id="3a13d-102">在 Managed 應用程式中裝載</span><span class="sxs-lookup"><span data-stu-id="3a13d-102">Hosting in a Managed Application</span></span>
<span data-ttu-id="3a13d-103">Windows Communication Foundation (WCF) 服務可以裝載於任何.NET Framework 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3a13d-103">Windows Communication Foundation (WCF) services can be hosted in any .NET Framework application.</span></span> <span data-ttu-id="3a13d-104">自我裝載服務是最彈性的裝載選項，因為它只需要最基本的基礎結構就可部署。</span><span class="sxs-lookup"><span data-stu-id="3a13d-104">Self-hosting services is the most flexible hosting option because it requires the least infrastructure to deploy.</span></span> <span data-ttu-id="3a13d-105">不過，也很最不穩固的裝載選項，因為受管理的應用程式不會提供的進階裝載和其他裝載選項在 WCF 中，例如 Internet Information Services (IIS) 和 Windows 服務的管理功能。</span><span class="sxs-lookup"><span data-stu-id="3a13d-105">However, it is also the least robust hosting option, because managed applications do not provide the advanced hosting and management features of other hosting options in WCF, such as Internet Information Services (IIS) and Windows services.</span></span>  
  
 <span data-ttu-id="3a13d-106">若要建立自我裝載服務，請建立並開啟 <xref:System.ServiceModel.ServiceHost>的執行個體，以便啟動服務來接聽訊息。</span><span class="sxs-lookup"><span data-stu-id="3a13d-106">To create a self-hosted service, create and open an instance of the <xref:System.ServiceModel.ServiceHost>, which starts a service listening for messages.</span></span> <span data-ttu-id="3a13d-107">如需詳細資訊，請參閱[如何：裝載 WCF 服務的受管理的應用程式中](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)。</span><span class="sxs-lookup"><span data-stu-id="3a13d-107">For more information, see [How to: Host a WCF Service in a Managed Application](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md).</span></span>  
  
 <span data-ttu-id="3a13d-108">如需如何定義合約、 實作合約，並裝載在受管理的應用程式服務的完整範例，請參閱[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)並[自我裝載](../../../../docs/framework/wcf/samples/self-host.md)。</span><span class="sxs-lookup"><span data-stu-id="3a13d-108">For a complete example on how to define a contract, implement the contract, and host a service inside of a managed application see the [Getting Started Tutorial](../../../../docs/framework/wcf/getting-started-tutorial.md) and the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md).</span></span>  
  
 <span data-ttu-id="3a13d-109">下列各節說明使用此裝載選項的常見案例。</span><span class="sxs-lookup"><span data-stu-id="3a13d-109">The following sections describe common scenarios that use this hosting option.</span></span>  
  
## <a name="console-applications"></a><span data-ttu-id="3a13d-110">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="3a13d-110">Console Applications</span></span>  
 <span data-ttu-id="3a13d-111">自我裝載可讓的常見案例是執行主控台應用程式內的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="3a13d-111">Common scenarios that self-hosting enables are WCF services running inside console applications.</span></span> <span data-ttu-id="3a13d-112">裝載於主控台應用程式的 WCF 服務一般來說是很有用的服務在開發階段。</span><span class="sxs-lookup"><span data-stu-id="3a13d-112">Hosting a WCF service inside a console application is typically useful during the development phase of the service.</span></span> <span data-ttu-id="3a13d-113">這樣一來，您可以很容易地進行偵錯、取得追蹤資訊以便了解應用程式裡面所發生的事，以及藉由將它們複製到新的位置輕易地加以移動。</span><span class="sxs-lookup"><span data-stu-id="3a13d-113">This makes them easy to debug, easy to get trace information from to find out what is happening inside of the application, and easy to move around by copying them to new locations.</span></span>  
  
## <a name="rich-client-applications"></a><span data-ttu-id="3a13d-114">豐富型用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="3a13d-114">Rich Client Applications</span></span>  
 <span data-ttu-id="3a13d-115">自我裝載可讓其他常見案例是豐富型用戶端應用程式，例如 Windows Presentation Foundation (WPF) 或 Windows Forms (WinForms) 為基礎。</span><span class="sxs-lookup"><span data-stu-id="3a13d-115">Other common scenarios that self-hosting enables are rich client applications, such as those based on Windows Presentation Foundation (WPF) or Windows Forms (WinForms).</span></span> <span data-ttu-id="3a13d-116">這個裝載選項也方便對於豐富型用戶端應用程式，例如 WPF 和 WinForms 應用程式，來與外界通訊。</span><span class="sxs-lookup"><span data-stu-id="3a13d-116">This hosting option also makes it easy for rich client applications, such as WPF and WinForms applications, to communicate with the outside world.</span></span> <span data-ttu-id="3a13d-117">例如，對等共同作業用戶端使用者介面中使用 WPF，也會裝載 WCF 服務，可讓其他用戶端連線，並共用資訊。</span><span class="sxs-lookup"><span data-stu-id="3a13d-117">For example, a peer-to-peer collaboration client that uses WPF for its user interface and also hosts a WCF service that allows other clients to connect to it and share information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a13d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a13d-118">See also</span></span>

- [<span data-ttu-id="3a13d-119">裝載服務</span><span class="sxs-lookup"><span data-stu-id="3a13d-119">Hosting Services</span></span>](../../../../docs/framework/wcf/hosting-services.md)
- [<span data-ttu-id="3a13d-120">快速入門教學課程</span><span class="sxs-lookup"><span data-stu-id="3a13d-120">Getting Started Tutorial</span></span>](../../../../docs/framework/wcf/getting-started-tutorial.md)
