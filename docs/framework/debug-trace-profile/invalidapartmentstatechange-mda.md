---
title: "invalidApartmentStateChange MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), invalid apartment state"
  - "managed debugging assistants (MDAs), invalid apartment state"
  - "InvalidApartmentStateChange MDA"
  - "invalid apartment state changes"
  - "threading [.NET Framework], apartment states"
  - "apartment states"
  - "threading [.NET Framework], managed debugging assistants"
  - "COM apartment states"
ms.assetid: e56fb9df-5286-4be7-b313-540c4d876cd7
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# invalidApartmentStateChange MDA
下列兩個問題中的任何一個問題都會啟動 `invalidApartmentStateChange` Managed 偵錯助理 \(MDS\)：  
  
-   嘗試變更執行緒的 COM Apartment 狀態，卻已經由 COM 初始化為不同的 Apartment 狀態。  
  
-   執行緒的 COM Apartment 狀態意外變更。  
  
## 症狀  
  
-   執行緒的 COM Apartment 狀態不是要求的狀態。  如此會使 Proxy 被具有不同於目前執行緒模式的 COM 元件所使用。  這樣在透過未針對跨 Apartment 封送處理 \(Marshaling\) 而設定的介面呼叫 COM 物件時，就會造成 <xref:System.InvalidCastException> 的擲回。  
  
-   執行緒的 COM Apartment 狀態與預期不同。  這樣在[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md) \(RCW\) 進行呼叫時，就會造成具有 RPC\_E\_WRONG\_THREAD 之 HRESULT 的 <xref:System.Runtime.InteropServices.COMException>，以及 <xref:System.InvalidCastException>。  這樣也會使一些單一執行緒 COM 元件同時被多個執行緒存取，並且因而導致損毀或資料遺失。  
  
## 原因  
  
-   執行緒在先前初始化為不同的 COM Apartment 狀態。  請注意，使用明確或隱含作業，都能設定執行緒的 Apartment 狀態。  明確作業包括 <xref:System.Threading.Thread.ApartmentState%2A?displayProperty=fullName> 屬性，以及 <xref:System.Threading.Thread.SetApartmentState%2A> 和 <xref:System.Threading.Thread.TrySetApartmentState%2A> 方法。  除非在啟動執行緒之前呼叫 <xref:System.Threading.Thread.SetApartmentState%2A>，否則使用 <xref:System.Threading.Thread.Start%2A> 方法建立的執行緒，都會隱含設定為 <xref:System.Threading.ApartmentState>。  除非在主方法上有指定 <xref:System.STAThreadAttribute> 屬性 \(Attribute\)，否則應用程式的主執行緒也會隱含初始化為 <xref:System.Threading.ApartmentState>。  
  
-   在執行緒上呼叫了具有不同並行模型的 `CoUninitialize` 方法 \(或是 `CoInitializeEx` 方法\)。  
  
## 解決方式  
 在執行緒開始執行之前，設定其 Apartment 狀態，或是將 <xref:System.STAThreadAttribute> 屬性或 <xref:System.MTAThreadAttribute> 屬性套用到應用程式的主方法。  
  
 理想上，對於第二種原因，應該修改呼叫 `CoUninitialize` 方法的程式碼以延遲呼叫，直到執行緒將要結束，而且沒有任何 RCW 及其基礎 COM 元件依然由執行緒使用為止。  然而，如果不可能修改呼叫 `CoUninitialize` 方法的程式碼，這樣沒有以這種方式初始化的執行緒就不該使用任何 RCW。  
  
## 對執行階段的影響  
 這個 MDA 對 CLR 無效。  
  
## Output  
 目前執行緒的 COM Apartment 狀態，以及程式碼嘗試套用的狀態。  
  
## 組態  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidApartmentStateChange />  
  </assistants>  
</mdaConfig>  
```  
  
## 範例  
 下列程式碼範例示範會啟動這個 MDA 的情況。  
  
```  
using System.Threading;  
namespace ApartmentStateMDA  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Thread.CurrentThread.SetApartmentState(ApartmentState.STA);  
        }  
    }  
}  
```  
  
## 請參閱  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)