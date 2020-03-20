---
title: <supportedRuntime>配置元素 - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153694"
---
# <a name="supportedruntime-element"></a>\<支援的運行時>元素

指定應用程式支援哪個通用語言執行階段版本，以及可選的 .NET Framework 版本。  

[\<配置>](../configuration-element.md)  
&nbsp;&nbsp;[\<啟動>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<支援的運行時>**  

## <a name="syntax"></a>語法

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|**version**|選擇性屬性。<br /><br /> 字串值，用於指定這個應用程式支援的通用語言執行平台 (CLR) 版本。 有關`version`屬性的有效值，請參閱["執行階段版本"值](#version)部分。 **注：** 通過 .NET 框架 3.5，"*執行階段版本*"值採用表單*主要*。*次要*。*生成*。 從 .NET 框架 4 開始，只需要主要版本號和次要版本號（即"v4.0"而不是"v4.0.30319"）。 建議使用較短的字串。|
|**Sku**|選擇性屬性。<br /><br /> 字串值，指定庫存單位 (SKU)，進而指定哪些應用程式支援的.NET Framework 版本。<br /><br /> 從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。  該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。<br /><br /> 有關 sku 屬性的有效值，請參閱["sku id"值](#sku)部分。|

## <a name="remarks"></a>備註

如果應用程式佈建檔中不存在**\<支援的 Runtime>** 元素，則使用用於生成應用程式的執行階段版本。

** \<支援的 Runtime>** 元素應由使用執行階段版本 1.1 或更高版本構建的所有應用程式使用。 為僅支援執行階段版本 1.0 而構建的應用程式必須使用[\<所需的 Runtime>](../startup/requiredruntime-element.md)元素。

> [!NOTE]
> 如果使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定設定檔，則必須對運行時的所有版本使用`<requiredRuntime>`該元素。 當您`<supportedRuntime>`使用[CorBindtoRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，該元素將被忽略。  
  
針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。 對於支援 .NET Framework 4.0 或更高版本的應用`version`，該屬性指示 CLR 版本（這是 .NET Framework 4 和更高版本`sku`所共有的），該屬性指示應用所針對的單個 .NET Framework 版本。

如果設定檔中存在`sku`**\<包含該屬性的受支援的 Runtime>** 元素，並且已安裝的 .NET Framework 版本較低，則指定的受支援版本無法運行，則應用程式將失敗，而是顯示一條消息，要求安裝受支援的版本。 否則，應用程式會嘗試在任何已安裝的版本上運行，但如果它與該版本不完全相容，則可能會意外。 （有關 .NET 框架版本之間的相容性差異，請參閱[.NET 框架中的應用程式相容性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)。因此，我們建議您在應用程式佈建檔中包含此元素，以便更輕鬆地進行錯誤診斷。 （視覺化工作室在創建新專案時自動生成的設定檔已包含該檔。
  
> [!NOTE]
> 如果應用程式使用舊版啟動路徑（如[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)），並且希望這些路徑啟動 CLR 版本 4 而不是早期版本，或者如果應用程式使用 .NET 框架 4 構建，但依賴于使用早期版本的 .NET Framework 構建的混合模式程式集，則在受支援的運行時清單中指定 .NET Framework 4 是不夠的。 此外，在設定檔中的[\<啟動>元素](../startup/startup-element.md)中，必須將`useLegacyV2RuntimeActivationPolicy`屬性設置為`true`。 但是，將此屬性設置為`true`意味著使用 .NET Framework 的早期版本構建的所有元件都使用 .NET Framework 4 而不是它們構建的運行時運行。

建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。

<a name="version"></a>
## <a name="runtime-version-values"></a>「執行階段版本」值
該`runtime`屬性指定給定應用程式所需的通用語言運行時 （CLR） 版本。 請注意，所有 .NET 框架 v4.x`v4.0`版本都指定 CLR。 下表列出了`version`屬性的*執行階段版本*值的有效值。

|.NET Framework 版本|`version` 屬性|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>"sku id"值

該`sku`屬性使用目標框架名字物件 （TFM） 來指示應用的目標和運行所需的 .NET 框架的版本。 下表列出了`sku`屬性支援的有效值，從 .NET 框架 4 開始。

|.NET Framework 版本|`sku` 屬性|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0，Client Profile|".NETFramework,Version=v4.0,Profile=Client"|
|4.0，平台更新 1|".NETFramework，版本=v4.0.1"|
|4.0，Client Profile，更新 1|".NETFramework，版本=v4.0.1，設定檔=用戶端"|
|4.0，平台更新 2|".NETFramework，版本=v4.0.2"|
|4.0，Client Profile，更新 2|".NETFramework，版本=v4.0.2，設定檔=用戶端"|
|4.0，平台更新 3|".NETFramework，版本=v4.0.3"|
|4.0，Client Profile，更新 3|".NETFramework，版本=v4.0.3，設定檔=用戶端"|
|4.5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|".NETFramework，版本=v4.6.2"|
|4.7|".NETFramework，版本=v4.7"|
|4.7.1|".NETFramework，版本=v4.7.1"|
|4.7.2|".NETFramework，版本=v4.7.2"|
|4.8|".NETFramework，版本=v4.8"|

## <a name="example"></a>範例

下列範例將示範如何在設定檔中指定支援的執行階段版本。 設定檔指示應用以 .NET 框架 4.7 為目標。

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>組態檔

這個項目可以在應用程式組態檔中使用。

## <a name="see-also"></a>另請參閱

- [啟動設置架構](../startup/index.md)
- [組態檔結構描述](../index.md)
- [同處理序並存執行](../../../deployment/in-process-side-by-side-execution.md)
