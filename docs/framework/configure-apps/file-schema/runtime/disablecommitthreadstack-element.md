---
title: "&lt;disableCommitThreadStack&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<disableCommitThreadStack> 項目"
  - "disableCommitThreadStack 項目"
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;disableCommitThreadStack&gt; 項目
指定是否在執行緒啟動時認可完整執行緒堆疊。  
  
 \<configuration\>  
\<runtime\>  
\<disableCommitThreadStack\>  
  
## 語法  
  
```  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|enabled|必要屬性。<br /><br /> 指定是否停用在執行緒啟動時認可完整執行緒堆疊 \(預設行為\)。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|0|不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。|  
|1|不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之所有組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。 如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。  
  
> [!NOTE]
>  未受管理的主機可以在 [STARTUP\_FLAGS](../../../../../ocs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) 列舉中使用 `STARTUP_DISABLE_COMMITTHREADSTACK` 啟動旗標，來達到相同的結果。  
  
## 範例  
 下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。  
  
```  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)