---
title: 如何：偵測有無安裝 .NET Framework 3.0
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 48295a187870340948b045a64b852f1e6fdc1a65
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a>如何：偵測有無安裝 .NET Framework 3.0
系統管理員可以部署之前[!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)]應用程式在系統上，他們必須先確認[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]執行階段會出現。 本主題提供撰寫的指令碼 HTML/javascript，系統管理員可以用來判斷是否[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]存在於系統上。  
  
> [!NOTE]
>  如需詳細資訊，在安裝時，部署和偵測 Microsoft.NET Framework，請參閱[部署 Microsoft.NET Framework 3.0](http://go.microsoft.com/fwlink/?LinkId=96739)。  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a>偵測 「.NET CLR"使用者代理字串  
 當[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]已安裝，MSI 新增 「.NET CLR"和版本號碼的使用者代理字串。 下列範例顯示簡單的 HTML 網頁中內嵌的指令碼。 指令碼搜尋使用者代理字串，以判斷是否[!INCLUDE[TLA2#tla_avalonwinfx](../../../../includes/tla2sharptla-avalonwinfx-md.md)]已安裝，且在搜尋結果中顯示狀態訊息。  
  
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
  
 如果 「.NET CLR"版本的搜尋成功，則會出現下列類型的狀態訊息：  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 否則，就會出現下列類型的狀態訊息：  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
