---
title: FindPrivateKey
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81ca357ccdcbe76f36f3ba56caf2013a80143728
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="findprivatekey"></a><span data-ttu-id="6199d-102">FindPrivateKey</span><span class="sxs-lookup"><span data-stu-id="6199d-102">FindPrivateKey</span></span>
<span data-ttu-id="6199d-103">在憑證存放區中尋找與特定 X.509 憑證相關聯的私密金鑰檔案位置和名稱，可能相當困難。</span><span class="sxs-lookup"><span data-stu-id="6199d-103">It can be difficult to find the location and name of the private key file associated with a specific X.509 certificate in the certificate store.</span></span> <span data-ttu-id="6199d-104">FindPrivateKey.exe 工具有助於進行這個程序。</span><span class="sxs-lookup"><span data-stu-id="6199d-104">The FindPrivateKey.exe tool facilitates this process.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6199d-105">FindPrivateKey 是必須先編譯才能使用的範例。</span><span class="sxs-lookup"><span data-stu-id="6199d-105">FindPrivateKey is a sample that needs to be compiled prior to use.</span></span> <span data-ttu-id="6199d-106">如何建置 FindPrivateKey 工具，請參閱 < 若要建置 FindPrivateKey 專案 「 下一節的指示。</span><span class="sxs-lookup"><span data-stu-id="6199d-106">See the "To build the FindPrivateKey project" section below for instructions on how to build the FindPrivateKey tool.</span></span>  
  
 <span data-ttu-id="6199d-107">X.509 憑證是由電腦中的系統管理員或任何使用者所安裝。</span><span class="sxs-lookup"><span data-stu-id="6199d-107">X.509 certificates are installed by an Administrator or any user in the machine.</span></span> <span data-ttu-id="6199d-108">然而，憑證可能由不同帳戶 (例如 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上的 ASPNET 或 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 上的 NETWORK SERVICE 帳戶) 下執行的服務存取。</span><span class="sxs-lookup"><span data-stu-id="6199d-108">However the certificate may be accessed by a service running under a different account (for example, the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE accounts on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]).</span></span>  
  
 <span data-ttu-id="6199d-109">這個帳戶可能無法用來存取私密金鑰檔案，因為憑證原先並非透過這個帳戶來安裝。</span><span class="sxs-lookup"><span data-stu-id="6199d-109">This account may not have access to the private key file because the certificate was not installed by it originally.</span></span> <span data-ttu-id="6199d-110">FindPrivateKey 工具提供您指定之 X.509 憑證的私密金鑰檔案位置。</span><span class="sxs-lookup"><span data-stu-id="6199d-110">The FindPrivateKey tool gives you the location of a given X.509 Certificate's private key file.</span></span> <span data-ttu-id="6199d-111">一旦知道特定 X.509 憑證的私密金鑰檔案位置之後，您就可以新增權限至此檔案或移除此檔案的權限。</span><span class="sxs-lookup"><span data-stu-id="6199d-111">You can add permissions or remove permissions to this file once you know the location of the particular X.509 certificates' private key file.</span></span>  
  
 <span data-ttu-id="6199d-112">基於安全性而使用憑證的範例採用 Setup.bat 檔案中的 FindPrivateKey 工具。</span><span class="sxs-lookup"><span data-stu-id="6199d-112">The samples that use certificates for security use the FindPrivateKey tool in the Setup.bat file.</span></span> <span data-ttu-id="6199d-113">一旦找到私密金鑰檔案，您就可以使用如 Cacls.exe 等其他工具，為檔案設定適當的存取權限。</span><span class="sxs-lookup"><span data-stu-id="6199d-113">Once the private key file has been found you can use other tools such as Cacls.exe to set the appropriate access rights onto the file.</span></span>  
  
 <span data-ttu-id="6199d-114">在使用者帳戶下執行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務時 (例如自我裝載的可執行檔)，請確定使用者帳戶具有檔案的唯讀權限。</span><span class="sxs-lookup"><span data-stu-id="6199d-114">When running a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service under a user account, such as a self-hosted executable, ensure that the user account has read-only access to the file.</span></span> <span data-ttu-id="6199d-115">在網際網路資訊服務 (IIS) 下執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，服務執行所在的預設帳戶為 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 上的 ASPNET 或 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 上的 NETWORK SERVICE，該帳戶根據預設無法存取私密金鑰檔案。</span><span class="sxs-lookup"><span data-stu-id="6199d-115">When running a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service under Internet Information Services (IIS) the default accounts that the service runs under are the ASPNET on [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or the NETWORK SERVICE on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], which by default do not have access to the private key file.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6199d-116">範例</span><span class="sxs-lookup"><span data-stu-id="6199d-116">Examples</span></span>  
 <span data-ttu-id="6199d-117">存取處理序沒有讀取權限的憑證時，您會看到類似下列範例的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="6199d-117">When accessing a certificate for which the process does not have read privilege, you see an exception message similar to the following example.</span></span>  
  
