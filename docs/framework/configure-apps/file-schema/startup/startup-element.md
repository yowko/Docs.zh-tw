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
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153723"
---
# <a name="startup-element"></a>\<startup> 項目

指定 common language runtime 啟動資訊。

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

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
|`useLegacyV2RuntimeActivationPolicy`|選擇性屬性。<br /><br /> 指定是否要啟用 .NET Framework 2.0 執行時間啟動原則，或使用 .NET Framework 4 啟用原則。|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy 屬性

|值|描述|
|-----------|-----------------|
|`true`|啟用所選執行時間的 .NET Framework 2.0 執行時間啟動原則，這是將舊版執行時間啟用技術（例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式）系結至從設定檔案選擇的執行時間，而不是在 CLR 2.0 版上加以上限。 因此，如果從設定檔中選擇 CLR 4 版（含）以後版本，則會使用所選擇的 CLR 版本載入以舊版 .NET Framework 建立的混合模式元件。 設定此值可防止 CLR 版本1.1 或 CLR 版本2.0 載入相同的進程中，有效地停用同進程並存功能。|
|`false`|使用 .NET Framework 4 和更新版本的預設啟用原則，這是為了允許舊版的執行時間啟用技術將 CLR 版本1.1 或2.0 載入至進程中。 設定此值可防止混合模式元件載入至 .NET Framework 4 或更新版本，除非它們是以 .NET Framework 4 或更新版本建立的。 此值為預設。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。 以執行階段版本1.1 或更新版本建立的應用程式應該使用 **\<supportedRuntime>** 元素。|
|[\<supportedRuntime>](supportedruntime-element.md)|指定應用程式支援的通用語言執行平台版本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|

## <a name="remarks"></a>備註

 專案 **\<supportedRuntime>** 應該由使用1.1 版或更新版本的執行時間所建立的所有應用程式所使用。 為了僅支援1.0 版執行時間所建立的應用程式，必須使用專案 **\<requiredRuntime>** 。

 Microsoft Internet Explorer 中裝載之應用程式的啟動程式碼會忽略 **\<startup>** 元素及其子專案。

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy 屬性

 如果您的應用程式使用舊版啟用路徑（例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式），而您想要讓這些路徑啟動 CLR 的第4版（而不是舊版），或如果您的應用程式是以 .NET Framework 4 建立，但相依于使用舊版 .NET Framework 所建立的混合模式元件，這個屬性就很有用。 在這些情況下，請將屬性設定為 `true` 。

> [!NOTE]
> 將屬性設為 `true` 可防止 clr 版本1.1 或 clr 版本2.0 載入相同的進程中，實際上會停用同進程並存功能（請參閱[COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))）。

## <a name="example"></a>範例

 下列範例顯示如何指定設定檔中的執行階段版本。

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
- [設定檔架構](../index.md)
- [如何：將應用程式設定為支援 .NET Framework 4 或更新版本](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [同處理序並存執行](../../../deployment/in-process-side-by-side-execution.md)
