---
title: "如何：透過 FTP 上傳檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e40f17c5-dd12-4c62-9dbf-00ab491382dc
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0772e77d699d11e29d17770bb2c737247ed1771d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-upload-files-with-ftp"></a><span data-ttu-id="a4f3d-102">如何：透過 FTP 上傳檔案</span><span class="sxs-lookup"><span data-stu-id="a4f3d-102">How to: Upload Files with FTP</span></span>
<span data-ttu-id="a4f3d-103">這個範例示範如何將檔案上傳至 FTP 伺服器。</span><span class="sxs-lookup"><span data-stu-id="a4f3d-103">This sample shows how to upload a file to an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4f3d-104">範例</span><span class="sxs-lookup"><span data-stu-id="a4f3d-104">Example</span></span>  
  
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
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4f3d-105">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a4f3d-105">Compiling the Code</span></span>  
 <span data-ttu-id="a4f3d-106">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="a4f3d-106">This example requires:</span></span>  
  
-   <span data-ttu-id="a4f3d-107">對 **System.Net** 命名空間的參考。</span><span class="sxs-lookup"><span data-stu-id="a4f3d-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a4f3d-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="a4f3d-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="a4f3d-109">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="a4f3d-109">.NET Framework Security</span></span>
