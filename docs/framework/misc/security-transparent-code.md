---
title: "Security-Transparent Code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "transparent code"
  - "security-transparent code"
ms.assetid: 4f3dd841-82f7-4659-aab0-6d2db2166c65
caps.latest.revision: 24
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 24
---
# Security-Transparent Code
<a name="top"></a> [!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 安全性牽涉到三個互動式的部分：沙箱、權限與強化。 沙箱是指建立隔離定義域的做法，其中將某些程式碼視為完全信任，且限制其他程式碼為沙箱授權集中的權限。 在沙箱授權集內部執行的應用程式程式碼會被視為透明的。也就是說，它無法執行任何可能會影響安全性的作業。 沙箱授權集是依照辨識項 \(<xref:System.Security.Policy.Evidence> 類別\) 決定的。 辨識項會識別沙箱所需的特定權限，以及可建立的沙箱種類。 強化是指讓透明程式碼只能在其授權集內部執行。  
  
> [!IMPORTANT]
>  安全性原則是舊版 .NET Framework 中的重要項目。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，安全性原則就已過時。 安全性原則的刪除獨立於安全性透明規則。 如需這項變更之作用的相關資訊，請參閱[Code Access Security Policy Compatibility and Migration](../../../docs/framework/misc/code-access-security-policy-compatibility-and-migration.md)。  
  
 本主題將詳細描述透明度模型。 它包含以下各節：  
  
-   [透明度模型的用途](#purpose)  
  
-   [指定透明度層級](#level)  
  
-   [透明度強化](#enforcement)  
  
<a name="purpose"></a>   
## 透明度模型的用途  
 透明度是一種強化機制，將當做應用程式一部分執行的程式碼與當做基礎結構一部分執行的程式碼分隔。 透明度在可以執行授權事項 \(例如呼叫機器碼\) 的程式碼 \(關鍵程式碼\) 和不能執行授權事項的程式碼 \(透明程式碼\) 之間畫出了一條界線。 透明程式碼可以在其運作的權限集合界限內執行命令，但是無法執行、衍生自關鍵程式碼或包含關鍵程式碼。  
  
 透明度強化的主要目標是提供簡單、有效率的機制，依據權限來隔離不同程式碼群組。 在沙箱模型的內容中，這些權限群組為完全信任 \(也就是不受限制\) 或部分信任 \(也就是限制為授與沙箱的權限集合\)。  
  
> [!IMPORTANT]
>  透明度模型超越了程式碼存取安全性。 透明度是由 Just\-In\-Time 編譯器強制執行，而且保持有效，不論組件的授權集為何 \(包含完全信任\)。  
  
 透明度是在 .NET Framework 2.0 版所引入的，以簡化安全性模型，並且讓您更輕鬆地撰寫和部署安全程式庫與應用程式。 Microsoft Silverlight 中也使用了透明程式碼，以簡化部分信任應用程式的開發。  
  
> [!NOTE]
>  當您開發部分信任應用程式時，必須注意目標主機的權限需求。 您可以開發使用某些主機不允許之資源的應用程式。 雖然這種應用程式在編譯時不會發生任何錯誤，不過在將它載入裝載環境時，就會失敗。 如果您已經使用 Visual Studio 開發應用程式，就可以在來自開發環境的部分信任或受限制的權限集合中啟用偵錯。 如需詳細資訊，請參閱[如何：以限制使用權限偵錯 ClickOnce 應用程式](../Topic/How%20to:%20Debug%20a%20ClickOnce%20Application%20with%20Restricted%20Permissions.md)。 提供給 ClickOnce 應用程式的「計算使用權限」功能也可用於任何部分信任的應用程式。  
  
 [回到頁首](#top)  
  
<a name="level"></a>   
## 指定透明度層級  
 組件層級的 <xref:System.Security.SecurityRulesAttribute> 屬性會明確選取該組件將遵循的 <xref:System.Security.SecurityRuleSet> 規則。 這些規則會在數值層級系統下受組織，其中較高層級表示會比較嚴格地強制執行安全性規則。  
  
 這些層級如下所示：  
  
-   層級 2 \(<xref:System.Security.SecurityRuleSet>\) – [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 透明度規則。  
  
-   層級 1 \(<xref:System.Security.SecurityRuleSet>\) – .NET Framework 2.0 透明度規則。  
  
 這兩個透明度層級之間的主要差異在於，層級 1 不會針對組件外部的呼叫強制執行透明度規則，而且這主要是為了相容性而使用。  
  
> [!IMPORTANT]
>  您應該僅針對相容性指定層級 1 透明度；也就是說，您應該僅針對使用 .NET Framework 3.5 或更早版本 \(使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> 屬性或沒有使用透明度模型\) 所開發的程式碼指定層級 1。 例如，對於允許來自部分信任呼叫端 \(APTCA\) 之呼叫的 .NET Framework 2.0 組件，請使用層級 1 透明度。 對於針對 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 所開發的程式碼，請一律使用層級 2 透明度。  
  
### 層級 2 透明度  
 層級 2 透明度是 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 引入的。 此模型的三個原則是透明程式碼、安全性安全關鍵程式碼和安全性關鍵程式碼。  
  
-   不論授與給透明程式碼的權限為何 \(包含完全信任\)，透明程式碼只能呼叫其他透明程式碼或安全性安全關鍵程式碼。 如果此程式碼受到部分信任，就只能執行該定義域之權限集合所允許的動作。 透明程式碼無法進行下列作業：  
  
    -   執行 <xref:System.Security.CodeAccessPermission.Assert%2A> 作業或提高權限。  
  
    -   包含不安全或無法驗證的程式碼。  
  
    -   直接呼叫關鍵程式碼。  
  
    -   呼叫機器碼或含有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 屬性的程式碼。  
  
    -   呼叫 <xref:System.Security.Permissions.SecurityAction> 所保護的成員。  
  
    -   繼承自關鍵類型。  
  
     此外，透明方法無法覆寫關鍵虛擬方法或實作關鍵介面方法。  
  
-   安全性安全關鍵程式碼受到完全信任，但是可由透明程式碼呼叫。 它會公開完全信任程式碼的有限介面區。 正確性和安全性驗證會在安全關鍵程式碼中進行。  
  
-   雖然安全性關鍵程式碼可以呼叫任何程式碼，而且受到完全信任，但是無法由透明程式碼呼叫。  
  
### 層級 1 透明度  
 層級 1 透明度模型是在 .NET Framework 2.0 版中所引入的，可讓開發人員減少受限於安全性稽核的程式碼數量。 雖然層級 1 透明度可公開使用於 2.0 版中，不過它主要是針對安全性稽核的用途，於 Microsoft 中所使用。 開發人員可以透過註釋宣告哪些類型和成員可以提高安全性和執行其他受信任動作 \(安全性關鍵\)，以及哪些類型和成員無法執行這些作業 \(安全性透明\)。 識別為透明的程式碼不需要高階安全性稽核。 層級 1 透明度指出透明度強制執行已限制於組件內部。 換句話說，識別為安全性關鍵的任何公用類型或成員只在組件內部為安全性關鍵的。 從組件外部呼叫這些類型和成員時，如果您想要針對它們強制執行安全性，就必須使用完全信任的連結要求。 如果您沒有這樣做，就會將公開可見的安全性關鍵類型和成員視為安全性安全關鍵的，而且可由組件外部的部分信任程式碼所呼叫。  
  
 層級 1 透明度模型具有下列限制：  
  
-   公用的安全性關鍵類型和成員可從安全性透明程式碼存取。  
  
-   透明度註釋只在組件內部強制執行。  
  
-   安全性關鍵類型和成員必須使用連結要求，針對來自組件外部的呼叫強制執行安全性。  
  
-   繼承規則不會強制執行。  
  
-   在完全信任中執行時，透明程式碼有可能會執行有害的事。  
  
 [回到頁首](#top)  
  
<a name="enforcement"></a>   
## 透明度強化  
 透明度規則會等到計算出透明度之後才會強制執行。 此時，如果違反了透明度規則，就會擲回 <xref:System.InvalidOperationException>。 計算透明度的時間取決於多個因素，而且無法預測。 透明度的計算會盡可能延後。 在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 中，組件層級的透明度計算會比在 .NET Framework 2.0 中更早發生。 唯一能保證的是透明度計算會在需要時發生。 這與 Just\-In\-Time \(JIT\) 編譯器如何變更進行方法之編譯的時間點很類似，也和其如何變更偵測該方法中任何錯誤的時間點很類似。 如果您的程式碼沒有任何透明度錯誤，透明度計算就會是不可見的。  
  
## 請參閱  
 [Security\-Transparent Code, Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md)   
 [Security\-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md)