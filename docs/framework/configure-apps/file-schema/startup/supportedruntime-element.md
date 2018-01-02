---
title: "&lt;supportedRuntime&gt;項目"
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 77886cef1a8dbd320223526b86f86fa9cee6a9f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltsupportedruntimegt-element"></a>&lt;supportedRuntime&gt;項目
指定應用程式支援的通用語言執行平台版本。 所有以 .NET Framework 1.1 (含) 以後版本建置的應用程式都應使用這個項目。  
  
[\<configuration>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  

[\<startup>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
  
**\<supportedRuntime>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**version**|選擇性屬性。<br /><br /> 字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。 如需有效值的`version`屬性，請參閱[「 執行階段版本 」 值](#version)> 一節。 **注意：**透過.NET Framework 3.5，「*執行階段版本*"值的形式*主要*。*次要*。*建置*。 從 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，只需要主要和次要版本號碼 (也就是 "v4.0"，不需要 "v4.0.30319")。 建議使用較短的字串。|  
|**sku**|選擇性屬性。<br /><br /> 字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。<br /><br /> 從.NET Framework 4.0 使用`sku`屬性建議。  該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。<br /><br /> 如需 sku 屬性的有效值，請參閱[「 sku 識別碼 」 值](#sku)> 一節。|  
  
## <a name="remarks"></a>備註  
如果 **\<supportedRuntime >**項目不存在於應用程式組態檔，在使用執行階段用來建置應用程式的版本。  

 **\<SupportedRuntime >**使用 1.1 版或更新版本的執行階段所建置的所有應用程式應該使用項目。 只支援 1.0 版的執行階段建置的應用程式必須使用[ \<requiredRuntime >](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)項目。  
  
> [!NOTE]
>  如果您使用[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函式指定組態檔，您必須使用`<requiredRuntime>`執行階段的所有版本的項目。 `<supportedRuntime>`使用時，便會忽略元素[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)。  
  
針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。 應用程式支援.NET Framework 4.0 或更新版本中，`version`屬性會指出 CLR 版本，也就是一般.NET Framework 4 和更新版本，而`sku`屬性會指出單一.NET Framework 版本的應用程式目標。  
  
> [!NOTE]
>  如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx 函式](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)，而且希望這些路徑啟用 CLR，而不是較早的版本中，第 4 版或如果您的應用程式使用建立[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]具有相依性，但與舊版的.NET framework 建置的混合模式組件，它並不足以指定[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]支援的執行階段清單中。 此外，在[\<啟動 > 項目](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)在組態檔中，您必須設定`useLegacyV2RuntimeActivationPolicy`屬性`true`。 但是，將這個屬性設定為 `true`，即表示以舊版 .NET Framework 建置的所有元件都會使用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 執行，而不是原本建置時所使用的執行階段。  
  
建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。  
  
<a name="version"></a>   
## <a name="runtime-version-values"></a>「執行階段版本」值  
`runtime`屬性指定的 Common Language Runtime (CLR) 版本所需的特定應用程式。 請注意，所有的.NET Framework v4.x 版本指定`v4.0`CLR。 下表列出的有效值*執行階段版本*值`version`屬性。  

|.NET Framework 版本|`version` 屬性|  
|----------------------------|-------------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0-4.7.1|"v4.0"|  

  
<a name="sku"></a>   
## <a name="sku-id-values"></a>「SKU 識別碼」值  
`sku`屬性會使用目標 framework moniker (TFM)，以指出應用程式為目標，且需要執行的.NET framework 版本。 下表列出支援的有效值`sku`屬性，從.NET Framework 4 開始。
  
|.NET Framework 版本|`sku` 屬性|  
|----------------------------|---------------------|  
|4.0|".NETFramework,Version=v4.0"|  
|4.0，Client Profile|".NETFramework,Version=v4.0,Profile=Client"|  
|4.0，平台更新 1|.NETFramework,Version=v4.0.1|  
|4.0，Client Profile，更新 1|.NETFramework,Version=v4.0.1,Profile=Client|  
|4.0，平台更新 2|.NETFramework,Version=v4.0.2|  
|4.0，Client Profile，更新 2|.NETFramework,Version=v4.0.2,Profile=Client|  
|4.0，平台更新 3|.NETFramework,Version=v4.0.3|  
|4.0，Client Profile，更新 3|.NETFramework,Version=v4.0.3,Profile=Client|  
|4.5|".NETFramework,Version=v4.5"|  
|4.5.1|".NETFramework,Version=v4.5.1"|  
|4.5.2|".NETFramework,Version=v4.5.2"|  
|4.6|".NETFramework,Version=v4.6"|  
|4.6.1|".NETFramework,Version=v4.6.1"|  
|4.6.2|".NETFramework，Version = v4.6.2"|  
|4.7|".NETFramework，Version = v4.7"|
|4.7.1|".NETFramework，Version = 4.7.1"|

## <a name="example"></a>範例  
 下列範例將示範如何在設定檔中指定支援的執行階段版本。 組態檔會指出應用程式的目標.NET Framework 4.7。  
  
```xml  
<configuration>  
   <startup>  
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />  
   </startup>  
</configuration>  
```  
  
## <a name="configuration-file"></a>組態檔  
 這個項目可以在應用程式組態檔中使用。  
  
## <a name="see-also"></a>請參閱  
 [啟動設定結構描述](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [同處理序並存執行](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
