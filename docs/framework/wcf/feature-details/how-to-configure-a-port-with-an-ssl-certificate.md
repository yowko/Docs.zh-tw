---
title: HOW TO：使用 SSL 憑證設定連接埠
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SSL
- WCF, security mode
- WCF, security
ms.assetid: b8abcc8e-a5f5-4317-aca5-01e3c40ab24d
ms.openlocfilehash: 90d5424e12bb770dc3da85e1b2738206f4777c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185100"
---
# <a name="how-to-configure-a-port-with-an-ssl-certificate"></a><span data-ttu-id="2ccf7-102">HOW TO：使用 SSL 憑證設定連接埠</span><span class="sxs-lookup"><span data-stu-id="2ccf7-102">How to: Configure a Port with an SSL Certificate</span></span>

<span data-ttu-id="2ccf7-103">使用使用傳輸安全性<xref:System.ServiceModel.WSHttpBinding>的類創建自託管的 Windows 通信基礎 （WCF） 服務時，還必須配置具有 X.509 憑證的埠。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-103">When creating a self-hosted Windows Communication Foundation (WCF) service with the <xref:System.ServiceModel.WSHttpBinding> class that uses transport security, you must also configure a port with an X.509 certificate.</span></span> <span data-ttu-id="2ccf7-104">如果您沒有建立自我裝載的服務，可以將您的服務裝載在 Internet Information Services (IIS) 上。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-104">If you are not creating a self-hosted service, you can host your service on Internet Information Services (IIS).</span></span> <span data-ttu-id="2ccf7-105">有關詳細資訊，請參閱[HTTP 傳輸安全](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-105">For more information, see [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).</span></span>  
  
 <span data-ttu-id="2ccf7-106">若要設定連接埠，使用的工具取決於電腦上執行的作業系統。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-106">To configure a port, the tool you use depends on the operating system that is running on your machine.</span></span>  
  
 <span data-ttu-id="2ccf7-107">如果您正在運行 Windows Server 2003，請使用 HttpCfg.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-107">If you are running Windows Server 2003, use the HttpCfg.exe tool.</span></span> <span data-ttu-id="2ccf7-108">在 Windows 伺服器 2003 上，將安裝此工具。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-108">On Windows Server 2003, this tool is installed.</span></span> <span data-ttu-id="2ccf7-109">有關詳細資訊，請參閱[Httpcfg 概述](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10))。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-109">For more information, see [Httpcfg Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc787508(v=ws.10)).</span></span> <span data-ttu-id="2ccf7-110">[Windows 支援工具文檔](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10))解釋了 Httpcfg.exe 工具的語法。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-110">The [Windows Support Tools documentation](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc781601(v=ws.10)) explains the syntax for the Httpcfg.exe tool.</span></span>  
  
 <span data-ttu-id="2ccf7-111">如果您正在運行 Windows Vista，請使用已安裝的 Netsh.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-111">If you are running Windows Vista, use the Netsh.exe tool that is already installed.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2ccf7-112">修改存儲在電腦上的證書需要管理許可權。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-112">Modifying certificates stored on the computer requires administrative privileges.</span></span>  
  
## <a name="determine-how-ports-are-configured"></a><span data-ttu-id="2ccf7-113">確定埠的配置方式</span><span class="sxs-lookup"><span data-stu-id="2ccf7-113">Determine how ports are configured</span></span>  
  
1. <span data-ttu-id="2ccf7-114">在 Windows 伺服器 2003 或 Windows XP 中，使用 HttpCfg.exe 工具使用**查詢**和**ssl**開關查看當前埠配置，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-114">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool to view the current port configuration, using the **query** and **ssl** switches, as shown in the following example.</span></span>  
  
    ```console
    httpcfg query ssl  
    ```  
  
2. <span data-ttu-id="2ccf7-115">在 Windows Vista 中，使用 Netsh.exe 工具查看當前埠配置，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-115">In Windows Vista, use the Netsh.exe tool to view the current port configuration, as shown in the following example.</span></span>  
  
    ```console  
    netsh http show sslcert  
    ```  
  
## <a name="get-a-certificates-thumbprint"></a><span data-ttu-id="2ccf7-116">獲取證書的指紋</span><span class="sxs-lookup"><span data-stu-id="2ccf7-116">Get a certificate's thumbprint</span></span>  
  
