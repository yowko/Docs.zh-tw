---
title: "&lt;移除&gt;元素&lt;接聽程式&gt;如&lt;追蹤&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 7bc4136fb917ee9b63b7cca26ba1834de21f542e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;移除&gt;元素&lt;接聽程式&gt;如&lt;追蹤&gt;
移除的接聽程式從**接聽程式**集合。  
  
 \<configuration>  
\<system.diagnostics >  
\<追蹤 >  
\<接聽項 >  
\<移除 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|**name**|必要屬性。<br /><br /> 要移除的接聽程式名稱**接聽程式**集合。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`listeners`|指定的接聽程式會收集，存放區，並將訊息路由。 接聽程式將追蹤輸出導向至適當的目標。|  
|`system.diagnostics`|指定用於收集、儲存及路由傳送訊息的追蹤接聽項，以及設定追蹤參數的層級。|  
|`trace`|設定 ASP.NET 追蹤服務。|  
  
## <a name="remarks"></a>備註  
  
> [!NOTE]
>  移除<xref:System.Diagnostics.DefaultTraceListener>從`Listeners`集合改變行為<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>， <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>，和<xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType>方法。 呼叫`Assert`或`Fail`方法通常會在顯示的訊息方塊中，不過，如果不顯示訊息方塊<xref:System.Diagnostics.DefaultTraceListener>不在`Listeners`集合。  
  
## <a name="example"></a>範例  
 下列範例示範如何從追蹤中移除預設的追蹤接聽項**接聽程式**集合。  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 [追蹤和偵錯設定結構描述](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
