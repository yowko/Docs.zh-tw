---
title: FTP
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e5dc6ee0f2c832e3274a1e58808acfdb56ae804c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862974"
---
# <a name="ftp"></a>FTP
.NET Framework 使用 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別提供 FTP 通訊協定的完整支援。 這些類別衍生自 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>。 在大部分情況下，<xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別提供提出要求所需的一切功能，但是如果您需要存取以屬性方式公開的 FTP 特定功能，則可以將這些類別的類型轉換為 <xref:System.Net.FtpWebRequest> 或 <xref:System.Net.FtpWebResponse>。  
  
## <a name="examples"></a>範例  
 如需詳細資訊，請參閱下列主題：[如何：透過 FTP 下載檔案](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md)、[如何：透過 FTP 上傳檔案](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md)和[如何：以 FTP 列出目錄內容](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md)。  
  
## <a name="ftp-and-proxies"></a>FTP 和 Proxy  
 如果 Proxy (透過 <xref:System.Net.FtpWebRequest.Proxy%2A> 屬性所指定) 是 HTTP Proxy，則只支援 <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、<xref:System.Net.WebRequestMethods.Ftp.ListDirectory> 和 <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> 命令。  
  
## <a name="see-also"></a>請參閱  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)  
 [FTP 用戶端技術範例](https://go.microsoft.com/fwlink/?LinkID=179557)  
 [FTP 總管技術範例](https://go.microsoft.com/fwlink/?LinkID=179569)  
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)
