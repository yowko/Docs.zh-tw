---
title: <requiredRuntime> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697492"
---
# <a name="requiredruntime-element"></a>@no__t 0requiredRuntime > 元素

指定應用程式只支援 Common Language Runtime 1.0 版。 此元素已被取代，不應該再使用。 應該改為使用[@no__t 1](supportedruntime-element.md)元素。

[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<startup >** ](startup-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requiredRuntime >**  

## <a name="syntax"></a>語法

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`version`|選擇性屬性。<br /><br /> 字串值，指定此應用程式支援的 .NET Framework 版本。 字串值必須符合在 .NET Framework 安裝根目錄下找到的目錄名稱。 不會剖析字串值的內容。|
|`safemode`|選擇性屬性。<br /><br /> 指定執行時間啟動程式碼是否會搜尋登錄，以判斷執行階段版本。|

## <a name="safemode-attribute"></a>安全模式屬性

|值|描述|
|-----------|-----------------|
|`false`|執行時間啟動程式碼會在登錄中尋找。 這是預設值。|
|`true`|執行時間啟動程式碼不會在登錄中尋找。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父元素

|元素|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`startup`|`<requiredRuntime>`包含元素。|

## <a name="remarks"></a>備註
 為了僅支援1.0 版執行時間所建立的應用程式，必須使用 `<requiredRuntime>` 元素。 使用1.1 版或更新版本的執行時間所建立的應用程式必須使用 `<supportedRuntime>` 元素。

> [!NOTE]
> 如果您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定設定檔，您必須針對所有版本的執行時間使用 `<requiredRuntime>` 元素。 當您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，會忽略 `<supportedRuntime>` 元素。

 @No__t-0 屬性字串必須符合指定之 .NET Framework 版本的安裝資料夾名稱。 不會解讀此字串。 如果執行時間啟動程式碼找不到相符的資料夾，則不會載入執行時間;啟動程式碼會顯示錯誤訊息並結束。

> [!NOTE]
> Microsoft Internet Explorer 中裝載之應用程式的啟動代碼會忽略 @no__t 0 元素。

## <a name="example"></a>範例

下列範例顯示如何指定設定檔中的執行階段版本。

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [啟動設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [如何：設定應用程式以支援 .NET Framework 4 或更新版本](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
