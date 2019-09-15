---
title: FindPrivateKey 範例-WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: 4ba4316489c1494da9421bea5c513e44c6eb50a7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989877"
---
# <a name="findprivatekey-sample"></a><span data-ttu-id="bbf97-102">FindPrivateKey 範例</span><span class="sxs-lookup"><span data-stu-id="bbf97-102">FindPrivateKey sample</span></span>

<span data-ttu-id="bbf97-103">在憑證存放區中尋找與特定 X.509 憑證相關聯的私密金鑰檔案位置和名稱，可能相當困難。</span><span class="sxs-lookup"><span data-stu-id="bbf97-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="bbf97-104">FindPrivateKey.exe 工具有助於進行這個程序。</span><span class="sxs-lookup"><span data-stu-id="bbf97-104">The FindPrivateKey.exe tool facilitates this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bbf97-105">FindPrivateKey 是必須先編譯才能使用的範例。</span><span class="sxs-lookup"><span data-stu-id="bbf97-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="bbf97-106">如需如何建立 FindPrivateKey 工具的指示，請參閱 <<c0>若要建立 FindPrivateKey 專案一節。</span><span class="sxs-lookup"><span data-stu-id="bbf97-106">See the [To build the FindPrivateKey project](#to-build-the-findprivatekey-project) section for instructions on how to build the FindPrivateKey tool.</span></span>

<span data-ttu-id="bbf97-107">X.509 憑證是由電腦中的系統管理員或任何使用者所安裝。</span><span class="sxs-lookup"><span data-stu-id="bbf97-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="bbf97-108">不過，在不同帳戶下執行的服務可能會存取憑證。</span><span class="sxs-lookup"><span data-stu-id="bbf97-108">However, the certificate may be accessed by a service running under a different account.</span></span> <span data-ttu-id="bbf97-109">例如，NETWORK SERVICE 帳戶。</span><span class="sxs-lookup"><span data-stu-id="bbf97-109">For example, the NETWORK SERVICE account.</span></span>

<span data-ttu-id="bbf97-110">這個帳戶可能無法用來存取私密金鑰檔案，因為憑證原先並非透過這個帳戶來安裝。</span><span class="sxs-lookup"><span data-stu-id="bbf97-110">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="bbf97-111">FindPrivateKey 工具提供您指定之 X.509 憑證的私密金鑰檔案位置。</span><span class="sxs-lookup"><span data-stu-id="bbf97-111">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="bbf97-112">一旦知道特定 X.509 憑證的私密金鑰檔案位置之後，您就可以新增權限至此檔案或移除此檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="bbf97-112">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>

<span data-ttu-id="bbf97-113">使用憑證來進行安全性的範例會使用*安裝程式 .bat*檔案中的 FindPrivateKey 工具。</span><span class="sxs-lookup"><span data-stu-id="bbf97-113">The samples that use certificates for security use the FindPrivateKey tool in the *Setup.bat* file.</span></span> <span data-ttu-id="bbf97-114">一旦找到私密金鑰檔案之後，您就可以使用其他工具（例如*Cacls* ），在檔案上設定適當的存取權限。</span><span class="sxs-lookup"><span data-stu-id="bbf97-114">Once the private key file has been found, you can use other tools such as *Cacls.exe* to set the appropriate access rights onto the file.</span></span>

<span data-ttu-id="bbf97-115">在使用者帳戶（例如自我裝載的可執行檔）下執行 Windows Communication Foundation （WCF）服務時，請確定使用者帳戶具有該檔案的唯讀存取權。</span><span class="sxs-lookup"><span data-stu-id="bbf97-115">When running a Windows Communication Foundation (WCF) service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="bbf97-116">在 Internet Information Services （IIS）下執行 WCF 服務時，用來執行服務的預設帳戶是 IIS 7 和更早版本上的網路服務，或是 IIS 7.5 和更新版本上的應用程式集區識別。</span><span class="sxs-lookup"><span data-stu-id="bbf97-116">When running a WCF service under Internet Information Services (IIS) the default accounts that the service runs under are the NETWORK SERVICE on IIS 7 and earlier versions, or Application Pool Identity on IIS 7.5 and later versions.</span></span> <span data-ttu-id="bbf97-117">如需詳細資訊，請參閱[應用程式集](/iis/manage/configuring-security/application-pool-identities)區身分識別。</span><span class="sxs-lookup"><span data-stu-id="bbf97-117">For more information, see [Application Pool Identities](/iis/manage/configuring-security/application-pool-identities).</span></span>

## <a name="examples"></a><span data-ttu-id="bbf97-118">範例</span><span class="sxs-lookup"><span data-stu-id="bbf97-118">Examples</span></span>

<span data-ttu-id="bbf97-119">存取進程沒有讀取權限的憑證時，您會看到類似下列範例的例外狀況訊息：</span><span class="sxs-lookup"><span data-stu-id="bbf97-119">When accessing a certificate for which the process doesn't have read privilege, you see an exception message similar to the following example:</span></span>

```output
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

<span data-ttu-id="bbf97-120">發生這種情況時，請使用 FindPrivateKey 工具來尋找私密金鑰檔案，然後設定服務執行所在進程的存取權限。</span><span class="sxs-lookup"><span data-stu-id="bbf97-120">When this occurs, use the FindPrivateKey tool to find the private key file, and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="bbf97-121">例如，您可以使用 Cacls 工具來完成這項作業，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bbf97-121">For example, this can be done with the Cacls.exe tool as shown in the following example:</span></span>

```console
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="bbf97-122">若要建置 FindPrivateKey 專案</span><span class="sxs-lookup"><span data-stu-id="bbf97-122">To build the FindPrivateKey project</span></span>

