---
title: 作法：偵測有無安裝 .NET Framework 3.0
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: e307125a2a8de3edc4df2fc1022c6e3de1904879
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960248"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="d13bf-102">HOW TO：偵測有無安裝 .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="d13bf-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="d13bf-103">在系統管理員可以將 Microsoft .NET Framework 應用程式部署到系統之前, 他們必須先確認 .NET Framework 執行時間是否存在。</span><span class="sxs-lookup"><span data-stu-id="d13bf-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="d13bf-104">本主題提供以 HTML/JavaScript 撰寫的腳本, 可讓系統管理員用來判斷 .NET Framework 是否存在於系統上。</span><span class="sxs-lookup"><span data-stu-id="d13bf-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d13bf-105">如需有關安裝、部署和偵測 Microsoft .NET Framework 的詳細資訊, 請參閱[部署 microsoft .NET Framework 3.0 版](https://go.microsoft.com/fwlink/?LinkId=96739)中的討論。</span><span class="sxs-lookup"><span data-stu-id="d13bf-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](https://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="d13bf-106">偵測 ".NET CLR" 使用者代理字串</span><span class="sxs-lookup"><span data-stu-id="d13bf-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="d13bf-107">安裝 .NET Framework 時, MSI 會將 ".NET CLR" 和版本號碼新增至 UserAgent 字串。</span><span class="sxs-lookup"><span data-stu-id="d13bf-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="d13bf-108">下列範例顯示內嵌在簡單 HTML 網頁中的腳本。</span><span class="sxs-lookup"><span data-stu-id="d13bf-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="d13bf-109">腳本會搜尋 UserAgent 字串, 以判斷是否已安裝 .NET Framework, 並顯示搜尋結果的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="d13bf-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 <span data-ttu-id="d13bf-110">如果搜尋「.NET CLR」版本成功, 則會顯示下列類型的狀態訊息:</span><span class="sxs-lookup"><span data-stu-id="d13bf-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="d13bf-111">否則, 會顯示下列類型的狀態訊息:</span><span class="sxs-lookup"><span data-stu-id="d13bf-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
