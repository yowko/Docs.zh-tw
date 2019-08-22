---
title: <NetFx40_PInvokeStackResilience> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf97cc1ec544c7cf640c43b1b45760fca8cffe89
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663548"
---
# <a name="netfx40_pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience > 元素

指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。

\<configuration > \
\<執行時間 > \
\<NetFx40_PInvokeStackResilience>

## <a name="syntax"></a>語法

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述屬性、子項目和父項目。

### <a name="attributes"></a>屬性

|屬性|描述|
|---------------|-----------------|
|`enabled`|必要屬性。<br /><br /> 指定執行時間是否偵測到不正確的平台叫用宣告, 並在32位平臺上自動修正執行時間的堆疊。|

## <a name="enabled-attribute"></a>啟用屬性

|值|描述|
|-----------|-----------------|
|`0`|執行時間會使用 .NET Framework 4 中引進的更快 interop 封送處理架構, 這不會偵測並修正不正確的平台叫用宣告。 這是預設值。|
|`1`|執行時間會使用較慢的轉換來偵測並修正不正確的平台叫用宣告。|

### <a name="child-elements"></a>子元素

無。

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|
|`runtime`|包含有關執行階段初始化選項的資訊。|

## <a name="remarks"></a>備註

此元素可讓您針對執行時間復原, 針對不正確的平台叫用宣告, 進行更快速的 interop 封送處理。

從 .NET Framework 4 開始, 簡化的 interop 封送處理架構可大幅改善從 managed 程式碼轉換為非受控碼的效能。 在舊版的 .NET Framework 中, 封送處理層在32位平臺上偵測到不正確的平台叫用宣告, 並自動修正堆疊。 新的封送處理架構會消除此步驟。 因此, 轉換會非常快速, 但不正確的平台叫用宣告可能會導致程式失敗。

為了讓您在開發過程中輕鬆偵測不正確的宣告, 已改善 Visual Studio 的偵錯工具體驗。 當您的應用程式是以附加的偵錯工具執行時, [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed 偵錯工具 (MDA) 會通知您不正確的平台叫用宣告。

若要處理您的應用程式使用無法重新編譯的元件, 且其平台叫用宣告不正確的情況, 您`NetFx40_PInvokeStackResilience`可以使用元素。 將此專案新增至您的應用程式`enabled="1"`設定檔, 並使用舊版 .NET Framework 的行為, 以較慢的轉換為代價, 將其加入至相容性模式。 已針對舊版 .NET Framework 編譯的元件會自動選擇進入此相容性模式, 而且不需要此元素。

## <a name="configuration-file"></a>組態檔

這個元素只能用在應用程式佈建檔中。

## <a name="example"></a>範例

下列範例示範如何針對應用程式的不正確平台叫用宣告, 選擇增加的復原能力, 代價是 managed 和非受控碼之間的轉換速度較慢。

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
- [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