1. <span data-ttu-id="2ccf7-117">使用憑證 MMC 嵌入式管理單元，尋找目的為用戶端驗證的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-117">Use the Certificates MMC snap-in to find an X.509 certificate that has an intended purpose of client authentication.</span></span> <span data-ttu-id="2ccf7-118">如需詳細資訊，請參閱 [做法：使用 MMC 嵌入式管理單元檢視憑證](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-118">For more information, see [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).</span></span>  
  
2. <span data-ttu-id="2ccf7-119">存取憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-119">Access the certificate's thumbprint.</span></span> <span data-ttu-id="2ccf7-120">如需詳細資訊，請參閱[做法：擷取憑證的指紋](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-120">For more information, see [How to: Retrieve the Thumbprint of a Certificate](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).</span></span>  
  
3. <span data-ttu-id="2ccf7-121">將憑證的指紋複製到文字編輯器中，例如「記事本」。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-121">Copy the thumbprint of the certificate into a text editor, such as Notepad.</span></span>  
  
4. <span data-ttu-id="2ccf7-122">移除十六進位字元之間的所有空格。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-122">Remove all spaces between the hexadecimal characters.</span></span> <span data-ttu-id="2ccf7-123">完成這項工作的方法之一是使用文字編輯器的尋找與取代功能，並使用 null 字元來取代各個空格。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-123">One way to accomplish this is to use the text editor's find-and-replace feature and replace each space with a null character.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number"></a><span data-ttu-id="2ccf7-124">將 SSL 憑證綁定到埠號</span><span class="sxs-lookup"><span data-stu-id="2ccf7-124">Bind an SSL certificate to a port number</span></span>  
  
1. <span data-ttu-id="2ccf7-125">在 Windows 伺服器 2003 或 Windows XP 中，在安全通訊端層 （SSL） 存儲的"設置"模式下使用 HttpCfg.exe 工具將證書綁定到埠號。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-125">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool in "set" mode on the Secure Sockets Layer (SSL) store to bind the certificate to a port number.</span></span> <span data-ttu-id="2ccf7-126">此工具是使用指紋來識別憑證，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-126">The tool uses the thumbprint to identify the certificate, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
    - <span data-ttu-id="2ccf7-127">**-i**開關的語法為`IP`：`port`並指示工具將證書設置為電腦的埠 8012。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-127">The **-i** switch has the syntax of `IP`:`port` and instructs the tool to set the certificate to port 8012 of the computer.</span></span> <span data-ttu-id="2ccf7-128">或者，號碼前面的四個零也可以使用電腦的實際 IP 位址來取代。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-128">Optionally, the four zeroes that precede the number can also be replaced by the actual IP address of the computer.</span></span>  
  
    - <span data-ttu-id="2ccf7-129">**-h**開關指定證書的指紋。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-129">The **-h** switch specifies the thumbprint of the certificate.</span></span>  
  
