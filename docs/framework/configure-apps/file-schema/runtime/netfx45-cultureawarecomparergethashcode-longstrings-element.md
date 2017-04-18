---
title: "&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; 項目 | Microsoft Docs"
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
  - "NetFx45_CultureAwareComparerGetHashCode_LongStrings 項目"
  - "<NetFx45_CultureAwareComparerGetHashCode_LongStrings> 項目"
  - "GetHashCode 方法"
  - "雜湊碼, 計算"
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; 項目
指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> 方法的雜湊碼。  
  
 \<configuration\>  
\<runtime\>  
\<NetFx45\_CultureAwareComparerGetHashCode\_LongStrings\>  
  
## 語法  
  
```vb  
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定通用語言執行平台是否會在計算雜湊碼時配置固定數量的記憶體。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|0|通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> 方法配置可變的記憶體數量來計算雜湊碼。 這是預設值。|  
|1|通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> 方法配置固定的記憶體數量來計算雜湊碼。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## 備註  
 根據預設，通用語言執行平台會為 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> 方法配置可變的記憶體數量，因此，當方法嘗試計算長度超過數百萬個字元的超大型字串雜湊碼時，就可能擲回 <xref:System.ArgumentException>。 藉由將這個項目加入至應用程式組態檔，並將其 `enabled` 屬性設定為 "1"，就可以指定 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> 方法使用替代演算法配置固定的記憶體數量來計算雜湊碼。  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` 項目不會在 [!INCLUDE[win8](../../../../../includes/win8-md.md)] \(含\) 以後版本中使用。  
  
## 請參閱  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName>   
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)