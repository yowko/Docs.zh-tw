---
title: WCF 安全性中的密碼編譯靈活性
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: 2dbacd53876ded76ea212dd5656cd2dded4a6e48
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714929"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="a2c87-102">WCF 安全性中的密碼編譯靈活性</span><span class="sxs-lookup"><span data-stu-id="a2c87-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="a2c87-103">這個範例示範如何在標準/自訂演算法中指定，以在 Windows Communication Foundation （WCF）用戶端和服務中提供密碼編譯 agile 執行。</span><span class="sxs-lookup"><span data-stu-id="a2c87-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="a2c87-104">此範例是由下列專案所組成：</span><span class="sxs-lookup"><span data-stu-id="a2c87-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="a2c87-105">**Service**</span><span class="sxs-lookup"><span data-stu-id="a2c87-105">**Service**</span></span>

<span data-ttu-id="a2c87-106">這是自我裝載的 WCF 服務，可執行 `ICalculator` 介面，並使用已停用安全會話和可靠會話的 <xref:System.ServiceModel.WSHttpBinding> 來保護端點。</span><span class="sxs-lookup"><span data-stu-id="a2c87-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="a2c87-107">這項服務會定義自訂的 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="a2c87-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="a2c87-108">**用戶端**</span><span class="sxs-lookup"><span data-stu-id="a2c87-108">**Client**</span></span>

<span data-ttu-id="a2c87-109">這是在成功驗證之後，會存取服務的 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="a2c87-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="a2c87-110">它會叫用由 `ICalculator` 介面公開並且由服務實作的作業。</span><span class="sxs-lookup"><span data-stu-id="a2c87-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="a2c87-111">這個用戶端還會定義相同的自訂 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="a2c87-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="a2c87-112">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="a2c87-112">To use this sample</span></span>

1. <span data-ttu-id="a2c87-113">在 Visual Studio 2012 中開啟 [CryptoAgility] 方案。</span><span class="sxs-lookup"><span data-stu-id="a2c87-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="a2c87-114">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="a2c87-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="a2c87-115">開啟 [檔案瀏覽器] 並流覽至 [\WCF\Basic\Security\CryptoAgility\Service\bin] 目錄，並以滑鼠右鍵按一下 [setup.exe]，然後選取 [以**系統管理員身分執行**]，以系統管理員許可權執行此服務 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="a2c87-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="a2c87-116">巡覽至 \WCF\Basic\Security\CryptoAgility\Client\bin 目錄，並正常執行 client.exe 檔。</span><span class="sxs-lookup"><span data-stu-id="a2c87-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a2c87-117">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="a2c87-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a2c87-118">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="a2c87-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a2c87-119">如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf）和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="a2c87-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a2c87-120">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="a2c87-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="a2c87-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="a2c87-121">See also</span></span>

- [<span data-ttu-id="a2c87-122">Windows Communication Foundation 安全性</span><span class="sxs-lookup"><span data-stu-id="a2c87-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)