```  
System.ArgumentException was unhandled  
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."  
Source="System.ServiceModel"  
```  
  
 <span data-ttu-id="6199d-118">發生這種情況時，請使用 FindPrivateKey 工具尋找私密金鑰檔案，然後為服務執行所在的處理序設定存取權限。</span><span class="sxs-lookup"><span data-stu-id="6199d-118">When this occurs use the FindPrivateKey tool to find the private key file and then set the access right for the process that the service is running under.</span></span> <span data-ttu-id="6199d-119">例如，使用 Cacls.exe 工具完成此操作，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="6199d-119">For example, this can be done with the Cacls.exe tool as shown in the following example.</span></span>  
  
```  
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R  
```  
  
#### <a name="to-build-the-findprivatekey-project"></a><span data-ttu-id="6199d-120">若要建置 FindPrivateKey 專案</span><span class="sxs-lookup"><span data-stu-id="6199d-120">To build the FindPrivateKey project</span></span>  
  
1.  <span data-ttu-id="6199d-121">開啟 [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]，並巡覽至安裝範例所在目錄位置下的語言特定子目錄。</span><span class="sxs-lookup"><span data-stu-id="6199d-121">Open [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] and navigate to the language-specific subdirectory under the directory location where you installed the sample.</span></span>  
  
2.  <span data-ttu-id="6199d-122">按兩下 .sln 檔案圖示，在 Visual Studio 中開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="6199d-122">Double-click the .sln file icon to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="6199d-123">在**建置**功能表上，選取**重建方案**。</span><span class="sxs-lookup"><span data-stu-id="6199d-123">In the **Build** menu, select **Rebuild Solution**.</span></span> <span data-ttu-id="6199d-124">用戶端程式檔會建置至 client\bin，服務程式檔則建置至 service\bin。</span><span class="sxs-lookup"><span data-stu-id="6199d-124">The client program files are built to client\bin and the service program files are built to service\bin.</span></span>  
  
4.  <span data-ttu-id="6199d-125">建置方案會產生檔案 FindPrivateKey.exe。</span><span class="sxs-lookup"><span data-stu-id="6199d-125">Building the solution generates the file: FindPrivateKey.exe.</span></span>  
  
## <a name="conventionscommand-line-entries"></a><span data-ttu-id="6199d-126">慣例—命令列項目</span><span class="sxs-lookup"><span data-stu-id="6199d-126">Conventions—Command-Line Entries</span></span>  
 <span data-ttu-id="6199d-127">"[*選項*]"代表一組選擇性的參數。</span><span class="sxs-lookup"><span data-stu-id="6199d-127">"[*option*]" represents an optional set of parameters.</span></span>  
  
 <span data-ttu-id="6199d-128">"{*選項*}"代表強制的參數組。</span><span class="sxs-lookup"><span data-stu-id="6199d-128">"{*option*}" represents a mandatory set of parameters.</span></span>  
  
 <span data-ttu-id="6199d-129">「*選項 1* &#124;*選項 2*"表示的選項集之間的選擇。</span><span class="sxs-lookup"><span data-stu-id="6199d-129">"*option1* &#124; *option2*" represents a choice between sets of options.</span></span>  
  
 <span data-ttu-id="6199d-130">「\<*值*> 」 表示輸入參數值。</span><span class="sxs-lookup"><span data-stu-id="6199d-130">"\<*value*>" represents a parameter value to be entered.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="6199d-131">使用方式</span><span class="sxs-lookup"><span data-stu-id="6199d-131">Usage</span></span>  
  
```  
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]  
```  
  
 <span data-ttu-id="6199d-132">其中：</span><span class="sxs-lookup"><span data-stu-id="6199d-132">Where:</span></span>  
  
```  
       <subjectName> The subject name of the certificate  
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)  
       -f            output file name only  
       -d            output directory only  
       -a            output absolute file name  
```  
  
 <span data-ttu-id="6199d-133">如果未在命令提示字元中指定參數，則會顯示此說明文字。</span><span class="sxs-lookup"><span data-stu-id="6199d-133">If no parameters are specified at the command prompt then this help text is displayed.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6199d-134">範例</span><span class="sxs-lookup"><span data-stu-id="6199d-134">Examples</span></span>  
 <span data-ttu-id="6199d-135">這個範例會在 Current User.FindPrivateKey My CurrentUser -n "CN=localhost" 的 Personal 存放區中尋找主體名稱為 "CN=localhost" 之憑證的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6199d-135">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current User.FindPrivateKey My CurrentUser -n "CN=localhost".</span></span>  
  
 <span data-ttu-id="6199d-136">這個範例會在 Current 的 Personal 存放區中尋找主體名稱為 "CN=localhost" 之憑證的檔案名稱，並且輸出完整的目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="6199d-136">This example finds the filename of the certificate with a subject name of "CN=localhost", in the Personal store of the Current and output the full directory path.</span></span>  
  
```  
User.FindPrivateKey My CurrentUser -n "CN=localhost" -a  
```  
  
 <span data-ttu-id="6199d-137">這個範例會在 Local Computer 的 Personal 存放區中尋找指紋為 "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" 之憑證的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="6199d-137">This example finds the filename of the certificate with a thumbprint of "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52", in the Personal store of the Local Computer.</span></span>  
  
```  
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" –c  
```  
  
## <a name="see-also"></a><span data-ttu-id="6199d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6199d-138">See Also</span></span>