2. <span data-ttu-id="2ccf7-130">在 Windows Vista 中，請使用 Netsh.exe 工具，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-130">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF}
    ```  
  
    - <span data-ttu-id="2ccf7-131">**證書**參數指定證書的指紋。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-131">The **certhash** parameter specifies the thumbprint of the certificate.</span></span>  
  
    - <span data-ttu-id="2ccf7-132">**ipport**參數指定 IP 位址和埠，其功能與描述的 Httpcfg.exe 工具的 **-i**開關類似。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-132">The **ipport** parameter specifies the IP address and port, and functions just like the **-i** switch of the Httpcfg.exe tool described.</span></span>  
  
    - <span data-ttu-id="2ccf7-133">**appid**參數是一個 GUID，可用於標識所屬應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-133">The **appid** parameter is a GUID that can be used to identify the owning application.</span></span>  
  
## <a name="bind-an-ssl-certificate-to-a-port-number-and-support-client-certificates"></a><span data-ttu-id="2ccf7-134">將 SSL 憑證綁定到埠號並支援用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="2ccf7-134">Bind an SSL certificate to a port number and support client certificates</span></span>  
  
1. <span data-ttu-id="2ccf7-135">在 Windows Server 2003 或 Windows XP 中，為了支援在傳輸層使用 X.509 憑證進行身份驗證的用戶端，請按照上述過程操作，但將附加命令列參數傳遞給 HttpCfg.exe，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-135">In Windows Server 2003 or Windows XP, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure but pass an additional command-line parameter to HttpCfg.exe, as shown in the following example.</span></span>  
  
    ```console  
    httpcfg set ssl -i 0.0.0.0:8012 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6 -f 2  
    ```  
  
     <span data-ttu-id="2ccf7-136">**-f**開關的語法`n`是 n 是介於 1 和 7 之間的數位。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-136">The **-f** switch has the syntax of `n` where n is a number between 1 and 7.</span></span> <span data-ttu-id="2ccf7-137">值為 2 (如上一個範例所示) 會在傳輸層啟用用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-137">A value of 2, as shown in the preceding example, enables client certificates at the transport layer.</span></span> <span data-ttu-id="2ccf7-138">值為 3 會啟用用戶端憑證，並將這些憑證對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-138">A value of 3 enables client certificates and maps those certificates to a Windows account.</span></span> <span data-ttu-id="2ccf7-139">如需其他值的行為，請參閱 HttpCfg.exe 說明。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-139">See HttpCfg.exe Help for the behavior of other values.</span></span>  
  
2. <span data-ttu-id="2ccf7-140">在 Windows Vista 中，為了支援在傳輸層使用 X.509 憑證進行身份驗證的用戶端，請遵循前面的過程，但使用附加參數，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-140">In Windows Vista, to support clients that authenticate with X.509 certificates at the transport layer, follow the preceding procedure, but with an additional parameter, as shown in the following example.</span></span>  
  
    ```console  
    netsh http add sslcert ipport=0.0.0.0:8000 certhash=0000000000003ed9cd0c315bbb6dc1c08da5e6 appid={00112233-4455-6677-8899-AABBCCDDEEFF} clientcertnegotiation=enable  
    ```  
  
## <a name="delete-an-ssl-certificate-from-a-port-number"></a><span data-ttu-id="2ccf7-141">從埠號中刪除 SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="2ccf7-141">Delete an SSL certificate from a port number</span></span>  
  
1. <span data-ttu-id="2ccf7-142">使用 HttpCfg.exe 或 Netsh.exe 工具來查看電腦上所有繫結的連接埠和指紋。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-142">Use the HttpCfg.exe or Netsh.exe tool to see the ports and thumbprints of all bindings on the computer.</span></span> <span data-ttu-id="2ccf7-143">要將資訊列印到磁片，請使用重定向字元">"，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-143">To print the information to disk, use the redirection character ">", as shown in the following example.</span></span>  
  
    ```console  
    httpcfg query ssl>myMachinePorts.txt  
    ```
  
2. <span data-ttu-id="2ccf7-144">在 Windows 伺服器 2003 或 Windows XP 中，使用 HttpCfg.exe 工具**刪除和\*\*\*\*ssl**關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-144">In Windows Server 2003 or Windows XP, use the HttpCfg.exe tool with the **delete** and **ssl** keywords.</span></span> <span data-ttu-id="2ccf7-145">使用 **-i**開關指定`IP`：`port`編號和 **-h**開關來指定指紋。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-145">Use the **-i** switch to specify the `IP`:`port` number, and the **-h** switch to specify the thumbprint.</span></span>  
  
    ```console  
    httpcfg delete ssl -i 0.0.0.0:8005 -h 0000000000003ed9cd0c315bbb6dc1c08da5e6  
    ```  
  
3. <span data-ttu-id="2ccf7-146">在 Windows Vista 中，請使用 Netsh.exe 工具，如以下示例所示。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-146">In Windows Vista, use the Netsh.exe tool, as shown in the following example.</span></span>  
  
    ```console  
    Netsh http delete sslcert ipport=0.0.0.0:8005  
    ```  
  
## <a name="example"></a><span data-ttu-id="2ccf7-147">範例</span><span class="sxs-lookup"><span data-stu-id="2ccf7-147">Example</span></span>  

 <span data-ttu-id="2ccf7-148">下列程式碼將示範如何使用設定為傳輸安全性的 <xref:System.ServiceModel.WSHttpBinding> 類別來建立自我裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-148">The following code shows how to create a self-hosted service using the <xref:System.ServiceModel.WSHttpBinding> class set to transport security.</span></span> <span data-ttu-id="2ccf7-149">當建立應用程式時，請在位址中指定連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="2ccf7-149">When creating an application, specify the port number in the address.</span></span>  
  
 [!code-csharp[c_WsHttpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#3)]
 [!code-vb[c_WsHttpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="2ccf7-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ccf7-150">See also</span></span>

- [<span data-ttu-id="2ccf7-151">HTTP 傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="2ccf7-151">HTTP Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/http-transport-security.md)
