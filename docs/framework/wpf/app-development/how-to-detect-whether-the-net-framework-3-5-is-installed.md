---
title: "如何：偵測有無安裝 .NET Framework 3.5 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵測 .NET Framework 3.5 安裝 [WPF]"
  - "偵測有無安裝 .NET Framework 3.5 [WPF]"
  - "判斷有無安裝 .NET Framework 3.5 [WPF]"
  - "驗證有無安裝 .NET Framework 3.5 [WPF]"
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 如何：偵測有無安裝 .NET Framework 3.5
系統管理員必須先確認 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 執行階段確實存在，然後才能在以 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 為目標的系統上部署 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)] 應用程式。  本主題提供以 HTML\/JavaScript 撰寫的指令碼，供系統管理員用來判斷系統上是否有 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]。  
  
> [!NOTE]
>  如需安裝、部署及偵測 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 的詳細資訊，請參閱[安裝.NET Framework](../../../../docs/framework/install/guide-for-developers.md)。  
  
## 範例  
 安裝 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] 時，MSI 會在 UserAgent 宇串中加入 ".NET CLR" 和版本號碼。  下列範例顯示內嵌在簡單 HTML 網頁中的指令碼。  這個指令碼會搜尋 UserAgent 字串，確定是否已安裝 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，並在搜尋結果中顯示狀態訊息。  
  
> [!NOTE]
>  這個指令碼是專為 Internet Explorer 而設計。  其他瀏覽器可能不會包含 UserAgent 字串中的 .NET CLR 資訊。  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
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
  
 如果搜尋 ".NET CLR " 版本成功，則會顯示下列類型的狀態訊息：  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 否則，便會出現下列類型的狀態訊息：  
  
 `This machine does not have the correct version of the .NET Framework 3.5.  The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## 請參閱  
 [偵測有無安裝 .NET Framework 3.0](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)