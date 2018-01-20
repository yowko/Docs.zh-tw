---
title: "&lt;loadFromRemoteSources&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: "31"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13b42405a0faf721c46476aadaa0cff8163883c1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a>&lt;loadFromRemoteSources&gt;項目
指定是否從遠端來源的組件應該被授與完全信任。  
  
> [!NOTE]
>  如果您已導向至本主題，因為 Visual Studio 專案錯誤清單或建置錯誤中的錯誤訊息，請參閱[How to： 使用 Visual Studio 中的 從 Web 組件](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070)。  
  
 \<configuration>  
\<runtime>  
\<loadFromRemoteSources>  
  
## <a name="syntax"></a>語法  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否會從遠端來源載入的組件應該被授與完全信任。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|請勿授與完全信任的應用程式從遠端來源。 這是預設值。|  
|`true`|授與完全信任應用程式從遠端來源。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET Framework 3.5 版和更早版本中，如果您從遠端位置，載入組件的組件就會執行部分信任使用取決於它已載入該區域的授權集。 例如，如果您從網站載入組件，該組件就會載入至網際網路區域，並取得網際網路權限集。 換句話說，它在網際網路沙箱中執行。 如果您嘗試在執行該組件[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本中，會擲回例外狀況，則您必須明確地建立沙箱組件 (請參閱[如何： 執行部分信任程式碼在沙箱中](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md))，或在完全信任中執行。  
  
 `<loadFromRemoteSources>` 項目可讓您指定在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] (含) 以後版本中，以完全信任方式執行先前在舊版 .NET Framework 中以部分信任方式執行的組件。 根據預設，遠端組件不會在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] (含) 以後版本中執行。 若要執行遠端組件，您必須以完全信任方式執行該組件，或是建立要在其中執行該組件的沙箱 <xref:System.AppDomain>。  
  
> [!NOTE]
>  在 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 中，區域網路共用上的組件預設會以完全信任方式執行，因此您不需要啟用 `<loadFromRemoteSources>` 項目。  
  
> [!NOTE]
>  如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。 您可以變更該指定變更檔案屬性，或者您可以使用`<loadFromRemoteSources>`授與組件的項目完全信任。 或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。  
  
 `enabled`屬性只有在程式碼存取安全性 (CAS) 已停用時，才這個項目才有效。 根據預設，CAS 原則中已停用[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本。 如果您設定`enabled`至`true`，遠端應用程式會授與完全信任。  
  
 如果`<loadFromRemoteSources>``enabled`未設定為`true`，在下列情況下擲回例外狀況：  
  
-   目前網域的沙箱化處理行為是在其行為與不同[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]。 這需要停用時，CAS 原則和目前的網域為沙箱化。  
  
-   正在載入的組件不是來自`MyComputer`區域。  
  
> [!NOTE]
>  您可能會收到<xref:System.IO.FileLoadException>Windows Virtual PC 應用程式，當您嘗試載入的檔案從主機服務電腦上的連結資料夾中。 當您嘗試從透過連結的資料夾載入檔案時，也可能發生此錯誤[遠端桌面服務](http://go.microsoft.com/fwlink/?LinkId=182775)（終端機服務）。 若要避免此例外狀況，將`enabled`至`true`。  
  
 設定`<loadFromRemoteSources>`元素`true`可避免擲回這個例外狀況。 它可讓您指定，您不依賴沙箱 common language runtime 載入的組件的安全性，和它們可以允許將當做執行完全信任。  
  
> [!IMPORTANT]
>  如果組件不在完全信任執行，請勿設定這個組態項目。 請改為建立的沙箱<xref:System.AppDomain>要載入的組件。  
  
## <a name="configuration-file"></a>組態檔  
 此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。 如需詳細資訊，請參閱文章[詳細隱含使用 CAS 原則： loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) .NET 安全性部落格。  
  
## <a name="example"></a>範例  
 下列範例會示範如何從遠端來源授與完全信任的應用程式。  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 [更隱含使用了 CAS 原則： loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [如何：在沙箱中執行部分信任的程式碼](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
