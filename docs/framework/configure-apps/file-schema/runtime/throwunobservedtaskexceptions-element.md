---
title: "&lt;ThrowUnobservedTaskExceptions&gt; 項目 | Microsoft Docs"
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
  - "<ThrowUnobservedTaskExceptions> 項目"
  - "ThrowUnobservedTaskExceptions 項目"
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# &lt;ThrowUnobservedTaskExceptions&gt; 項目
指定未處理的工作例外狀況是否應該結束執行中處理序。  
  
## 語法  
  
```vb  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定未處理的工作例外狀況是否應該結束執行中處理序。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|`false`|不會因為未處理的工作例外狀況而結束執行中的處理序。  這是預設值。|  
|`true`|因為未處理的工作例外狀況而結束執行中的處理序。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含與執行階段初始化選項有關的資訊。|  
|||  
  
## 備註  
 如果與 <xref:System.Threading.Tasks.Task> 相關的例外狀況未被檢視，就沒有 <xref:System.Threading.Tasks.Task.Wait%2A> 作業，也不會附加父代，還有未讀取工作例外狀況的 <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=fullName> 屬性視為未觀察。  
  
 在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]中，根據預設，如果內含未觀察例外狀況的 <xref:System.Threading.Tasks.Task> 已進行記憶體回收，則完成項擲回例外狀況並結束處理序。  處理序終止取決於記憶體回收和結束時間。  
  
 為了方便開發人員撰寫以工作為基礎的非同步程式碼， [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 變更未觀察的例外狀況的預設行為。  未觀察的例外狀況仍然會引發 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> 事件，不過根據預設，處理序不會結束。  相反地，例外狀況會在引發事件後忽略，不論事件處理常式是否觀察例外狀況。  
  
 在 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]中，您可以在應用程式組態檔中使用 [\<ThrowUnobservedTaskExceptions\> 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) 啟用[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 行為擲回例外狀況。  
  
 您可以在下列其中一個方式，以指定例外狀況行為：  
  
-   藉由設定環境變數 `COMPlus_ThrowUnobservedTaskExceptions`\(`set COMPlus_ThrowUnobservedTaskExceptions=1`\) 。  
  
-   藉由在 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework 索引鍵設定註冊 DWORD 值 ThrowUnobservedTaskExceptions \= 1。  
  
## 範例  
 下列範例示範如何使用應用程式組態檔，來啟用擲回工作中的例外狀況。  
  
```  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
  
```  
  
## 範例  
 下列範例示範未觀察的例外狀況如何從工作擲回。  程式碼必須以發行程式執行來正確運作。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)