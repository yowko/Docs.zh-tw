---
title: FindPrivateKey 範例-WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490766"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="85ceb-102">FindPrivateKey 範例</span><span class="sxs-lookup"><span data-stu-id="85ceb-102">FindPrivateKey sample</span></span>

<span data-ttu-id="85ceb-103">在憑證存放區中尋找與特定 X.509 憑證相關聯的私密金鑰檔案位置和名稱，可能相當困難。</span><span class="sxs-lookup"><span data-stu-id="85ceb-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="85ceb-104">FindPrivateKey.exe 工具有助於進行這個程序。</span><span class="sxs-lookup"><span data-stu-id="85ceb-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="85ceb-105">FindPrivateKey 是必須先編譯才能使用的範例。</span><span class="sxs-lookup"><span data-stu-id="85ceb-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="85ceb-106">請參閱[若要建置 FindPrivateKey 專案](#to-build-the-findprivatekey-project)區段，如需有關如何建置 FindPrivateKey 工具。</span><span class="sxs-lookup"><span data-stu-id="85ceb-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="85ceb-107">X.509 憑證是由電腦中的系統管理員或任何使用者所安裝。</span><span class="sxs-lookup"><span data-stu-id="85ceb-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="85ceb-108">不過，憑證可能由不同的帳戶下執行的服務存取。</span><span class="sxs-lookup"><span data-stu-id="85ceb-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="85ceb-109">比方說，NETWORK SERVICE 帳戶。</span><span class="sxs-lookup"><span data-stu-id="85ceb-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="85ceb-110">這個帳戶可能無法用來存取私密金鑰檔案，因為憑證原先並非透過這個帳戶來安裝。</span><span class="sxs-lookup"><span data-stu-id="85ceb-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="85ceb-111">FindPrivateKey 工具提供您指定之 X.509 憑證的私密金鑰檔案位置。</span><span class="sxs-lookup"><span data-stu-id="85ceb-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="85ceb-112">一旦知道特定 X.509 憑證的私密金鑰檔案位置之後，您就可以新增權限至此檔案或移除此檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="85ceb-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="85ceb-113">使用憑證安全性的範例使用中的 FindPrivateKey 工具*Setup.bat*檔案。</span><span class="sxs-lookup"><span data-stu-id="85ceb-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="85ceb-114">一旦已找到私密金鑰檔案，您可以使用其他工具這類*Cacls.exe*為檔案設定適當的存取權。</span><span class="sxs-lookup"><span data-stu-id="85ceb-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="85ceb-115">當執行 Windows Communication Foundation (WCF) 服務是自我裝載可執行檔的使用者帳戶下確認使用者帳戶對檔案唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="85ceb-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="85ceb-116">執行 WCF 服務在網際網路資訊服務 (IIS) 時執行服務的預設帳戶是在 IIS 7 和舊版中，網路服務或 IIS 7.5 和更新版本上的應用程式集區識別。</span><span class="sxs-lookup"><span data-stu-id="85ceb-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="85ceb-117">如需詳細資訊，請參閱 <<c0> [ 應用程式集區識別](/iis/manage/configuring-security/application-pool-identities)。</span><span class="sxs-lookup"><span data-stu-id="85ceb-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="85ceb-118">範例</span><span class="sxs-lookup"><span data-stu-id="85ceb-118">Examples</span></span>

<span data-ttu-id="85ceb-119">存取時的處理序沒有讀取權限的憑證，您會看到類似下列範例的例外狀況訊息：</span><span class="sxs-lookup"><span data-stu-id="85ceb-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="85ceb-120">當發生這種情況時，若要尋找私密金鑰檔案，請使用 FindPrivateKey 工具，然後將 存取權限之下執行服務的程序。</span><span class="sxs-lookup"><span data-stu-id="85ceb-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="85ceb-121">比方說，做法是使用 Cacls.exe 工具，在下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="85ceb-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="85ceb-122">若要建置 FindPrivateKey 專案</span><span class="sxs-lookup"><span data-stu-id="85ceb-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="85ceb-123">若要下載的專案，請造訪[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://www.microsoft.com/download/details.aspx?id=21459)。</span><span class="sxs-lookup"><span data-stu-id="85ceb-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="85ceb-124">開啟檔案總管並瀏覽至*WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS*範例安裝目錄位置下的資料夾。</span><span class="sxs-lookup"><span data-stu-id="85ceb-124">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="85ceb-125">按兩下 .sln 檔案圖示，在 Visual Studio 中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="85ceb-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="85ceb-126">在 **建置**功能表上，選取**重建方案**。</span><span class="sxs-lookup"><span data-stu-id="85ceb-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="85ceb-127">建置方案時，會產生檔案：FindPrivateKey.exe。</span><span class="sxs-lookup"><span data-stu-id="85ceb-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="85ceb-128">慣例 — 命令列項目</span><span class="sxs-lookup"><span data-stu-id="85ceb-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="85ceb-129">"[*選項*]"表示一組選擇性的參數。</span><span class="sxs-lookup"><span data-stu-id="85ceb-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="85ceb-130">"{*選項*}"表示一組必要的參數。</span><span class="sxs-lookup"><span data-stu-id="85ceb-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="85ceb-131">「*option1* &#124; *option2*"代表選項組之間的選項。</span><span class="sxs-lookup"><span data-stu-id="85ceb-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="85ceb-132">「\<*值*> 」 表示輸入的參數值。</span><span class="sxs-lookup"><span data-stu-id="85ceb-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="85ceb-133">使用量</span><span class="sxs-lookup"><span data-stu-id="85ceb-133">Usage</span></span>

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="85ceb-134">其中：</span><span class="sxs-lookup"><span data-stu-id="85ceb-134">Where:</span></span>

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

<span data-ttu-id="85ceb-135">如果未不指定任何參數，在命令提示字元，則會顯示此說明文字。</span><span class="sxs-lookup"><span data-stu-id="85ceb-135">If no parameters are specified at the command prompt, then this help text is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="85ceb-136">範例</span><span class="sxs-lookup"><span data-stu-id="85ceb-136">Examples</span></span>

<span data-ttu-id="85ceb-137">此範例會尋找憑證的主體名稱為的檔案名稱"CN = localhost"，目前使用者的個人存放區中。</span><span class="sxs-lookup"><span data-stu-id="85ceb-137">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="85ceb-138">此範例會尋找憑證的主體名稱為的檔案名稱"CN = localhost"、 的個人存放區目前的使用者和輸出的完整目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="85ceb-138">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="85ceb-139">這個範例會在 Local Computer 的 Personal 存放區中尋找指紋為 "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" 之憑證的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="85ceb-139">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
