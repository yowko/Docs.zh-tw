---
title: WCF 安全性中的加密彈性
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: a97f0b908d3c4d2e14fb55ec21371322dc740e47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668895"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="4a687-102">WCF 安全性中的加密彈性</span><span class="sxs-lookup"><span data-stu-id="4a687-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="4a687-103">此範例示範如何在提供的密碼編譯的敏捷式實作 Windows Communication Foundation (WCF) 用戶端和服務中的標準/自訂演算法中指定。</span><span class="sxs-lookup"><span data-stu-id="4a687-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="4a687-104">此範例是由下列專案所組成：</span><span class="sxs-lookup"><span data-stu-id="4a687-104">The sample is composed of the following projects:</span></span>

 <span data-ttu-id="4a687-105">這是自我裝載的 WCF 服務實作的服務`ICalculator`介面，並保護端點使用 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 安全工作階段與可靠工作階段停用。</span><span class="sxs-lookup"><span data-stu-id="4a687-105">Service This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="4a687-106">這項服務會定義自訂的 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="4a687-106">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

 <span data-ttu-id="4a687-107">用戶端這是在成功驗證之後存取服務 [wcfclient]。</span><span class="sxs-lookup"><span data-stu-id="4a687-107">Client This is a WCFclient that accesses the service after successful authentication.</span></span> <span data-ttu-id="4a687-108">它會叫用由 `ICalculator` 介面公開並且由服務實作的作業。</span><span class="sxs-lookup"><span data-stu-id="4a687-108">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="4a687-109">這個用戶端還會定義相同的自訂 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="4a687-109">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="4a687-110">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="4a687-110">To use this sample</span></span>

1.  <span data-ttu-id="4a687-111">Visual Studio 2012 中開啟 CryptoAgility.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="4a687-111">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2.  <span data-ttu-id="4a687-112">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="4a687-112">Press CTRL+SHIFT+B to build the solution.</span></span>

3.  <span data-ttu-id="4a687-113">開啟[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]並巡覽至 \WCF\Basic\Security\CryptoAgility\Service\bin 目錄，然後以系統管理員權限執行 service.exe 檔，以滑鼠右鍵按一下 service.exe 並選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="4a687-113">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4.  <span data-ttu-id="4a687-114">巡覽至 \WCF\Basic\Security\CryptoAgility\Client\bin 目錄，並正常執行 client.exe 檔。</span><span class="sxs-lookup"><span data-stu-id="4a687-114">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="4a687-115">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="4a687-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4a687-116">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="4a687-116">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4a687-117">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="4a687-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4a687-118">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="4a687-118">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="4a687-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a687-119">See also</span></span>
- [<span data-ttu-id="4a687-120">安全性</span><span class="sxs-lookup"><span data-stu-id="4a687-120">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
