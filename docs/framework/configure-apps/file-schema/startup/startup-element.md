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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153723"
---
# <a name="startup-element"></a>\<啟動>元素

指定通用語言運行時啟動資訊。

[**\<配置>**](../configuration-element.md)  
&nbsp;&nbsp;**\<啟動>**  

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
|`useLegacyV2RuntimeActivationPolicy`|選擇性屬性。<br /><br /> 指定是啟用 .NET 框架 2.0 運行時啟動策略還是使用 .NET 框架 4 啟動策略。|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>使用傳統V2運行時啟動策略屬性

|值|描述|
|-----------|-----------------|
|`true`|為所選運行時啟用 .NET Framework 2.0 運行時啟動策略，即將舊式運行時啟動技術（如[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)）綁定到從設定檔中選擇的運行時，而不是在 CLR 版本 2.0 上將其封頂。 因此，如果從設定檔中選擇 CLR 版本 4 或更高版本，則使用早期版本的 .NET Framework 創建的混合模式程式集將載入所選 CLR 版本。 設置此值可防止 CLR 版本 1.1 或 CLR 版本 2.0 載入到同一進程中，從而有效地禁用進程內並排功能。|
|`false`|對 .NET 框架 4 及更高版本使用預設啟動策略，即允許舊式運行時啟動技術將 CLR 版本 1.1 或 2.0 載入到進程中。 設置此值可防止混合模式程式集載入到 .NET 框架 4 或更高版本，除非這些程式集是使用 .NET 框架 4 或更高版本構建的。 這是預設值。|

### <a name="child-elements"></a>子元素

|元素|描述|
|-------------|-----------------|
|[\<所需的運行時>](requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。 使用執行階段版本 1.1 或更高版本構建的應用程式應使用**\<支援的 Runtime>** 元素。|
|[\<支援的運行時>](supportedruntime-element.md)|指定應用程式支援的通用語言執行平台版本。|

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|

## <a name="remarks"></a>備註

 ** \<支援的 Runtime>** 元素應由使用執行階段版本 1.1 或更高版本構建的所有應用程式使用。 為僅支援執行階段版本 1.0 而構建的應用程式必須使用**\<所需的 Runtime>** 元素。

 Microsoft Internet Explorer 中託管的應用程式的啟動代碼忽略**\<啟動>** 元素及其子項目。

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>使用傳統V2運行時啟動策略屬性

 如果應用程式使用舊版啟動路徑（如[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)），並且希望這些路徑啟動 CLR 的版本 4 而不是早期版本，或者應用程式是使用 .NET 框架 4 構建的，但依賴于使用早期版本的 .NET Framework 構建的混合模式程式集，則此屬性非常有用。 在這些情況下，將屬性設置為`true`。

> [!NOTE]
> 設置屬性以防止`true`CLR 版本 1.1 或 CLR 版本 2.0 載入到同一進程中，從而有效地禁用進程內並行功能（請參閱[COM 內部操作的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))）。

## <a name="example"></a>範例

 下面的示例演示如何在設定檔中指定執行階段版本。

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

- [啟動設置架構](index.md)
- [組態檔結構描述](../index.md)
- [如何：將應用配置為支援 .NET 框架 4 或更高版本](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [同處理序並存執行](../../../deployment/in-process-side-by-side-execution.md)
