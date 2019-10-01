---
title: <assert> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 30ec24aefcf8c4d1e110238a2c60a958eded5545
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699391"
---
# <a name="assert-element"></a>@no__t 0assert > 元素
指定呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> 方法時是否要顯示訊息方塊，此外也會指定寫入訊息之目的地檔案的名稱。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. 診斷 >** ](system-diagnostics-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<assert >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`assertuienabled`|選擇性屬性。<br /><br /> 指定當**Debug. Assert**方法評估為**false**時，是否要顯示訊息方塊。|  
|`logfilename`|選擇性屬性。<br /><br /> 指定在**Debug. Assert**評估為**false**時，要寫入訊息的檔案名。|  
  
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
 在這兩個屬性 **\<判斷提示>** 是選擇性的項目。 您可以停用訊息方塊，但不指定要寫入訊息的檔案，或者您也可以指定要寫入訊息的檔案，同時讓訊息方塊保持啟用。  
  
## <a name="example"></a>範例  
 下列範例顯示當您呼叫**Debug. Assert**並將訊息寫入 `c:\log.txt` 時，如何停用顯示訊息方塊。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.Debug>
- [追蹤和偵錯設定結構描述](index.md)
