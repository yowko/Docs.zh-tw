---
title: <system.serviceModel.activation>
ms.date: 03/30/2017
ms.assetid: c0cae85f-56cb-4030-8807-6f96edff8d2d
ms.openlocfilehash: e00bbad452398e7f8f4f50208da572986391fc9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399468"
---
# <a name="systemservicemodelactivation"></a><span data-ttu-id="2f0a1-102">\<system.serviceModel.activation></span><span class="sxs-lookup"><span data-stu-id="2f0a1-102">\<system.serviceModel.activation></span></span>
<span data-ttu-id="2f0a1-103">這個組態區段表示 SMSvcHost.exe 工具的組態設定。</span><span class="sxs-lookup"><span data-stu-id="2f0a1-103">This configuration section represents the configuration settings for the SMSvcHost.exe tool.</span></span> <span data-ttu-id="2f0a1-104">組態項目可於 SMSvcHost.exe.config 檔案中設定。</span><span class="sxs-lookup"><span data-stu-id="2f0a1-104">The configuration elements can be configured in the SMSvcHost.exe.config file.</span></span> <span data-ttu-id="2f0a1-105">具體來說，它包含了所有必須設定的整個電腦設定。</span><span class="sxs-lookup"><span data-stu-id="2f0a1-105">Specifically, it includes all machine-wide settings that must be configured.</span></span>  

<span data-ttu-id="2f0a1-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2f0a1-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2f0a1-107">&nbsp;&nbsp; **\<System.servicemodel. 啟用 >**</span><span class="sxs-lookup"><span data-stu-id="2f0a1-107">&nbsp;&nbsp;**\<system.serviceModel.activation>**</span></span>  
  
## <a name="sample-configuration-file"></a><span data-ttu-id="2f0a1-108">範例組態檔</span><span class="sxs-lookup"><span data-stu-id="2f0a1-108">Sample Configuration File</span></span>  
 <span data-ttu-id="2f0a1-109">以下為範例組態檔 (SMSvcHost.exe.config)，由 SMSvcHost.exe 接聽程式處理序使用。</span><span class="sxs-lookup"><span data-stu-id="2f0a1-109">The following is a sample configuration file (SMSvcHost.exe.config), which is used by the listener process SMSvcHost.exe.</span></span>  
  
```xml  
<configuration>
  <runtime>
    <gcConcurrent enabled="false" />
  </runtime>
  <system.serviceModel.activation>
    <net.tcp listenBacklog="10"
             maxPendingAccepts="2"
             maxPendingConnections="100"
             receiveTimeout="00:00:10"
             teredoEnabled="false">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18"/>
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19"/>
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20"/>
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568"/>
      </allowAccounts>
    </net.tcp>
    <net.pipe maxConnectionsPendingDispatch="100"
              maxPendingAccepts="2"
              receiveTimeout="00:00:10">
      <allowAccounts>
        <!-- LocalSystem account -->
        <add securityIdentifier="S-1-5-18" />
        <!-- LocalService account -->
        <add securityIdentifier="S-1-5-19" />
        <!-- Network Service account -->
        <add securityIdentifier="S-1-5-20" />
        <!-- Administrators account -->
        <add securityIdentifier="S-1-5-32-544" />
        <!-- IIS_IUSRS account (Vista only) -->
        <add securityIdentifier="S-1-5-32-568" />
      </allowAccounts>
    </net.pipe>
    <diagnostics performanceCountersEnabled="true" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="2f0a1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f0a1-110">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration>
