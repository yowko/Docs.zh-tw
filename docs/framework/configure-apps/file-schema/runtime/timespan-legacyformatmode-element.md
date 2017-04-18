---
title: "&lt;TimeSpan_LegacyFormatMode&gt; 項目 | Microsoft Docs"
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
  - "<TimeSpan_LegacyFormatMode> 項目"
  - "TimeSpan_LegacyFormatMode 項目"
ms.assetid: 865e7207-d050-4442-b574-57ea29d5e2d6
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# &lt;TimeSpan_LegacyFormatMode&gt; 項目
決定執行階段是否會保留使用 <xref:System.TimeSpan?displayProperty=fullName> 值的格式化作業中的舊版行為。  
  
## 語法  
  
```  
<TimeSpan_LegacyFormatMode    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否使用具 <xref:System.TimeSpan?displayProperty=fullName> 值的舊版格式化行為。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|執行階段不會還原舊版的格式化行為。|  
|`true`|執行階段會還原舊版的格式化行為。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
 自 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，<xref:System.TimeSpan?displayProperty=fullName> 結構會實作 <xref:System.IFormattable> 介面，並支援以標準及自訂格式字串進行格式化作業。  如果剖析方法遇到不支援的格式規範或格式字串，就會擲回 <xref:System.FormatException>。  
  
 在舊版的.NET Framework 中，<xref:System.TimeSpan> 結構並未實作 <xref:System.IFormattable>，且不支援格式字串。  不過，許多開發人員錯誤地假設 <xref:System.TimeSpan> 確實支援一組格式字串，並且在 [複合格式化作業](../../../../../docs/standard/base-types/composite-formatting.md)中使用這些字串搭配<xref:System.String.Format%2A?displayProperty=fullName> 之類的方法。  正常情況下，如果型別會實作 <xref:System.IFormattable> 並支援格式化字串，呼叫具有不支援格式字串的格式化方法通常會擲回 <xref:System.FormatException>。  不過，<xref:System.TimeSpan> 並未實作 <xref:System.IFormattable>，因此執行階段已忽略格式字串，改而呼叫 <xref:System.TimeSpan.ToString?displayProperty=fullName> 方法。  這表示，雖然格式字串對於格式化作業沒有作用，但它們的存在並不會導致 <xref:System.FormatException>。  
  
 當舊版程式碼傳遞複合格式化方法和不正確的格式字串，且無法重新編譯程式碼時，您可以使用 `<TimeSpan_LegacyFormatMode>` 項目還原舊版的 <xref:System.TimeSpan> 行為。  當您將這個項目的 `enabled` 屬性設為 `true`時，複合格式方法會造成呼叫 <xref:System.TimeSpan.ToString?displayProperty=fullName> 而非 <xref:System.TimeSpan.ToString%28System.String%2CSystem.IFormatProvider%29?displayProperty=fullName>，而且不會擲回 <xref:System.FormatException>。  
  
## 範例  
 下列範例會執行個體化 <xref:System.TimeSpan> 物件，並嘗試使用不支援的標準格式字串將它以 <xref:System.String.Format%28System.String%2CSystem.Object%29?displayProperty=fullName> 方法格式化。  
  
 [!code-csharp[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/timespan.breakingchanges/cs/legacyformatmode1.cs#1)]
 [!code-vb[TimeSpan.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/timespan.breakingchanges/vb/legacyformatmode1.vb#1)]  
  
 在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 或較舊版本上執行該範例時，它會顯示下列輸出：  
  
```  
12:30:45  
```  
  
 如果您在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 或更新的版本上執行範例，會出現相當不同的結果：  
  
```  
Invalid Format  
```  
  
 不過，如果您將下列組態檔加入到範例的目錄中，然後在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 或更新的版本上執行該範例，則輸出會與在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上執行範例時產生的輸出完全相同。  
  
```  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <TimeSpan_LegacyFormatMode enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)