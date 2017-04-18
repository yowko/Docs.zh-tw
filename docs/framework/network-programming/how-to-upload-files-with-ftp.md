---
title: "如何：透過 FTP 上傳檔案 | Microsoft Docs"
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
ms.assetid: e40f17c5-dd12-4c62-9dbf-00ab491382dc
caps.latest.revision: 5
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 5
---
# 如何：透過 FTP 上傳檔案
這個範例顯示如何將檔案上載至 FTP 伺服器。  
  
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
            request.Method = WebRequestMethods.Ftp.UploadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            // Copy the contents of the file to the request stream.  
            StreamReader sourceStream = new StreamReader("testfile.txt");  
            byte [] fileContents = Encoding.UTF8.GetBytes(sourceStream.ReadToEnd());  
            sourceStream.Close();  
            request.ContentLength = fileContents.Length;  
  
            Stream requestStream = request.GetRequestStream();  
            requestStream.Write(fileContents, 0, fileContents.Length);  
            requestStream.Close();  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Console.WriteLine("Upload File Complete, status {0}", response.StatusDescription);  
  
            response.Close();  
            }  
        }  
    }  
}  
```  
  
## 編譯程式碼  
 這個範例需要：  
  
-   為 **System.Net** 命名空間的參考。  
  
## 穩固程式設計  
  
## .NET Framework 安全性