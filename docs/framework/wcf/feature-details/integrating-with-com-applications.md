---
title: 整合 COM 應用程式
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: dc3bbe0ee72ca5583b1e52a61c914ad866a22a05
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596806"
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="ed01a-102">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="ed01a-102">Integrating with COM Applications</span></span>
<span data-ttu-id="ed01a-103">Windows Communication Foundation （WCF）服務可以使用 WCF 服務標記，直接整合到您現有的程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ed01a-103">Windows Communication Foundation (WCF) services can be integrated directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="ed01a-104">服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。</span><span class="sxs-lookup"><span data-stu-id="ed01a-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed01a-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="ed01a-105">In This Section</span></span>  
 [<span data-ttu-id="ed01a-106">與 COM 應用程式整合總覽</span><span class="sxs-lookup"><span data-stu-id="ed01a-106">Integrating with COM Applications Overview</span></span>](integrating-with-com-applications-overview.md)  
 <span data-ttu-id="ed01a-107">提供整合處理序主要部分的概觀。</span><span class="sxs-lookup"><span data-stu-id="ed01a-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="ed01a-108">如何：註冊和設定服務 Moniker</span><span class="sxs-lookup"><span data-stu-id="ed01a-108">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="ed01a-109">若要在 COM 應用程式中使用 WCF 服務名字標記，請向 COM 註冊必要的屬性化型別，並以必要的系結設定來設定 COM 應用程式和名字。</span><span class="sxs-lookup"><span data-stu-id="ed01a-109">To use the WCF service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="ed01a-110">HOW TO：使用 Windows Communication Foundation 服務 Moniker 且不註冊</span><span class="sxs-lookup"><span data-stu-id="ed01a-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="ed01a-111">說明如何取得格式為 Web Services Definition Language (WSDL) 文件的合約定義，或如何從 WS-MetadataExchange 端點取得該定義。</span><span class="sxs-lookup"><span data-stu-id="ed01a-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="ed01a-112">如何：使用服務 Moniker 搭配 WSDL 合約</span><span class="sxs-lookup"><span data-stu-id="ed01a-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="ed01a-113">描述如何使用 WCF WSDL 標記呼叫 WCF 範例。</span><span class="sxs-lookup"><span data-stu-id="ed01a-113">Describes how to call a WCF sample using a WCF WSDL moniker.</span></span>  
  
 [<span data-ttu-id="ed01a-114">如何：使用服務 Moniker 搭配中繼資料交換合約</span><span class="sxs-lookup"><span data-stu-id="ed01a-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="ed01a-115">描述如何使用指定 Mex 端點的 WCF 標記呼叫 WCF 範例。</span><span class="sxs-lookup"><span data-stu-id="ed01a-115">Describes how to call a WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="ed01a-116">HOW TO：指定通道安全性認證</span><span class="sxs-lookup"><span data-stu-id="ed01a-116">How to: Specify Channel Security Credentials</span></span>](how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="ed01a-117">WCF 服務的「標記」支援 `IChannelCredentials` 介面，可允許一系列的替代方法來指定通道認證。</span><span class="sxs-lookup"><span data-stu-id="ed01a-117">The WCF service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ed01a-118">參考</span><span class="sxs-lookup"><span data-stu-id="ed01a-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="ed01a-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed01a-119">See also</span></span>

- [<span data-ttu-id="ed01a-120">與 COM + 應用程式整合</span><span class="sxs-lookup"><span data-stu-id="ed01a-120">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
