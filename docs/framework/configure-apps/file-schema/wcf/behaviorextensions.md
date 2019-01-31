---
title: <behaviorExtensions>
ms.date: 03/30/2017
ms.assetid: 59f2791a-c78f-40d7-aa80-0d9cd10135d9
ms.openlocfilehash: b3554db2ee037eceb43126968a02e826b65928a0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55285898"
---
# <a name="behaviorextensions"></a>\<behaviorExtensions>
行為延伸可讓使用者建立使用者定義的行為項目。 這些項目可以和標準的 Windows Communication Foundation (WCF) 行為項目並列使用。 `behaviorExtensions` 區段會定義項目，讓項目可用於組態中。 以下是典型行為擴充的範例。  
  
```xml  
<system.serviceModel>
  <extensions>
    <behaviorExtensions>
      <add name="myBehavior"
           type="Microsoft.ServiceModel.Samples.MyBehaviorSection, MyBehavior,
                 Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
    </behaviorExtensions>
  </extensions>
</system.serviceModel>
```  
  
 若要將組態功能加入至項目，您必須寫入並註冊組態項目。 如需這方面的詳細資訊，請參閱 <xref:System.Configuration>。  
  
 在定義項目及其組態型別後，即可使用擴充，如下列範例所示。  
  
```xml  
<behaviors>
  <behavior configurationName="testChannelBehavior">
    <myBehavior />
    <channelSecurity cacheCookies="false"
                     detectReplays="false"
                     maxCachedNonces="9"
                     maxClockSkew="00:00:03"
                     maxCookieCachingTime="00:07:24"
                     replayWindow="00:07:22.2190000" />
  </behavior>
</behaviors>
```  
  
## <a name="security"></a>安全性  
 強烈建議您在 `machine.config` 和 `app.config` 檔案中註冊型別時，使用完整組件名稱。 如果型別不是唯一定義的型別，則 CLR 型別載入器會以指定的順序在以下位置中搜尋該型別：  
  
 如果型別的組件為已知，則載入器會搜尋組態檔案的重新導向位置、GAC、使用組態資訊的目前組件，和應用程式基底目錄。 如果組件為未知，則載入器會搜尋目前組件、mscorlib 和 `TypeResolve` 事件處理常式傳回的位置。 這個 CLR 搜尋順序可以用型別轉送機制和 AppDomain.TypeResolve 事件等攔截程序 (Hook) 來修改。  
  
 攻擊者可能會利用 CLR 搜尋順序並執行未經授權的程式碼。 使用完整 (強式) 名稱來唯一識別型別，可進一步增加您系統的安全性。  
  
 如需詳細資訊，請參閱 <<c0> [ 執行階段如何找出組件](https://go.microsoft.com/fwlink/?LinkId=95336)和<xref:System.AppDomain.TypeResolve>。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>
- [使用行為來設定與擴充執行階段](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
