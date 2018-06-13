---
title: 如何：偵測有無安裝 .NET Framework 3.0
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 09de427980ecfb515b8d341d0d7833b878140286
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546487"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="b5987-102">如何：偵測有無安裝 .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="b5987-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="b5987-103">系統管理員可以部署的系統上的 Microsoft.NET Framework 應用程式之前，他們必須先確認.NET Framework 執行階段已存在。</span><span class="sxs-lookup"><span data-stu-id="b5987-103">Before administrators can deploy Microsoft .NET Framework applications on a system, they must first confirm that the .NET Framework runtime is present.</span></span> <span data-ttu-id="b5987-104">本主題提供以 HTML/JavaScript 撰寫的指令碼的系統管理員可用來判斷.NET Framework 是否存在於系統上。</span><span class="sxs-lookup"><span data-stu-id="b5987-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the .NET Framework is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5987-105">如需詳細資訊，在安裝時，部署和偵測 Microsoft.NET Framework，請參閱[部署 Microsoft.NET Framework 3.0](http://go.microsoft.com/fwlink/?LinkId=96739)。</span><span class="sxs-lookup"><span data-stu-id="b5987-105">For more detailed information on installing, deploying, and detecting the Microsoft .NET Framework, see the discussion in [Deploying Microsoft .NET Framework Version 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="b5987-106">偵測 「.NET CLR"使用者代理字串</span><span class="sxs-lookup"><span data-stu-id="b5987-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="b5987-107">安裝.NET Framework 時，MSI 加入 「.NET CLR"，版本號碼的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="b5987-107">When .NET Framework is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="b5987-108">下列範例顯示簡單的 HTML 網頁中內嵌的指令碼。</span><span class="sxs-lookup"><span data-stu-id="b5987-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="b5987-109">指令碼會搜尋要判斷.NET Framework 是否已安裝，且在搜尋結果中顯示狀態訊息的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="b5987-109">The script searches the UserAgent string to determine whether .NET Framework is installed, and displays a status message on the results of the search.</span></span>  
  
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
  
 <span data-ttu-id="b5987-110">如果 「.NET CLR"版本的搜尋成功，則會出現下列類型的狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="b5987-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="b5987-111">否則，就會出現下列類型的狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="b5987-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
