---
title: "延伸保護驗證之範例的讀我檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3981a0d0c82b8bc35536a9afd702e753fcf07db5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="9e894-102">延伸保護驗證之範例的讀我檔案</span><span class="sxs-lookup"><span data-stu-id="9e894-102">ReadMe for Extended Protection Authentication Sample</span></span>
<span data-ttu-id="9e894-103">延伸的保護是一項安全性方案來抵禦攔截 (MITM) 攻擊，攻擊者 （"--攔截 」） 攔截用戶端認證並使用它們來存取用戶端想要的伺服器上的安全資源保護。</span><span class="sxs-lookup"><span data-stu-id="9e894-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>  
  
 <span data-ttu-id="9e894-104">如需詳細資訊，請參閱[Extended Protection for Authentication 概觀](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9e894-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e894-105">這個範例僅適用於由 IIS 裝載的情況。</span><span class="sxs-lookup"><span data-stu-id="9e894-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="9e894-106">Visual Studio 程式開發伺服器不支援 HTTPS，所以並不適用。</span><span class="sxs-lookup"><span data-stu-id="9e894-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9e894-107">安裝設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="9e894-107">To Set Up, Build, and Run the Sample</span></span>  
  
1.  <span data-ttu-id="9e894-108">透過 [新增/移除程式] -> [Windows 功能]，在電腦上安裝 IIS。</span><span class="sxs-lookup"><span data-stu-id="9e894-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>  
  
2.  <span data-ttu-id="9e894-109">啟用 Windows 功能中的 Windows 驗證：[Internet Information Services] -> [全球資訊網服務] -> [安全性] -> [Windows 驗證]。</span><span class="sxs-lookup"><span data-stu-id="9e894-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>  
  
3.  <span data-ttu-id="9e894-110">啟用 Windows 功能中的 HTTP 啟動：[Microsoft .NET Framework 3.5.1] -> [Windows Communication Foundation HTTP 啟動]。</span><span class="sxs-lookup"><span data-stu-id="9e894-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>  
  
4.  <span data-ttu-id="9e894-111">這個範例需由用戶端與伺服器建立安全通道，所以必須有可從 Internet Information Services (IIS) 管理員進行安裝的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="9e894-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="9e894-112">開啟 [IIS 管理員] -> [伺服器憑證] (位於功能檢視索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="9e894-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>  
  
    2.  <span data-ttu-id="9e894-113">為了測試這個範例，您可以建立自我簽署憑證 </span><span class="sxs-lookup"><span data-stu-id="9e894-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="9e894-114">(若不希望 Internet Explorer 出現憑證可能不安全的提示，可將此憑證安裝到 [受信任的根憑證授權單位] 存放區)。</span><span class="sxs-lookup"><span data-stu-id="9e894-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>  
  
5.  <span data-ttu-id="9e894-115">移至 [預設的網站] 的 [執行] 窗格。</span><span class="sxs-lookup"><span data-stu-id="9e894-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="9e894-116">按一下 [編輯站台] -> [繫結]。</span><span class="sxs-lookup"><span data-stu-id="9e894-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="9e894-117">新增 HTTPS 做為繫結類型 (如果沒有此項)，連接埠編號為 443，並指派上一個步驟所建立的 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="9e894-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>  
  
6.  <span data-ttu-id="9e894-118">建置服務。</span><span class="sxs-lookup"><span data-stu-id="9e894-118">Build the service.</span></span> <span data-ttu-id="9e894-119">這樣會建立一個 IIS 虛擬目錄 (透過專案屬性中指定的建置後動作)，並且視需要複製 Web 裝載服務的 dll、.svc 和 config 檔案。</span><span class="sxs-lookup"><span data-stu-id="9e894-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>  
  
7.  <span data-ttu-id="9e894-120">開啟 [IIS 管理員]。</span><span class="sxs-lookup"><span data-stu-id="9e894-120">Open the IIS Manager.</span></span> <span data-ttu-id="9e894-121">以滑鼠右鍵按一下先前步驟所建立的虛擬目錄 (ExtendedProtection)，選取 [轉換成應用程式]。</span><span class="sxs-lookup"><span data-stu-id="9e894-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>  
  
8.  <span data-ttu-id="9e894-122">開啟此虛擬目錄在 [IIS 管理員] 中的驗證模組，然後啟用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="9e894-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>  
  
9. <span data-ttu-id="9e894-123">開啟此虛擬目錄 Windows 驗證的 [進階設定] 並將其設為 [必要]，因為這個範例中 ExtendedProtection 的相應設定是設為 [永遠]。</span><span class="sxs-lookup"><span data-stu-id="9e894-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>  
  
10. <span data-ttu-id="9e894-124">您可以從瀏覽器視窗存取 URL 來測試服務。</span><span class="sxs-lookup"><span data-stu-id="9e894-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="9e894-125">若想要從其他電腦存取此 URL，請確定防火牆已開放所有傳入的 HTTP 和 HTTPS 連線。</span><span class="sxs-lookup"><span data-stu-id="9e894-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>  
  
11. <span data-ttu-id="9e894-126">開啟用戶端組態檔，並提供完整電腦名稱\<用戶端 >-\<端點 >-位址屬性，取代 << full_machine_name >>。</span><span class="sxs-lookup"><span data-stu-id="9e894-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing <<full_machine_name>>.</span></span>  
  
12. <span data-ttu-id="9e894-127">執行該用戶端。</span><span class="sxs-lookup"><span data-stu-id="9e894-127">Run the client.</span></span> <span data-ttu-id="9e894-128">用戶端隨即建立安全通道，在延伸保護的庇護之下與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="9e894-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
