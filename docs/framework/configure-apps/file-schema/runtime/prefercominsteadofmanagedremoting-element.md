---
title: "&lt;PreferComInsteadOfManagedRemoting&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<PreferComInsteadOfManagedRemoting> 項目"
  - "PreferComInsteadOfManagedRemoting 項目"
ms.assetid: a279a42a-c415-4e79-88cf-64244ebda613
caps.latest.revision: 17
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 17
---
# &lt;PreferComInsteadOfManagedRemoting&gt; 項目
指定對於所有跨應用程式定義域界限的呼叫，執行階段是否會使用 COM Interop 而非遠端處理。  
  
## 語法  
  
```  
<PreferComInsteadOfManagedRemoting enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指示執行階段是否跨應用程式定義域界限使用 COM Interop，而不使用遠端處理。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|執行階段將會跨應用程式定義域界限使用遠端處理。  這是預設值。|  
|`true`|執行階段將會跨應用程式定義域界限使用 COM Interop。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 當您將 `enabled` 屬性設定為 `true` 時，執行階段的行為如下：  
  
-   當[IUnknown](http://go.microsoft.com/fwlink/?LinkId=148003)介面透過 COM 介面進入網域時，執行階段不會為了[IManagedObject](../../../../../ocs/framework/unmanaged-api/hosting/imanagedobject-interface.md) 介面而呼叫 [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) 。  而是建構[執行階段可呼叫包裝函式](../../../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW\) 包裝該物件。  
  
-   收到此定義域中所建立之任何 [COM 可呼叫包裝函式](../../../../../docs/framework/interop/com-callable-wrapper.md) \(CCW\) 之 [IManagedObject](../../../../../ocs/framework/unmanaged-api/hosting/imanagedobject-interface.md) 介面的 `QueryInterface` 呼叫時，執行階段會傳回 E\_NOINTERFACE。  
  
 這兩個行為可確保跨應用程式定義域界限對 Managed 物件之間 COM 介面的所有呼叫都會使用 COM 與 COM Interop，而不使用遠端處理。  
  
## 範例  
 在下列範例中，會示範如何指定執行階段應該跨隔離界限使用 COM Interop：  
  
```  
<configuration>  
  <runtime>  
    <PreferComInsteadOfManagedRemoting enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)