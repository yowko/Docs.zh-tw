---
title: "loadFromContext MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), LoadFrom context"
  - "managed debugging assistants (MDAs), LoadFrom context"
  - "LoadFrom context"
  - "LoadFromContext MDA"
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
caps.latest.revision: 8
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 8
---
# loadFromContext MDA
當組件 \(Assembly\) 載入至 `LoadFrom` 內容時，`loadFromContext` Managed 偵錯助理 \(MDA\) 就會啟動。  這種情況的發生，可能是呼叫 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> 或其他類似方法的結果。  
  
## 症狀  
 一些載入器方法的使用，可能會使組件載入到 `LoadFrom` 內容中。  這種內容的使用，可能會造成序例化 \(Serialization\)、轉型 \(Casting\) 及相依性解決方式出現未預期行為。  通常，都會建議將組件載入 `Load` 內容以避免這些問題。  要判斷組件已載入至何種內容，而不使用這個 MDA 是相當困難的。  
  
## 原因  
 一般而言，如果是從 `Load` 內容之外的路徑載入 \(像是全域組件快取或 <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=fullName> 屬性\)，組件都會載入至 `LoadFrom` 內容。  
  
## 解決方式  
 設定應用程式，以便不再需要 <xref:System.Reflection.Assembly.LoadFrom%2A> 呼叫。  您可以使用下列技巧來做到這點：  
  
-   在全域組件快取中安裝組件。  
  
-   將組件放置在 <xref:System.AppDomain> 的 <xref:System.AppDomainSetup.ApplicationBase%2A> 目錄中。  在預設網域的情況下，<xref:System.AppDomainSetup.ApplicationBase%2A> 目錄會包含啟動處理序的可執行檔。  如果不方便移動組件，也可能需要建立新的 <xref:System.AppDomain>。  
  
-   如果相依的組件位於相對於可執行檔的子目錄中，請將探查路徑加入您的應用程式組態 \(.config\) 檔或次要應用程式定義域中。  
  
 在每種情況下，程式碼都能變更為使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 方法。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 沒有任何影響。  此 MDA 會報告用來做為載入要求結果的內容。  
  
## Output  
 這個 MDA 會報告組件已載入至 `LoadFrom` 內容。  而且會指定組件和路徑的簡單名稱。  另外也會建議避免使用 `LoadFrom` 內容的降低方法。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 下列程式碼範例示範會啟動這個 MDA 的情況：  
  
```  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## 請參閱  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)