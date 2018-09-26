---
title: '&lt;判斷提示&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b15e569ff6e42298c0a1de02f77ab7c302c70d86
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193508"
---
# <a name="ltassertgt-element"></a>&lt;判斷提示&gt;項目
指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。  
  
 \<configuration>  
\<system.diagnostics >  
\<判斷提示 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`assertuienabled`|選擇性屬性。<br /><br /> 指定是否要顯示訊息方塊的時機**Debug.Assert**方法會評估要**false**。|  
|`logfilename`|選擇性屬性。<br /><br /> 指定要寫入訊息，如果檔案名稱**Debug.Assert**評估為**false**。|  
  
## <a name="assertuienabled-attribute"></a>assertuienabled 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`true`|顯示訊息方塊。 這是預設值。|  
|`false`|不會顯示訊息方塊。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
  
## <a name="remarks"></a>備註  
 在這兩個屬性**\<判斷提示 >** 是選擇性的項目。 您可以將訊息方塊停用未指定要寫入至訊息的檔案，或者您可以指定要寫入訊息時保留訊息方塊，啟用檔案。  
  
## <a name="example"></a>範例  
 下列範例示範如何停用顯示訊息方塊，當您呼叫**Debug.Assert**寫入到訊息`c:\log.txt`。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.Debug>  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
