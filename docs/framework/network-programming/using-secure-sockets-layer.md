---
title: 使用安全通訊端層
description: 深入瞭解 System.Net 和擴充類別如何使用安全通訊端層，為 .NET Framework 中的數個網路通訊協定加密連接。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: 67330962382e768849cbf67d5f412ea80f65569d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501985"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="0f2a4-103">使用安全通訊端層</span><span class="sxs-lookup"><span data-stu-id="0f2a4-103">Using Secure Sockets Layer</span></span>
<span data-ttu-id="0f2a4-104"><xref:System.Net> 類別會使用安全通訊端層 (SSL) 來加密數個網路通訊協定的連線。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-104">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="0f2a4-105">若為 HTTP 連線，<xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別會使用 SSL 來與支援 SSL 的 Web 主機通訊。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-105">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="0f2a4-106">決定使用 SSL 與否是 <xref:System.Net.WebRequest> 類別根據給定的 URI 來進行。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-106">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="0f2a4-107">如果 URI 開頭是 "https:"，則使用 SSL。如果 URI 開頭是 "http:"，則使用未加密的連線。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-107">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="0f2a4-108">若要搭配使用 SSL 與檔案傳輸通訊協定 (FTP)，請將 <xref:System.Net.FtpWebRequest.EnableSsl> 屬性設定為 true，才能呼叫 <xref:System.Net.FtpWebRequest.GetResponse>。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-108">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="0f2a4-109">同樣地，若要搭配使用 SSL 與簡易郵件傳輸通訊協定 (SMTP)，請將 <xref:System.Net.Mail.SmtpClient.EnableSsl> 屬性設定為 true，然後傳送電子郵件。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-109">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="0f2a4-110"><xref:System.Net.Security.SslStream> 類別提供 SSL 以資料流為基礎的抽象概念，並提供許多方式來設定 SSL 交握。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-110">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f2a4-111">範例</span><span class="sxs-lookup"><span data-stu-id="0f2a4-111">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="0f2a4-112">程式碼</span><span class="sxs-lookup"><span data-stu-id="0f2a4-112">Code</span></span>  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0f2a4-113">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="0f2a4-113">Compiling the Code</span></span>  
 <span data-ttu-id="0f2a4-114">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="0f2a4-114">This example requires:</span></span>  
  
- <span data-ttu-id="0f2a4-115">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="0f2a4-115">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f2a4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f2a4-116">See also</span></span>

- [<span data-ttu-id="0f2a4-117">網路程式設計的安全性</span><span class="sxs-lookup"><span data-stu-id="0f2a4-117">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="0f2a4-118">.NET Framework 中的網路程式設計</span><span class="sxs-lookup"><span data-stu-id="0f2a4-118">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="0f2a4-119">憑證的選取和驗證</span><span class="sxs-lookup"><span data-stu-id="0f2a4-119">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
