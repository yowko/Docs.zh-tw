---
title: "FTP | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "FTP"
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# FTP
.NET Framework 使用 FTP 通訊協定提供廣泛的支援。 <xref:System.Net.FtpWebRequest> 和 <xref:System.Net.FtpWebResponse> 類別。  這些類別是從 <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse>衍生。  在許多情況下， <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別提供所有必要提出要求，，不過，如果您需要為屬性所公開的 FTP 特定功能的存取權，可能會將角色這些類別加入至 <xref:System.Net.FtpWebRequest> 或 <xref:System.Net.FtpWebResponse>。  
  
## 範例  
 如需詳細資訊，請參閱下列主題: [如何：透過 FTP 下載檔案](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md)、 [如何：透過 FTP 上傳檔案](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md)和 [如何：以 FTP 列出目錄內容](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md)。  
  
## FTP 和 Proxy  
 如果 Proxy \(由屬性 <xref:System.Net.FtpWebRequest.Proxy%2A> \) 是 HTTP Proxy，則 <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>、 <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>和只 <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> 命令支援。  
  
## 請參閱  
 [透過 Proxy 存取網際網路](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)   
 [網路程式設計範例](../../../docs/framework/network-programming/network-programming-samples.md)   
 [FTP 用戶端技術範例](http://go.microsoft.com/fwlink/?LinkID=179557)   
 [FTP 總管技術範例](http://go.microsoft.com/fwlink/?LinkID=179569)   
 [使用應用程式通訊協定](../../../docs/framework/network-programming/using-application-protocols.md)