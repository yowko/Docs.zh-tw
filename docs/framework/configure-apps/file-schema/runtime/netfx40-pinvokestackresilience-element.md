---
title: '&lt;NetFx40_PInvokeStackResilience&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0cfd8c971edd4537de6e073c49f128f86eb8a042
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748993"
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a>&lt;NetFx40_PInvokeStackResilience&gt;項目
指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。  
  
 \<configuration>  
\<執行階段 >  
< NetFx40_PInvokeStackResilience >  
  
## <a name="syntax"></a>語法  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否執行階段偵測到不正確的平台叫用宣告，並自動在執行階段在 32 位元平台上修正堆疊。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`0`|執行階段會更快的 interop 封送處理架構中導入[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]、 其中不會偵測及修正不正確的平台叫用宣告。 這是預設值。|  
|`1`|執行階段會使用速度較慢轉換偵測及修正不正確的平台叫用宣告。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 這個項目可讓您更快速 interop 封送處理為執行時期恢復功能，針對不正確的平台叫用宣告進行交易。  
  
 從開始[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]，簡化的 interop 封送處理架構提供從 managed 程式碼會轉換成 unmanaged 程式碼的效能大幅提升。 在舊版的.NET Framework 中，封送處理的層級偵測到不正確平台叫用 32 位元平台上的宣告，並自動修正堆疊。 新的封送處理架構會移除此步驟。 如此一來，轉換會非常快速，但不正確的平台叫用宣告可能會導致程式失敗。  
  
 若要可讓您輕鬆偵測不正確的宣告，在開發期間，Visual Studio 偵錯體驗已經過改良。 [PInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) managed 偵錯助理 (MDA) 會通知您不正確的平台叫用宣告附加了偵錯工具執行您的應用程式時。  
  
 您的應用程式使用的元件，您無法重新編譯，，有不正確的平台叫用宣告，您可以使用位置的位址案例`NetFx40_PInvokeStackResilience`項目。 將這個項目加入至應用程式組態檔與`enabled="1"`opts 為相容性模式，與舊版的.NET Framework 中，但要付出速度較慢的轉換行為。 針對舊版.NET Framework 的已編譯的組件會自動選擇加入此相容性模式中，而且不需要這個項目。  
  
## <a name="configuration-file"></a>組態檔  
 此項目只能用於應用程式組態檔中。  
  
## <a name="example"></a>範例  
 下列範例會示範如何針對不正確的增加彈性選擇平台叫用的應用程式，但要付出之間的速度較慢轉換宣告 managed 和 unmanaged 程式碼。  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
