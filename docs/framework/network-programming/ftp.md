---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 286ab6ad4742f3e31db8037e10e98d5890c6144d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47200915"
---
# <a name="ftp"></a><span data-ttu-id="09580-102">FTP</span><span class="sxs-lookup"><span data-stu-id="09580-102">FTP</span></span>
<span data-ttu-id="09580-103">.NET Framework 使用 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別提供 FTP 通訊協定的完整支援。</span><span class="sxs-lookup"><span data-stu-id="09580-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="09580-104">這些類別衍生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>。</span><span class="sxs-lookup"><span data-stu-id="09580-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="09580-105">在大部分情況下，<xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別提供提出要求所需的一切功能，但是如果您需要存取以屬性方式公開的 FTP 特定功能，則可以將這些類別的類型轉換為 <xref:System.Net.FtpWebRequest> 或 <xref:System.Net.FtpWebResponse>。</span><span class="sxs-lookup"><span data-stu-id="09580-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="09580-106">範例</span><span class="sxs-lookup"><span data-stu-id="09580-106">Examples</span></span>  
 <span data-ttu-id="09580-107">如需詳細資訊，請參閱下列主題：[如何：透過 FTP 下載檔案](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md)、[如何：透過 FTP 上傳檔案](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md)和[如何：以 FTP 列出目錄內容](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md)。</span><span class="sxs-lookup"><span data-stu-id="09580-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="09580-108">FTP 和 Proxy</span><span class="sxs-lookup"><span data-stu-id="09580-108">FTP and proxies</span></span>  
 <span data-ttu-id="09580-109">如果 Proxy (透過 <xref:System.Net.FtpWebRequest.Proxy%2A> 屬性所指定) 是 HTTP Proxy，則只支援 <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、<xref:System.Net.WebRequestMethods.Ftp.ListDirectory> 和 <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> 命令。</span><span class="sxs-lookup"><span data-stu-id="09580-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09580-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="09580-110">See Also</span></span>  
 [<span data-ttu-id="09580-111">透過 Proxy 存取網際網路</span><span class="sxs-lookup"><span data-stu-id="09580-111">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="09580-112">網路程式設計範例</span><span class="sxs-lookup"><span data-stu-id="09580-112">Network Programming Samples</span></span>](../../../docs/framework/network-programming/network-programming-samples.md)  
 [<span data-ttu-id="09580-113">FTP 用戶端技術範例</span><span class="sxs-lookup"><span data-stu-id="09580-113">FTP Client Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [<span data-ttu-id="09580-114">FTP 總管技術範例</span><span class="sxs-lookup"><span data-stu-id="09580-114">FTP Explorer Technology Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [<span data-ttu-id="09580-115">使用應用程式通訊協定</span><span class="sxs-lookup"><span data-stu-id="09580-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)
