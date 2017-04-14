---
title: "使用安全通訊端層 | Microsoft Docs"
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
  - "網路"
  - "SSL"
  - "安全通訊端層"
  - "從網際網路要求資料，安全通訊端層"
  - "傳送資料，安全通訊端層"
  - "網路資源"
  - "資料要求，安全通訊端層"
  - "接收資料，安全通訊端層"
  - "網際網路，安全通訊端層"
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# 使用安全通訊端層
<xref:System.Net> 類別使用 Secure Sockets Layer \(SSL\) 加密幾個網路通訊協定的連接。  
  
 http 連接， <xref:System.Net.WebRequest> 和 <xref:System.Net.WebResponse> 類別搭配使用 SSL 與支援 SSL 的 Web 主機通訊。  使用 SSL 的決策提供給它的 <xref:System.Net.WebRequest> 類別進行，依據 URI。  如果從 URI 「https 開始: 」，使用 SSL，如果從 URI 「http 開始: 」，使用未加密的連接。  
  
 若要使用檔案傳輸通訊協定 \(FTP\) \(FTP\) 的 SSL，請將 <xref:System.Net.FtpWebRequest.EnableSsl> 屬性在呼叫之前 <xref:System.Net.FtpWebRequest.GetResponse>true。  同樣地，搭配 Simple Mail Transport Protocol \(SMTP\) 的 SSL，請將 <xref:System.Net.Mail.SmtpClient.EnableSsl> 屬性在傳送電子郵件訊息之前則為 true。  
  
 <xref:System.Net.Security.SslStream> 類別為 SSL 之資料流的抽象概念，並提供許多設定 SSL 交換。  
  
## 範例  
  
### 程式碼  
  
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
  
## 編譯程式碼  
 這個範例需要：  
  
-   為 **System.Net** 命名空間的參考。  
  
## 請參閱  
 [網路程式設計的安全性](../../../docs/framework/network-programming/security-in-network-programming.md)   
 [以 .NET Framework 進行網路程式設計](../../../docs/framework/network-programming/index.md)   
 [憑證的選取和驗證](../../../docs/framework/network-programming/certificate-selection-and-validation.md)