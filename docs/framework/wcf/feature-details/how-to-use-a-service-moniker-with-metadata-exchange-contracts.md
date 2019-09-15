---
title: HOW TO：使用服務 Moniker 搭配中繼資料交換合約
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: e114bc2c046ba7145a91121ce23c82912680a048
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968954"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="10167-102">HOW TO：使用服務 Moniker 搭配中繼資料交換合約</span><span class="sxs-lookup"><span data-stu-id="10167-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="10167-103">在開發一些新的 WCF 服務之後，您可能會決定要能夠從腳本或 Visual Basic 6.0 應用程式呼叫這些服務。</span><span class="sxs-lookup"><span data-stu-id="10167-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="10167-104">其中一個方法是產生 WCF 用戶端元件、向 COM 註冊元件、在 GAC 中安裝元件，然後從您的 Visual Basic 程式碼參考 COM 類型。</span><span class="sxs-lookup"><span data-stu-id="10167-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="10167-105">當您散發應用程式時，也必須散發 WCF 用戶端元件。</span><span class="sxs-lookup"><span data-stu-id="10167-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="10167-106">然後使用者必須向 COM 註冊 WCF 用戶端組件，並將它放在 GAC 中。</span><span class="sxs-lookup"><span data-stu-id="10167-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="10167-107">WCF COM Interop 也可讓您在不依賴 WCF 用戶端元件的情況下，進行相同的服務呼叫。</span><span class="sxs-lookup"><span data-stu-id="10167-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="10167-108">WCF 標記可讓您藉由指定服務標記用來解壓縮類型的中繼資料交換（Mex）端點 URI，從任何 COM 相容語言（Visual Basic、VBScript、Visual Basic for Applications （VBA）等等）呼叫任何 WCF 服務。服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="10167-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="10167-109">本主題描述如何使用指定 Mex 端點的 WCF 標記來呼叫消費者入門 WCF 範例。</span><span class="sxs-lookup"><span data-stu-id="10167-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10167-110">WCF 用戶端元件所定義的類型實際上不會具現化。</span><span class="sxs-lookup"><span data-stu-id="10167-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="10167-111">此組件僅用於中繼資料。</span><span class="sxs-lookup"><span data-stu-id="10167-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="10167-112">使用含有 Mex 位址的服務 Moniker</span><span class="sxs-lookup"><span data-stu-id="10167-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="10167-113">建立消費者入門範例，並使用 Internet Explorer 流覽至其 URL （ http://localhost/ServiceModelSamples/Service.svc) 以確保服務正常運作。</span><span class="sxs-lookup"><span data-stu-id="10167-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="10167-114">建立 Visual Basic 指令碼或含有下列程式碼的 Visual Basic 應用程式：</span><span class="sxs-lookup"><span data-stu-id="10167-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="10167-115">執行 Visual Basic 應用程式或指令碼。</span><span class="sxs-lookup"><span data-stu-id="10167-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="10167-116">您正在呼叫的服務必須公開 Mex 端點，Moniker 才能從服務讀取中繼資料。</span><span class="sxs-lookup"><span data-stu-id="10167-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="10167-117">如需詳細資訊，請參閱[如何：使用設定檔](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)發佈服務的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="10167-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="10167-118">如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。</span><span class="sxs-lookup"><span data-stu-id="10167-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="10167-119">如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。</span><span class="sxs-lookup"><span data-stu-id="10167-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10167-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10167-120">See also</span></span>

- [<span data-ttu-id="10167-121">如何：使用 Windows Communication Foundation 服務的名字標記而不進行註冊</span><span class="sxs-lookup"><span data-stu-id="10167-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="10167-122">如何：搭配 WSDL 合約使用服務標記</span><span class="sxs-lookup"><span data-stu-id="10167-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
