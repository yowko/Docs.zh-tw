---
title: "bindingFailure MDA | Microsoft Docs"
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
  - "binding failure"
  - "binding, failures"
  - "MDAs (managed debugging assistants), binding failures"
  - "assemblies [.NET Framework], binding failures"
  - "managed debugging assistants (MDAs), binding failures"
  - "BindingFailure MDA"
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# bindingFailure MDA
當組件 \(Assembly\) 載入失敗時，`bindingFailure` Managed 偵錯助理 \(MDA\) 就會啟動。  
  
## 症狀  
 程式碼已經嘗試使用靜態參考或其中一個載入器方法 \(例如 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> 或 <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>\)，來載入組件。  組件沒有載入，並且擲回 <xref:System.IO.FileNotFoundException> 或 <xref:System.IO.FileLoadException> 例外狀況。  
  
## 原因  
 執行階段無法載入組件時，發生繫結失敗。  繫結失敗可能會是下列其中一種情況所造成的：  
  
-   Common Language Runtime \(CLR\) 找不到要求的組件。  這種情況有很多可能原因，例如未安裝組件，或是未正確地設定應用程式以尋找組件。  
  
-   常見的問題案例，就是將型別傳遞至另一個應用程式定義域，如此便需要 CLR 在其他應用程式定義域中，載入含有該型別的組件。  如果另一個應用程式定義域的設定，與原始應用程式定義域的設定不同，執行階段就可能無法載入組件。  例如，兩個應用程式定義域可能具有不同的 <xref:System.AppDomain.BaseDirectory%2A> 屬性值。  
  
-   要求的組件已損毀，或者已不是組件。  
  
-   嘗試載入組件的程式碼，沒有載入組件的正確程式碼存取安全性權限。  
  
-   使用者認證並未提供讀取檔案的必要使用權限。  
  
## 解決方式  
 第一個步驟是判斷 CLR 為何無法繫結至要求的組件。  有很多原因會使執行階段找不到或無法載入要求的組件，例如＜原因＞一節所列的案例。  建議您進行下列動作以排除繫結失敗的原因：  
  
-   使用 `bindingFailure` MDA 所提供的資料以判斷原因：  
  
    -   執行[Fuslogvw.exe \(Assembly Binding Log Viewer\)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) 以讀取組件繫結器所產生的錯誤記錄檔。  
  
    -   判斷組件是否位於要求的位置。  在 <xref:System.Reflection.Assembly.LoadFrom%2A> 和 <xref:System.Reflection.Assembly.LoadFile%2A> 方法的情況下，都可以輕易地判斷出要求的位置。  在 <xref:System.Reflection.Assembly.Load%2A> 方法的情況中，由於此方法會使用組件識別 \(Identity\) 來繫結，因此，您必須在應用程式定義域的 <xref:System.AppDomain.BaseDirectory%2A> 屬性探查路徑和全域組件快取中，尋找符合該識別的組件。  
  
-   根據先前的判斷解決原因。  下列是可能的解決方式選項：  
  
    -   在全域組件快取中安裝要求的組件，並呼叫   <xref:System.Reflection.Assembly.Load%2A> 方法，依照識別載入組件。  
  
    -   將要求的組件複製到應用程式目錄中，並呼叫 <xref:System.Reflection.Assembly.Load%2A> 方法，依照識別載入組件。  
  
    -   藉由變更 <xref:System.AppDomain.BaseDirectory%2A> 屬性，或是加入私用探查路徑，重新設定發生繫結失敗的應用程式定義域，以加入組件路徑。  
  
    -   變更檔案的存取控制項清單，以允許登入的使用者讀取檔案。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  它只會報告有關繫結失敗的資料。  
  
## Output  
 MDA 會報告載入失敗的組件，其中包括了要求的路徑和 \(或\) 顯示名稱、繫結內容、要求載入的應用程式定義域，以及失敗的原因。  
  
 如果 CLR 無法取得顯示名稱或要求的路徑，這些資料可能會維持空白。  如果失敗的呼叫原先是對 <xref:System.Reflection.Assembly.Load%2A> 方法發出呼叫，執行階段便可能無法判斷組件的顯示名稱。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 下列程式碼範例示範會啟動這個 MDA 的情況：  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## 請參閱  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)