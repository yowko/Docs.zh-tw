---
title: "&lt;loadFromRemoteSources&gt; 元素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "loadFromRemoteSources 項目"
  - "<loadFromRemoteSources> 元素"
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: 31
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 31
---
# &lt;loadFromRemoteSources&gt; 元素
指定是否應該對遠端來源的組件授與完全信任。  
  
> [!NOTE]
>  如果因為發生 Visual Studio 專案錯誤清單或建置錯誤中的錯誤訊息而將您帶到本主題，請參閱 [HOW TO：在 Visual Studio 使用來自網路的組件](http://msdn.microsoft.com/zh-tw/d8635b63-89a0-41aa-90f4-f351b2111070)。  
  
## 語法  
  
```  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定是否應該對從遠端來源載入的組件授與完全信任。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|請勿對遠端來源的應用程式授與完全信任。  這是預設值。|  
|`true`|將完全信任授與給遠端來源的應用程式。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
 在 .NET Framework 3.5 \(含\) 以前版本中，如果您從遠端位置載入組件，這個組件將會搭配依載入區域而定的授權集，以部分信任方式來執行。  例如，如果從網站載入組件，它就會載入至網際網路區域，並獲得網際網路權限集的授與。  換句話說，它是在網際網路沙箱中執行。  如果嘗試在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 或較新版本上執行該組件，就會擲回例外狀況 。您必須為該組件明確建立沙箱\(請參閱[How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)\)，或是以完全信任來執行該組件。  
  
 `<loadFromRemoteSources>` 項目可讓您指定舊版 .NET Framework 中以部分信任方式執行的組件，是否應該在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以及叫新版本中以完全信任的方式執行。  根據預設，遠端組件無法在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] \(含\) 以後版本中執行 。  若要執行遠端組件，您必須以完全信任或建立執行其沙箱 <xref:System.AppDomain> 。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]區域網路共用上的組件根據預設以完全信任執行；您不需要啟用 `<loadFromRemoteSources>` 項目。  
  
> [!NOTE]
>  如果應用程式是從網路複製，即使位於本機電腦上，也會由 Windows 標示為 Web 應用程式。  您可以藉由變更檔案屬性來變更該指定，或者可以使用 `<loadFromRemoteSources>` 項目來授與組件完全信任。  或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法來載入作業系統標示為從 Web 載入的本機組件。  
  
 只有當停用程式碼存取安全性 \(CAS\) 時，這個項目的 `enabled` 屬性才會有效。  根據預設，[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] \(含\) 以後版本都會停用 CAS 原則。  如果您將 `enabled` 設定為 `true`，就會授與遠端應用程式完全信任。  
  
 如果沒有將 `<loadFromRemoteSources>` `enabled` 設為 `true`，則會在下列情況中擲回例外狀況：  
  
-   目前網域的沙箱行為與它在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 中的行為不同。  這需要停用 CAS 原則，但不要將目前網域沙箱化。  
  
-   載入的組件不是來自 `MyComputer` 區域。  
  
> [!NOTE]
>  當您嘗試從主機電腦上的連結資料夾載入檔案時，便可能會收到 Windows Virtual PC 應用程式中的 <xref:System.IO.FileLoadException>。  當您嘗試從連接 [遠端桌面服務](http://go.microsoft.com/fwlink/?LinkId=182775)\(終端機服務\)的資料夾中載入檔案，這項錯誤也可能發生。  若要避免此例外狀況，請將 `enabled` 設定為 `true`。  
  
 將 `<loadFromRemoteSources>` 項目設定為 `true` 以避免擲回這個例外狀況。  它可讓您指定不要依賴 Common Language Runtime 將載入的組件沙箱化以確保安全性，並允許以完全信任的方式執行這些組件。  
  
> [!IMPORTANT]
>  如果組件不應以完全信任的方式執行，就不要設定這個組態項目。  請改為建立要在其中載入組件的沙箱化 <xref:System.AppDomain>。  
  
## 組態檔  
 這個項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。  如需詳細資訊，請參閱 .NET 安全性的部落格文章 [對 CAS 原則的更隱含的使用：loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) 。  
  
## 範例  
 下列範例示範如何對遠端來源的應用程式授與完全信任。  
  
```  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [對 CAS 原則的更隱含的使用：loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)   
 [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)   
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)