---
title: 延伸保護驗證之範例的讀我檔案
ms.date: 03/30/2017
ms.assetid: 80bf2e97-398d-4db5-9040-d96478a2ccab
ms.openlocfilehash: cc60ee32efcbe1e6ac1ce620fa1c17504db5197f
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690584"
---
# <a name="readme-for-extended-protection-authentication-sample"></a><span data-ttu-id="38264-102">延伸保護驗證之範例的讀我檔案</span><span class="sxs-lookup"><span data-stu-id="38264-102">ReadMe for Extended Protection Authentication Sample</span></span>

<span data-ttu-id="38264-103">延伸的保護是一項安全性方案以防止攔截 (MITM) 攻擊，攻擊者 （"--攔截 」） 會攔截用戶端的認證和使用它們來存取用戶端想要的伺服器上的安全資源。</span><span class="sxs-lookup"><span data-stu-id="38264-103">Extended Protection is a security initiative to protect against man-in-the-middle (MITM) attacks, in which an attacker (the "man-in-the-middle") intercepts a client’s credentials and uses them to access secure resources on the client’s intended server.</span></span>

<span data-ttu-id="38264-104">如需詳細資訊，請參閱 < [Extended Protection for Authentication 概觀](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="38264-104">For more information, see [Extended Protection for Authentication Overview](../../../../docs/framework/wcf/feature-details/extended-protection-for-authentication-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="38264-105">這個範例僅適用於由 IIS 裝載的情況。</span><span class="sxs-lookup"><span data-stu-id="38264-105">This sample only works when hosted on IIS.</span></span> <span data-ttu-id="38264-106">Visual Studio 程式開發伺服器不支援 HTTPS，所以並不適用。</span><span class="sxs-lookup"><span data-stu-id="38264-106">It does not work on Visual Studio Development Server because that does not support HTTPS.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38264-107">安裝設定、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="38264-107">To Set Up, Build, and Run the Sample</span></span>

1. <span data-ttu-id="38264-108">安裝 IIS 電腦上，從 新增/移除程式-> Windows 功能。</span><span class="sxs-lookup"><span data-stu-id="38264-108">Install IIS on the machine from Add/Remove Programs -> Windows Features.</span></span>

2. <span data-ttu-id="38264-109">開啟 Windows 驗證，在 Windows 功能：網際網路資訊服務-> World Wide Web 服務-> 安全性-> Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="38264-109">Turn on Windows Authentication in Windows features: Internet Information Services -> World Wide Web Services -> Security -> Windows Authentication.</span></span>

3. <span data-ttu-id="38264-110">在 Windows 功能，以開啟 HTTP 啟動：Microsoft.NET Framework 3.5.1-> Windows Communication Foundation HTTP 啟動。</span><span class="sxs-lookup"><span data-stu-id="38264-110">Turn on HTTP Activation in Windows features: Microsoft .NET Framework 3.5.1 -> Windows Communication Foundation HTTP Activation.</span></span>

4. <span data-ttu-id="38264-111">這個範例需由用戶端與伺服器建立安全通道，所以必須有可從 Internet Information Services (IIS) 管理員進行安裝的伺服器憑證。</span><span class="sxs-lookup"><span data-stu-id="38264-111">This sample requires the client to establish a secure channel with the server and so it requires the presence of a server certificate which can be installed from Internet Information Services (IIS) Manager.</span></span>

    1. <span data-ttu-id="38264-112">開啟 [IIS 管理員] -> [伺服器憑證] \(位於功能檢視索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="38264-112">Open the IIS manager -> Server certificates (from the feature view tab).</span></span>

    2. <span data-ttu-id="38264-113">為了測試這個範例，您可以建立自我簽署憑證</span><span class="sxs-lookup"><span data-stu-id="38264-113">For the purpose of testing this sample, you can create a self-signed certificate.</span></span> <span data-ttu-id="38264-114">(若不希望 Internet Explorer 出現憑證可能不安全的提示，可將此憑證安裝到 [受信任的根憑證授權單位] 存放區)。</span><span class="sxs-lookup"><span data-stu-id="38264-114">(If you don’t want Internet Explorer to prompt you about the certificate not being secure, you can install it in the Trusted Certificate Root authority store).</span></span>

5. <span data-ttu-id="38264-115">移至 [預設的網站] 的 [執行] 窗格。</span><span class="sxs-lookup"><span data-stu-id="38264-115">Go to the Actions pane for the Default Web site.</span></span> <span data-ttu-id="38264-116">按一下 編輯站台-> 繫結。</span><span class="sxs-lookup"><span data-stu-id="38264-116">Click Edit Site -> Bindings.</span></span> <span data-ttu-id="38264-117">新增 HTTPS 做為繫結類型 (如果沒有此項)，連接埠編號為 443，並指派上一個步驟所建立的 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="38264-117">Add HTTPS as a type if it is not already present, with port number 443, and assign the SSL certificate created in the above step.</span></span>

6. <span data-ttu-id="38264-118">建置服務。</span><span class="sxs-lookup"><span data-stu-id="38264-118">Build the service.</span></span> <span data-ttu-id="38264-119">這樣會建立一個 IIS 虛擬目錄 (透過專案屬性中指定的建置後動作)，並且視需要複製 Web 裝載服務的 dll、.svc 和 config 檔案。</span><span class="sxs-lookup"><span data-stu-id="38264-119">This creates a virtual directory in IIS for you (from the post build action specified in the project properties) and copies the dll, .svc and config files as needed for a service to be Web hosted.</span></span>

7. <span data-ttu-id="38264-120">開啟 [IIS 管理員]。</span><span class="sxs-lookup"><span data-stu-id="38264-120">Open the IIS Manager.</span></span> <span data-ttu-id="38264-121">以滑鼠右鍵按一下先前步驟所建立的虛擬目錄 (ExtendedProtection)，選取 [轉換成應用程式]。</span><span class="sxs-lookup"><span data-stu-id="38264-121">Right-click the virtual directory (ExtendedProtection) that you created in the previous step and select Convert to Application.</span></span>

8. <span data-ttu-id="38264-122">開啟此虛擬目錄在 [IIS 管理員] 中的驗證模組，然後啟用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="38264-122">Open the Authentication module in IIS Manager for this virtual directory and enable Windows Authentication.</span></span>

9. <span data-ttu-id="38264-123">開啟此虛擬目錄 Windows 驗證的 [進階設定] 並將其設為 [必要]，因為這個範例中 ExtendedProtection 的相應設定是設為 [永遠]。</span><span class="sxs-lookup"><span data-stu-id="38264-123">Open the Advanced Settings for Windows Authentication for this virtual directory and set it to Required, since, in the sample, the corresponding ExtendedProtection setting is set to Always.</span></span>

10. <span data-ttu-id="38264-124">您可以從瀏覽器視窗存取 URL 來測試服務。</span><span class="sxs-lookup"><span data-stu-id="38264-124">You can test the service by accessing the URL from a browser window.</span></span> <span data-ttu-id="38264-125">若想要從其他電腦存取此 URL，請確定防火牆已開放所有傳入的 HTTP 和 HTTPS 連線。</span><span class="sxs-lookup"><span data-stu-id="38264-125">If you want to access this URL from a cross machine, make sure that the firewall is opened for all incoming HTTP and HTTPS connections.</span></span>

11. <span data-ttu-id="38264-126">開啟用戶端組態檔，並提供完整電腦名稱\<用戶端 >-\<端點 >-address 屬性取代\<full_machine_name >。</span><span class="sxs-lookup"><span data-stu-id="38264-126">Open the client config file and provide a full machine name for the \<client> - \<endpoint> - address attribute, replacing \<full_machine_name>.</span></span>

12. <span data-ttu-id="38264-127">執行該用戶端。</span><span class="sxs-lookup"><span data-stu-id="38264-127">Run the client.</span></span> <span data-ttu-id="38264-128">用戶端隨即建立安全通道，在延伸保護的庇護之下與服務通訊。</span><span class="sxs-lookup"><span data-stu-id="38264-128">The client communicates to the service by establishing a secure channel and using extended protection under the covers.</span></span>
