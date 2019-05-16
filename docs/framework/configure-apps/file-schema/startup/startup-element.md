---
title: <startup> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: d98f8d672ed1de1a5065a0390dba29992bcc1b39
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634463"
---
# <a name="startup-element"></a>\<啟動 > 項目

指定 common language runtime 的啟動資訊。

 \<configuration> \<startup>

## <a name="syntax"></a>語法

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a>屬性和元素

 下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|選擇性屬性。<br /><br /> 指定是否要啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]執行階段啟用原則，或使用[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]啟用原則。|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy 屬性

|值|描述|
|-----------|-----------------|
|`true`|啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]執行階段啟用原則，針對所選的執行階段，也就是繫結舊版執行階段啟用技術 (例如[CorBindToRuntimeEx 函式](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) 至執行階段從組態檔，而不是選擇在 CLR 2.0 版將達到其上限。 因此，如果從組態檔中選擇 CLR 版本 4 或更新版本，則建立與舊版.NET Framework 的混合模式組件會載入與所選的 CLR 版本。 將此值設定防止 CLR 1.1 版或 CLR 2.0 版載入到相同的程序，並有效地停用內含式並排顯示功能。|
|`false`|使用預設的啟用原則，如[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本中，也就是允許舊版執行階段載入處理序中的 CLR 1.1 或 2.0 版的啟用技術。 將此值可防止混合模式組件載入到.NET Framework 4 或更新版本，除非它們建置在.NET Framework 4 或更新版本。 預設值為這個值。|

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。 使用執行階段版本 1.1 或更新版本建置的應用程式應該改用 **\<Supportedruntime> >** 項目。|
|[\<supportedRuntime>](supportedruntime-element.md)|指定應用程式支援的通用語言執行平台版本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|

## <a name="remarks"></a>備註

  **\<Supportedruntime> >** 項目應由使用 1.1 版或更新版本的執行階段所建置的所有應用程式。 若要只支援 1.0 版的執行階段所建置的應用程式必須使用 **\<Requiredruntime> >** 項目。

 在 Microsoft Internet Explorer 中裝載的應用程式的啟動程式碼會忽略**\<啟動 >** 項目和其子項目。

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy 屬性

 此屬性才有用，如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx 函式](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)，和您想要這些路徑來啟動第 4 版的 clr，而不是較早的版本，或如果您的應用程式使用建置[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]但有使用舊版.NET Framework 所建置的混合模式組件中的 相依性。 在這些情況下，將屬性設定為`true`。

> [!NOTE]
> 將屬性設定為`true`載入至相同的程序，並有效地停用內含式並排顯示功能可防止 CLR 1.1 版或 CLR 2.0 版 (請參閱 < [COM interop 的並排顯示執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100)))。

## <a name="example"></a>範例

 下列範例示範如何在組態檔中指定的執行階段版本。

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [啟動設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [如何：設定應用程式以支援 .NET Framework 4 或更新版本](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [同處理序並存執行](../../../deployment/in-process-side-by-side-execution.md)
