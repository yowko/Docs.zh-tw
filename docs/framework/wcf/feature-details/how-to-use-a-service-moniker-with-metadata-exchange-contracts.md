---
title: "HOW TO：使用服務 Moniker 搭配中繼資料交換合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d2b5b6d4a671a3eb281f49dd60fd3c00ee76f8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="dcf76-102">HOW TO：使用服務 Moniker 搭配中繼資料交換合約</span><span class="sxs-lookup"><span data-stu-id="dcf76-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="dcf76-103">在開發一些新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之後，您可能會決定想要能夠從指令檔或 Visual Basic 6.0 應用程式來呼叫這些服務。</span><span class="sxs-lookup"><span data-stu-id="dcf76-103">After developing some new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="dcf76-104">有一種方法會產生 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件，請向 COM 註冊組件，在 GAC 中安裝組件，然後從您的 Visual Basic 程式碼參照 COM 型別。</span><span class="sxs-lookup"><span data-stu-id="dcf76-104">One method would be to generate a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="dcf76-105">當您散發應用程式時，也必須散發 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件。</span><span class="sxs-lookup"><span data-stu-id="dcf76-105">When you distribute the application, you will have to distribute the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Client assembly as well.</span></span> <span data-ttu-id="dcf76-106">然後使用者必須向 COM 註冊 WCF 用戶端組件，並將它放在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="dcf76-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="dcf76-107"> COM Interop 也讓您不需依賴 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件，就可以進行相同的服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="dcf76-107"> COM Interop also allows you to make the same service calls without relying on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly.</span></span> <span data-ttu-id="dcf76-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker 可讓您藉由指定服務 Moniker 用於擷取有關服務之型別資訊的中繼資料交換 (Mex) 端點 URI，從與 COM 相容的語言 (Visual Basic、VBScript、Visual Basic for Applications (VBA) 等等) 呼叫任何 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="dcf76-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker allows you to call any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="dcf76-109">本主題將說明如何使用指定 Mex 端點的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Moniker 來呼叫「使用者入門」[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="dcf76-109">This topic describes how to call the Getting Started [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcf76-110">由 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端組件定義的型別實際上永遠不會產生。</span><span class="sxs-lookup"><span data-stu-id="dcf76-110">The types defined by the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client assembly are never actually instantiated.</span></span> <span data-ttu-id="dcf76-111">此組件僅用於中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dcf76-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="dcf76-112">使用含有 Mex 位址的服務 Moniker</span><span class="sxs-lookup"><span data-stu-id="dcf76-112">Using the service moniker with a Mex address</span></span>  
  
1.  <span data-ttu-id="dcf76-113">請建置「使用者入門」範例，並使用 Internet Explorer 瀏覽至其 URL (http://localhost/ServiceModelSamples/Service.svc)，以確保服務正在運作。</span><span class="sxs-lookup"><span data-stu-id="dcf76-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2.  <span data-ttu-id="dcf76-114">建立 Visual Basic 指令碼或含有下列程式碼的 Visual Basic 應用程式：</span><span class="sxs-lookup"><span data-stu-id="dcf76-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```  
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3.  <span data-ttu-id="dcf76-115">執行 Visual Basic 應用程式或指令碼。</span><span class="sxs-lookup"><span data-stu-id="dcf76-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dcf76-116">您正在呼叫的服務必須公開 Mex 端點，Moniker 才能從服務讀取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="dcf76-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="dcf76-117">如需詳細資訊，請參閱[How to： 使用組態檔的服務發行中繼資料](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="dcf76-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dcf76-118">如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。</span><span class="sxs-lookup"><span data-stu-id="dcf76-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="dcf76-119">如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。</span><span class="sxs-lookup"><span data-stu-id="dcf76-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf76-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="dcf76-120">See Also</span></span>  
 [<span data-ttu-id="dcf76-121">如何：使用 Windows Communication Foundation 服務 Moniker 且不註冊</span><span class="sxs-lookup"><span data-stu-id="dcf76-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 [<span data-ttu-id="dcf76-122">如何：使用服務 Moniker 搭配 WSDL 合約</span><span class="sxs-lookup"><span data-stu-id="dcf76-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
