---
title: "&lt;UseRandomizedStringHashAlgorithm&gt; 項目 | Microsoft Docs"
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
  - "<UseRandomizedStringHashAlgorithm> 項目"
  - "UseRandomizedStringHashAlgorithm 項目"
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;UseRandomizedStringHashAlgorithm&gt; 項目
判斷 Common Language Runtime 是否以每個應用程式定義域為基準，計算字串的雜湊碼。  
  
## 語法  
  
```  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定是否以每個應用程式定義域為基準，計算字串的雜湊碼。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`0`|Common Language Runtime 不會計算每個應用程式定義域上字串的雜湊碼。使用單一演算法來計算字串的雜湊程式碼。  這是預設值。|  
|`1`|Common Language Runtime 會以每個應用程式定義域為基準，計算字串的雜湊碼。  不同應用程式定義域和不同處理序中的相同字串會有不同的雜湊碼。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
  
## 備註  
 根據預設，<xref:System.StringComparer> 類別和 <xref:System.String.GetHashCode%2A?displayProperty=fullName> 方法會使用跨應用程式定義域產生一致雜湊碼的單一雜湊演算法。  此設定相當於將 `<UseRandomizedStringHashAlgorithm>` 項目的 `enabled` 屬性設定為 `0`。  這是 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 使用的雜湊演算法。  
  
 <xref:System.StringComparer> 類別和 <xref:System.String.GetHashCode%2A?displayProperty=fullName> 方法也可以使用不同的雜湊演算法，在每個應用程式定義域計算雜湊碼。  因此，對等字串的雜湊碼在不同應用程式定義域之間會有所不同。  這是加入宣告功能；若要使用它，您必須將 `<UseRandomizedStringHashAlgorithm>` 項目的 `enabled` 屬性設定為 `1`。  
  
 在雜湊資料表的字串查閱通常是 O\(1\) 運算。  不過，當發生大量碰撞時，查閱可能會變成 O\(n<sup>2</sup>\) 運算。  您可以使用 `<UseRandomizedStringHashAlgorithm>` 組態項目為每一個應用程式定義域產生一個隨機雜湊演算法，進而限制可能發生的衝突數目，特別是在計算雜湊碼時做為根據的索引鍵以使用者輸入的資料為準時。  
  
## 範例  
 下列範例定義 `DisplayString` 類別，包含私用字串常數 `s`，其值為 "This is a string"。它也包含 `ShowStringHashCode` 方法，這個方法會將字串值及其雜湊碼與方法執行所在之應用程式定義域的名稱一起顯示。  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 當您在沒有提供組態檔的情況下執行此範例，它會顯示類似下列的輸出。  請注意，字串的雜湊碼在兩個應用程式定義域中相同。  
  
```  
  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
  
```  
  
 不過，如果您將下列組態檔加入至範例的目錄，然後執行這個範例，相同字串的雜湊碼將會因為應用程式定義域不同而有所不同。  
  
```  
  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
  
```  
  
 當組態檔存在時，這個範例會顯示下列輸出：  
  
```  
  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
  
```  
  
## 請參閱  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.String.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>