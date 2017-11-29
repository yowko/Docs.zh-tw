---
title: "如何：以 FTP 列出目錄內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f5f74b215fb753d8d5a12a3e203b8598fc258053
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-list-directory-contents-with-ftp"></a><span data-ttu-id="d7372-102">如何：以 FTP 列出目錄內容</span><span class="sxs-lookup"><span data-stu-id="d7372-102">How to: List Directory Contents with FTP</span></span>
<span data-ttu-id="d7372-103">這個範例示範如何列出 FTP 伺服器的目錄內容。</span><span class="sxs-lookup"><span data-stu-id="d7372-103">This sample shows how to list the directory contents of an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7372-104">範例</span><span class="sxs-lookup"><span data-stu-id="d7372-104">Example</span></span>  
  
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
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/");  
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Directory List Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7372-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="d7372-105">Compiling the Code</span></span>  
 <span data-ttu-id="d7372-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="d7372-106">This example requires:</span></span>  
  
-   <span data-ttu-id="d7372-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="d7372-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d7372-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="d7372-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d7372-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="d7372-109">.NET Framework Security</span></span>