<span data-ttu-id="bbf97-123">若要下載專案，請造訪[適用于 .NET Framework 4 的 Windows Communication Foundation （WCF）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)。</span><span class="sxs-lookup"><span data-stu-id="bbf97-123">To download the project, visit [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459).</span></span>

1. <span data-ttu-id="bbf97-124">開啟 [檔案瀏覽器]，然後流覽至安裝範例所在目錄位置下的 [ *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="bbf97-124">Open File Explorer and navigate to the *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS* folder under the directory location where you installed the sample.</span></span>

2. <span data-ttu-id="bbf97-125">按兩下 .sln 檔案圖示，在 Visual Studio 中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="bbf97-125">Double-click the .sln file icon to open the file in Visual Studio.</span></span>

3. <span data-ttu-id="bbf97-126">在 [**建立**] 功能表中，選取 [**重建方案**]。</span><span class="sxs-lookup"><span data-stu-id="bbf97-126">In the **Build** menu, select **Rebuild Solution**.</span></span>

4. <span data-ttu-id="bbf97-127">建立解決方案會產生檔案：FindPrivateKey .exe。</span><span class="sxs-lookup"><span data-stu-id="bbf97-127">Building the solution generates the file: FindPrivateKey.exe.</span></span>

## <a name="conventionscommand-line-entries"></a><span data-ttu-id="bbf97-128">慣例-命令列專案</span><span class="sxs-lookup"><span data-stu-id="bbf97-128">Conventions—Command-Line entries</span></span>

 <span data-ttu-id="bbf97-129">"[*option*]" 代表一組選擇性的參數。</span><span class="sxs-lookup"><span data-stu-id="bbf97-129">"[*option*]" represents an optional set of parameters.</span></span>

 <span data-ttu-id="bbf97-130">"{*option*}" 代表一組必要的參數。</span><span class="sxs-lookup"><span data-stu-id="bbf97-130">"{*option*}" represents a mandatory set of parameters.</span></span>

 <span data-ttu-id="bbf97-131">"*option1* &#124; *option2*" 代表選項組之間的選擇。</span><span class="sxs-lookup"><span data-stu-id="bbf97-131">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>

 <span data-ttu-id="bbf97-132">「值 >」代表要輸入的參數值。 \<</span><span class="sxs-lookup"><span data-stu-id="bbf97-132">"\<*value*>" represents a parameter value to be entered.</span></span>

## <a name="usage"></a><span data-ttu-id="bbf97-133">使用量</span><span class="sxs-lookup"><span data-stu-id="bbf97-133">Usage</span></span>

```console
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

<span data-ttu-id="bbf97-134">其中：</span><span class="sxs-lookup"><span data-stu-id="bbf97-134">Where:</span></span>

| <span data-ttu-id="bbf97-135">參數</span><span class="sxs-lookup"><span data-stu-id="bbf97-135">Parameter</span></span>         | <span data-ttu-id="bbf97-136">說明</span><span class="sxs-lookup"><span data-stu-id="bbf97-136">Description</span></span>                                                                       |
|-----------------|-----------------------------------------------------------------------------------|
| `<subjectName>` | <span data-ttu-id="bbf97-137">憑證的主體名稱</span><span class="sxs-lookup"><span data-stu-id="bbf97-137">The subject name of the certificate</span></span>                                               |
| `<thumbprint>`  | <span data-ttu-id="bbf97-138">憑證的指紋（您可以使用 Certmgr.msc 來尋找此項）</span><span class="sxs-lookup"><span data-stu-id="bbf97-138">The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)</span></span> |
| `-f`            | <span data-ttu-id="bbf97-139">僅輸出檔案名</span><span class="sxs-lookup"><span data-stu-id="bbf97-139">output file name only</span></span>                                                             |
| `-d`            | <span data-ttu-id="bbf97-140">僅輸出目錄</span><span class="sxs-lookup"><span data-stu-id="bbf97-140">output directory only</span></span>                                                             |
| `-a`            | <span data-ttu-id="bbf97-141">輸出絕對的檔案名</span><span class="sxs-lookup"><span data-stu-id="bbf97-141">output absolute file name</span></span>                                                         |

<span data-ttu-id="bbf97-142">如果在命令提示字元中未指定任何參數，則會顯示含有這則資訊的解說文字。</span><span class="sxs-lookup"><span data-stu-id="bbf97-142">If no parameters are specified at the command prompt, then help text with this information is displayed.</span></span>

## <a name="examples"></a><span data-ttu-id="bbf97-143">範例</span><span class="sxs-lookup"><span data-stu-id="bbf97-143">Examples</span></span>

<span data-ttu-id="bbf97-144">這個範例會在目前使用者的個人存放區中，尋找主體名稱為 "CN = localhost" 之憑證的檔案名。</span><span class="sxs-lookup"><span data-stu-id="bbf97-144">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost"
```

<span data-ttu-id="bbf97-145">這個範例會在目前使用者的個人存放區中，尋找主體名稱為 "CN = localhost" 之憑證的檔案名，並輸出完整的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="bbf97-145">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User and output the full directory path.</span></span>

```console
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

<span data-ttu-id="bbf97-146">這個範例會在 Local Computer 的 Personal 存放區中尋找指紋為 "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" 之憑證的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="bbf97-146">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>

```console
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
