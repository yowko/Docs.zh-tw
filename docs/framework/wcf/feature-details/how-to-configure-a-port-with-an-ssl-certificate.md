---
title: 作法：使用 SSL 憑證設定連接埠
description: 瞭解如何設定具有 x.509 憑證的埠，這是使用傳輸安全性的 WSHttpBinding 類別所需的自我裝載 WCF 服務所需的憑證。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 619a893e0973f6691e32446d75f101201a0b6799
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556378"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="75e39-103">作法：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="75e39-103">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="75e39-104">使用使用傳輸安全性的類別來建立自我裝載的 Windows Communication Foundation (WCF) 服務時 <xref:System.ServiceModel.WSHttpBinding> ，您也必須使用 x.509 憑證來設定埠。</span><span class="sxs-lookup"><span data-stu-id="75e39-104">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="75e39-105">如果您沒有建立自我裝載的服務，可以將您的服務裝載在 Internet Information Services (IIS) 上。</span><span class="sxs-lookup"><span data-stu-id="75e39-105">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="75e39-106">如需詳細資訊，請參閱 [HTTP 傳輸安全性](http-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="75e39-106">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="75e39-107">若要設定連接埠，使用的工具取決於電腦上執行的作業系統。</span><span class="sxs-lookup"><span data-stu-id="75e39-107">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="75e39-108">如果您正在執行 Windows Server 2003，請使用 HttpCfg.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="75e39-108">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="75e39-109">在 Windows Server 2003 上，已安裝此工具。</span><span class="sxs-lookup"><span data-stu-id="75e39-109">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="75e39-110">如需詳細資訊，請參閱 [Httpcfg.exe 總覽](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="75e39-110">For more information, see [Httpcfg Overview](/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="75e39-111">[Windows 支援工具檔](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10))說明 Httpcfg.exe 工具的語法。</span><span class="sxs-lookup"><span data-stu-id="75e39-111">The [Windows Support Tools documentation](/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="75e39-112">如果您執行的是 Windows Vista，請使用已安裝的 Netsh.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="75e39-112">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="75e39-113">修改電腦上儲存的憑證需要系統管理許可權。</span><span class="sxs-lookup"><span data-stu-id="75e39-113">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="75e39-114">判斷如何設定埠</span><span class="sxs-lookup"><span data-stu-id="75e39-114">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="75e39-115">在 Windows Server 2003 或 Windows XP 中，請使用 HttpCfg.exe 工具，使用 **查詢** 和 **ssl** 參數來查看目前的埠設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-115">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="75e39-116">在 Windows Vista 中，使用 Netsh.exe 工具來查看目前的埠設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-116">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="75e39-117">取得憑證的指紋</span><span class="sxs-lookup"><span data-stu-id="75e39-117">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="75e39-118">使用憑證 MMC 嵌入式管理單元，尋找目的為用戶端驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="75e39-118">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="75e39-119">如需詳細資訊，請參閱 [做法：使用 MMC 嵌入式管理單元檢視憑證](how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="75e39-119">For more information, see [How to: View Certificates with the MMC Snap-in](how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="75e39-120">存取憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="75e39-120">Access the certificate's thumbprint.</span></span> <span data-ttu-id="75e39-121">如需詳細資訊，請參閱[做法：擷取憑證的指紋](how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="75e39-121">For more information, see [How to: Retrieve the Thumbprint of a Certificate](how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="75e39-122">將憑證的指紋複製到文字編輯器中，例如「記事本」。</span><span class="sxs-lookup"><span data-stu-id="75e39-122">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="75e39-123">移除十六進位字元之間的所有空格。</span><span class="sxs-lookup"><span data-stu-id="75e39-123">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="75e39-124">完成這項工作的方法之一是使用文字編輯器的尋找與取代功能，並使用 null 字元來取代各個空格。</span><span class="sxs-lookup"><span data-stu-id="75e39-124">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="75e39-125">將 SSL 憑證系結至埠號碼</span><span class="sxs-lookup"><span data-stu-id="75e39-125">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="75e39-126">在 Windows Server 2003 或 Windows XP 中，請使用安全通訊端層 (SSL) 存放區上「設定」模式中的 HttpCfg.exe 工具，將憑證系結至埠號碼。</span><span class="sxs-lookup"><span data-stu-id="75e39-126">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="75e39-127">此工具是使用指紋來識別憑證，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-127">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="75e39-128">**-I**參數的語法為 `IP` ： `port` ，並指示工具將憑證設定為電腦的埠8012。</span><span class="sxs-lookup"><span data-stu-id="75e39-128">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="75e39-129">或者，號碼前面的四個零也可以使用電腦的實際 IP 位址來取代。</span><span class="sxs-lookup"><span data-stu-id="75e39-129">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="75e39-130">**-H**參數會指定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="75e39-130">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="75e39-131">在 Windows Vista 中，請使用 Netsh.exe 工具，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-131">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="75e39-132">**Certhash**參數會指定憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="75e39-132">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="75e39-133">**Ipport**參數會指定 IP 位址和埠，以及與所述 Httpcfg.exe 工具的 **-i**參數一樣的函式。</span><span class="sxs-lookup"><span data-stu-id="75e39-133">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="75e39-134">**Appid**參數是一種 GUID，可用來識別擁有應用程式。</span><span class="sxs-lookup"><span data-stu-id="75e39-134">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="75e39-135">將 SSL 憑證系結至埠號碼，並支援用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="75e39-135">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="75e39-136">在 Windows Server 2003 或 Windows XP 中，為了支援在傳輸層以 x.509 憑證進行驗證的用戶端，請遵循上述程式，但是將額外的命令列參數傳遞至 HttpCfg.exe，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-136">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="75e39-137">**-F**參數具有的語法， `n` 其中 n 是介於1和7之間的數位。</span><span class="sxs-lookup"><span data-stu-id="75e39-137">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="75e39-138">值為 2 (如上一個範例所示) 會在傳輸層啟用用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="75e39-138">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="75e39-139">值為 3 會啟用用戶端憑證，並將這些憑證對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="75e39-139">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="75e39-140">如需其他值的行為，請參閱 HttpCfg.exe 說明。</span><span class="sxs-lookup"><span data-stu-id="75e39-140">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="75e39-141">在 Windows Vista 中，為了支援在傳輸層以 x.509 憑證進行驗證的用戶端，請遵循上述程式，但使用額外的參數，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-141">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="75e39-142">從埠號碼刪除 SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="75e39-142">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="75e39-143">使用 HttpCfg.exe 或 Netsh.exe 工具來查看電腦上所有繫結的連接埠和指紋。</span><span class="sxs-lookup"><span data-stu-id="75e39-143">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="75e39-144">若要將資訊列印到磁片，請使用重新導向字元 ">"，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-144">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="75e39-145">在 Windows Server 2003 或 Windows XP 中，請使用 HttpCfg.exe 工具搭配 **delete** 和 **ssl** 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="75e39-145">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="75e39-146">使用 **-i** 參數來指定 `IP` ： `port` 號碼，並使用 **-h** 參數來指定指紋。</span><span class="sxs-lookup"><span data-stu-id="75e39-146">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="75e39-147">在 Windows Vista 中，請使用 Netsh.exe 工具，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="75e39-147">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="75e39-148">範例</span><span class="sxs-lookup"><span data-stu-id="75e39-148">Example</span></span>  

 <span data-ttu-id="75e39-149">下列程式碼將示範如何使用設定為傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別來建立自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="75e39-149">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="75e39-150">當建立應用程式時，請在位址中指定連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="75e39-150">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="75e39-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="75e39-151">See also</span></span>

- [<span data-ttu-id="75e39-152">HTTP 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="75e39-152">HTTP Transport Security</span></span>](http-transport-security.md)
