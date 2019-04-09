---
title: <NetFx40_LegacySecurityPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_LegacySecurityPolicy> element
- NetFx40_LegacySecurityPolicy element
ms.assetid: 07132b9c-4a72-4710-99d7-e702405e02d4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20a0ca8560fcd5d7f9d171df3e3b4c3f42e78641
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075986"
---
# <a name="netfx40legacysecuritypolicy-element"></a>\<NetFx40_LegacySecurityPolicy > 項目
指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。  
  
 \<configuration>  
\<執行階段 >  
<NetFx40_LegacySecurityPolicy>  
  
## <a name="syntax"></a>語法  
  
```xml  
<NetFx40_LegacySecurityPolicy  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否使用舊版 CAS 原則。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行階段不使用舊版 CAS 原則。 這是預設值。|  
|`true`|執行階段會使用舊版 CAS 原則。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 在.NET Framework 3.5 版和更早版本中，CAS 原則一律是作用中。 在  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，必須啟用 CAS 原則。  
  
 特定版本的 CAS 原則。 存在舊版.NET Framework 中的自訂 CA 原則必須重新指定在[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。  
  
 套用`<NetFx40_LegacySecurityPolicy>`項目[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]組件不會影響[安全性透明程式碼](../../../../../docs/framework/misc/security-transparent-code.md); 透明度規則仍適用。  
  
> [!IMPORTANT]
>  套用`<NetFx40_LegacySecurityPolicy>`項目可以原生映像所建立的組件會導致重大的效能損失[原生映像產生器 (Ngen.exe)](../../../../../docs/framework/tools/ngen-exe-native-image-generator.md) ，不會安裝在[全域組件快取](../../../../../docs/framework/app-domains/gac.md). 效能降低因執行階段無法載入組件為原生映像，套用屬性時，導致其被載入，在 just-in-time 組件。  
  
> [!NOTE]
>  如果您指定的目標.NET Framework 版本早於[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]在專案設定為您的 Visual Studio 專案中，CAS 原則就會啟用，包括您為該版本所指定的任何自訂 CA 原則。 不過，您將無法使用新[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]類型和成員。 您也可以藉由指定舊版的.NET framework [ \<Supportedruntime> > 項目](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)啟動設定結構描述中您[應用程式組態檔](../../../../../docs/framework/configure-apps/index.md)。  
  
> [!NOTE]
>  組態檔語法會區分大小寫。 提供語法和範例區段中，您應該使用的語法。  
  
## <a name="configuration-file"></a>組態檔  
 此元素只用於應用程式組態檔中。  
  
## <a name="example"></a>範例  
 下列範例示範如何啟用舊版 CAS 原則，對應用程式。  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
