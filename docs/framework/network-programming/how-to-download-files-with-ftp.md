---
title: "如何：透過 FTP 下載檔案 | Microsoft Docs"
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
ms.assetid: 892548b8-954a-4f6a-9bca-2ae620c3700f
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# 如何：透過 FTP 下載檔案
這個範例顯示如何從 FTP 伺服器下載的檔案。  
  
## 範例  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Get the object used to communicate with the server.  
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/test.htm");  
            request.Method = WebRequestMethods.Ftp.DownloadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Download Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();    
        }  
    }  
}  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   為 **System.Net** 命名空間的參考。  
  
## 穩固程式設計  
  
## .NET Framework 安全性