---
title: "如何：偵測有無安裝 .NET Framework 3.0"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6990ca4bff7c8756f8d7f25ff0153b3a5d41a4f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a><span data-ttu-id="2b02e-102">如何：偵測有無安裝 .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="2b02e-102">How to: Detect Whether the .NET Framework 3.0 Is Installed</span></span>
<span data-ttu-id="2b02e-103">系統管理員可以部署之前[!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)]應用程式在系統上，他們必須先確認[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]執行階段會出現。</span><span class="sxs-lookup"><span data-stu-id="2b02e-103">Before administrators can deploy [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] applications on a system, they must first confirm that the [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] runtime is present.</span></span> <span data-ttu-id="2b02e-104">本主題提供撰寫的指令碼 HTML/javascript，系統管理員可以用來判斷是否[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]存在於系統上。</span><span class="sxs-lookup"><span data-stu-id="2b02e-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b02e-105">如需詳細資訊，在上安裝、 部署和偵測[!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)]，請參閱[部署 Microsoft.NET Framework 3.0](http://go.microsoft.com/fwlink/?LinkId=96739)。</span><span class="sxs-lookup"><span data-stu-id="2b02e-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[TLA#tla_winfx](../../../../includes/tlasharptla-winfx-md.md)], see the discussion in [Deploying Microsoft .NET Framework Version 3.0](http://go.microsoft.com/fwlink/?LinkId=96739).</span></span>  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a><span data-ttu-id="2b02e-106">偵測 「.NET CLR"使用者代理字串</span><span class="sxs-lookup"><span data-stu-id="2b02e-106">Detect the ".NET CLR" User-Agent String</span></span>  
 <span data-ttu-id="2b02e-107">當[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]已安裝，MSI 新增 「.NET CLR"和版本號碼的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="2b02e-107">When [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="2b02e-108">下列範例顯示簡單的 HTML 網頁中內嵌的指令碼。</span><span class="sxs-lookup"><span data-stu-id="2b02e-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="2b02e-109">指令碼搜尋使用者代理字串，以判斷是否[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]已安裝，且在搜尋結果中顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="2b02e-109">The script searches the UserAgent string to determine whether [!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
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
  
 <span data-ttu-id="2b02e-110">如果 「.NET CLR"版本的搜尋成功，則會出現下列類型的狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="2b02e-110">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 <span data-ttu-id="2b02e-111">否則，就會出現下列類型的狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="2b02e-111">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
