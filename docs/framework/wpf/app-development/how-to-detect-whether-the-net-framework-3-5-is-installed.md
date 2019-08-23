---
title: HOW TO：偵測有無安裝 .NET Framework 3.5
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 220fb3236786eb894bb78d12104025d24c9876ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960899"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>HOW TO：偵測有無安裝 .NET Framework 3.5
在系統管理員可以將 Windows Presentation Foundation (WPF) 應用程式部署到以 .NET Framework 3.5 為目標的系統之前, 他們必須先確認是否有 .NET Framework 3.5 執行時間。 本主題提供以 HTML/JavaScript 撰寫的腳本, 可讓系統管理員用來判斷系統上是否有 .NET Framework 3.5。  
  
> [!NOTE]
> 如需有關安裝、部署和偵測 .NET Framework 的詳細資訊, 請參閱[為開發人員安裝 .NET Framework](../../install/guide-for-developers.md)。  
  
## <a name="example"></a>範例  
 安裝 .NET Framework 3.5 時, MSI 會將 ".NET CLR" 和版本號碼新增至 UserAgent 字串。 下列範例顯示內嵌在簡單 HTML 網頁中的腳本。 腳本會搜尋 UserAgent 字串, 以判斷是否已安裝 .NET Framework 3.5, 並顯示搜尋結果的狀態訊息。  
  
> [!NOTE]
> 此腳本是針對 Internet Explorer 所設計。 其他瀏覽器可能不會在 UserAgent 字串中包含 .NET CLR 資訊。  
  
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
  
 如果搜尋「.NET CLR」版本成功, 則會顯示下列類型的狀態訊息:  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 否則, 會顯示下列類型的狀態訊息:  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>另請參閱

- [偵測有無安裝 .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
