---
title: '&lt;Requiredruntime>&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7cb5e29f3d7fc1faffdba01a5322f1883fca8af0
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837385"
---
# <a name="ltrequiredruntimegt-element"></a>&lt;Requiredruntime>&gt;項目
指定應用程式只支援 Common Language Runtime 1.0 版。 這個項目已被取代，無法再使用。 [ `supportedRuntime` ](supportedruntime-element.md)應該改為使用項目。
  
 \<configuration>  
\<啟動 >  
\<requiredRuntime>  
  
## <a name="syntax"></a>語法  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`version`|選擇性屬性。<br /><br /> 字串值，指定這個應用程式支援的.NET framework 版本。 字串值必須符合.NET Framework 安裝根下找到的目錄名稱。 未剖析的字串值的內容。|  
|`safemode`|選擇性屬性。<br /><br /> 指定是否要在執行階段啟始程式碼搜尋登錄，以判斷執行階段版本。|  
  
## <a name="safemode-attribute"></a>安全模式屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|執行階段啟始程式碼會尋找在登錄中。 這是預設值。|  
|`true`|執行階段啟始程式碼不會在登錄中尋找。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`startup`|包含`<requiredRuntime>`項目。|  
  
## <a name="remarks"></a>備註  
 若要只支援 1.0 版的執行階段所建置的應用程式必須使用`<requiredRuntime>`項目。 使用 1.1 版或更新版本的執行階段所建置的應用程式必須使用`<supportedRuntime>`項目。  
  
> [!NOTE]
>  如果您使用[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定組態檔，您必須使用`<requiredRuntime>`的執行階段的所有版本的項目。 `<supportedRuntime>`當您使用時，便會忽略元素[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)。  
  
 `version`屬性字串必須符合指定之版本的.NET framework 的安裝資料夾名稱。 此字串無法加以解譯。 如果執行階段啟始程式碼找不到相符的資料夾，則執行階段不會載入;啟動程式碼會顯示錯誤訊息，並結束。  
  
> [!NOTE]
>  在 Microsoft Internet Explorer 中裝載的應用程式的啟始程式碼會忽略`<requiredRuntime>`項目。  
  
## <a name="example"></a>範例  
 下列範例示範如何在組態檔中指定的執行階段版本。  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [啟動設定結構描述](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [\<PaveOver> 指定要使用哪一個執行階段版本](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
