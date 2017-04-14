---
title: "&lt;enforceFIPSPolicy&gt; 項目 | Microsoft Docs"
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
  - "<enforceFIPSPolicy> 項目"
  - "enforceFIPSPolicy 項目"
  - "聯邦資訊處理標準 (FIPS)"
  - "FIPS"
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;enforceFIPSPolicy&gt; 項目
指定是否強制電腦組態要求，也就是加密演算法必須遵守聯邦資訊處理標準 \(FIPS\)。  
  
## 語法  
  
```  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|enabled|必要屬性。<br /><br /> 指定是否啟用強制計算組態要求，也就是加密演算法必須符合 FIPS。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`true`|如果您的電腦設定為要求加密演算法相容於 FIPS，則會強制該需求。  如果類別實作不相容於 FIPS 的演算法，該類別的建構函式或 `Create` 方法會在執行於該電腦時擲回例外狀況。  這是預設值。|  
|`false`|應用程式使用的加密演算法不需符合 FIPS，無論電腦組態為何。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 從 .NET Framework 2.0 開始，建立實作加密演算法的類別由電腦的組態控制。  如果電腦配置為要求符合 FIPS，演算法和類實現不是與 FIPS 相容的演算法，任何嘗試建立該類別的執行個體都將擲回例外狀況。  建構函式會擲回 <xref:System.InvalidOperationException> 例外狀況，而 `Create` 方法則擲回包含內部 <xref:System.InvalidOperationException> 例外狀況的 <xref:System.Reflection.TargetInvocationException> 例外狀況。  
  
 如果您的應用程式執行於組態需要符合 FIPS 的電腦，且您的應用程式使用的演算法不相容於 FIPS，您可以在設定檔中使用此項目，防止 common language runtime \(CLR\) 強制 FIPS 相容。  這個項目是在 [!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)] 中引進的。  
  
## 範例  
 下列範例示範如何防止 CLR 強制要求符合 FIPS 標準。  
  
```  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [Cryptography Model](../../../../../docs/standard/security/cryptography-model.md)