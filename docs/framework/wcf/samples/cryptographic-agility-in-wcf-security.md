---
title: "WCF 安全性中的加密彈性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7d99ada67255d0ced8bbabc2ab6fc645e6ba9e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="f0686-102">WCF 安全性中的加密彈性</span><span class="sxs-lookup"><span data-stu-id="f0686-102">Cryptographic Agility in WCF Security</span></span>
<span data-ttu-id="f0686-103">本範例示範如何在標準/自訂演算法中指定，以便在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 用戶端和服務中提供敏捷的密碼編譯實作。</span><span class="sxs-lookup"><span data-stu-id="f0686-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client and service.</span></span> <span data-ttu-id="f0686-104">此範例是由下列專案所組成：</span><span class="sxs-lookup"><span data-stu-id="f0686-104">The sample is composed of the following projects:</span></span>  
  
 <span data-ttu-id="f0686-105">服務</span><span class="sxs-lookup"><span data-stu-id="f0686-105">Service</span></span>  
 <span data-ttu-id="f0686-106">這是自我裝載[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]實作服務`ICalculator`介面，並可保護端點使用 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> 安全工作階段與可靠工作階段停用。</span><span class="sxs-lookup"><span data-stu-id="f0686-106">This is a self-hosted [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements the `ICalculator` interface and secures the endpoint using the <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> with secure session and reliable session disabled.</span></span> <span data-ttu-id="f0686-107">這項服務會定義自訂的 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="f0686-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
 <span data-ttu-id="f0686-108">用戶端</span><span class="sxs-lookup"><span data-stu-id="f0686-108">Client</span></span>  
 <span data-ttu-id="f0686-109">這是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，會在驗證成功之後存取服務。</span><span class="sxs-lookup"><span data-stu-id="f0686-109">This is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]client that accesses the service after successful authentication.</span></span> <span data-ttu-id="f0686-110">它會叫用由 `ICalculator` 介面公開並且由服務實作的作業。</span><span class="sxs-lookup"><span data-stu-id="f0686-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="f0686-111">這個用戶端還會定義相同的自訂 `SecurityAlgorithmSuite` 類別，以指定用於訊息安全性的密碼編譯演算法。</span><span class="sxs-lookup"><span data-stu-id="f0686-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="f0686-112">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="f0686-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="f0686-113">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中開啟 CryptoAgility.sln 方案。</span><span class="sxs-lookup"><span data-stu-id="f0686-113">Open the CryptoAgility.sln solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="f0686-114">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="f0686-114">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="f0686-115">開啟[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]並巡覽至 \WCF\Basic\Security\CryptoAgility\Service\bin 目錄，然後以系統管理權限執行 service.exe 檔，以滑鼠右鍵按一下 service.exe 並選取**系統管理員身分執行**。</span><span class="sxs-lookup"><span data-stu-id="f0686-115">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="f0686-116">巡覽至 \WCF\Basic\Security\CryptoAgility\Client\bin 目錄，並正常執行 client.exe 檔。</span><span class="sxs-lookup"><span data-stu-id="f0686-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f0686-117">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="f0686-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f0686-118">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="f0686-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f0686-119">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="f0686-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f0686-120">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="f0686-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a><span data-ttu-id="f0686-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0686-121">See Also</span></span>  
 [<span data-ttu-id="f0686-122">安全性</span><span class="sxs-lookup"><span data-stu-id="f0686-122">Security</span></span>](../../../../docs/framework/wcf/feature-details/security.md)
