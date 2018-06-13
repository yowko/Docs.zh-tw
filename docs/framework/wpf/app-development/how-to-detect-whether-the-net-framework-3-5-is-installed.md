---
title: 如何： 偵測是否已安裝.NET Framework 3.5
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 0d0f99dfa88216d0d768895ea751b0f62eccf701
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546038"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a><span data-ttu-id="7e967-102">如何： 偵測是否已安裝.NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="7e967-102">How to: Detect Whether the .NET Framework 3.5 Is Installed</span></span>
<span data-ttu-id="7e967-103">系統管理員可以部署為目標的系統上的 Windows Presentation Foundation (WPF) 應用程式之前[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]，必須先確認，[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]執行階段會出現。</span><span class="sxs-lookup"><span data-stu-id="7e967-103">Before administrators can deploy Windows Presentation Foundation (WPF) applications on a system that targets the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)], they must first confirm that the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] runtime is present.</span></span> <span data-ttu-id="7e967-104">本主題提供撰寫的指令碼 HTML/javascript，系統管理員可以用來判斷是否[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]存在於系統上。</span><span class="sxs-lookup"><span data-stu-id="7e967-104">This topic provides a script written in HTML/JavaScript that administrators can use to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is present on a system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e967-105">如需詳細資訊，在上安裝、 部署和偵測[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]，請參閱[安裝.NET Framework 開發人員](../../../../docs/framework/install/guide-for-developers.md)。</span><span class="sxs-lookup"><span data-stu-id="7e967-105">For more detailed information on installing, deploying, and detecting the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], see [Install the .NET Framework for developers](../../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e967-106">範例</span><span class="sxs-lookup"><span data-stu-id="7e967-106">Example</span></span>  
 <span data-ttu-id="7e967-107">當[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]已安裝，MSI 新增 「.NET CLR"和版本號碼的使用者代理字串。</span><span class="sxs-lookup"><span data-stu-id="7e967-107">When the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, the MSI adds ".NET CLR" and the version number to the UserAgent string.</span></span> <span data-ttu-id="7e967-108">下列範例顯示簡單的 HTML 網頁中內嵌的指令碼。</span><span class="sxs-lookup"><span data-stu-id="7e967-108">The following example shows a script embedded in a simple HTML page.</span></span> <span data-ttu-id="7e967-109">指令碼搜尋使用者代理字串，以判斷是否[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]已安裝，且在搜尋結果中顯示狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="7e967-109">The script searches the UserAgent string to determine whether the [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)] is installed, and displays a status message on the results of the search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e967-110">此指令碼可供 Internet Explorer。</span><span class="sxs-lookup"><span data-stu-id="7e967-110">This script is designed for Internet Explorer.</span></span> <span data-ttu-id="7e967-111">其他瀏覽器使用者代理字串中，可能不包含.NET CLR 的資訊。</span><span class="sxs-lookup"><span data-stu-id="7e967-111">Other browsers may not include .NET CLR information in the UserAgent string.</span></span>  
  
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
  
 <span data-ttu-id="7e967-112">如果 「.NET CLR"版本的搜尋成功，則會出現下列類型的狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="7e967-112">If the search for the ".NET CLR " version is successful, the following type of status message appears:</span></span>  
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 <span data-ttu-id="7e967-113">否則，就會出現下列類型的狀態訊息：</span><span class="sxs-lookup"><span data-stu-id="7e967-113">Otherwise, the following type of status message appears:</span></span>  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a><span data-ttu-id="7e967-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e967-114">See Also</span></span>  
 [<span data-ttu-id="7e967-115">偵測有無安裝 .NET Framework 3.0</span><span class="sxs-lookup"><span data-stu-id="7e967-115">Detect Whether the .NET Framework 3.0 Is Installed</span></span>](../../../../docs/framework/wpf/app-development/how-to-detect-whether-the-net-framework-3-0-is-installed.md)
