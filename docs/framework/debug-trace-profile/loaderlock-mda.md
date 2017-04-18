---
title: "loaderLock MDA | Microsoft Docs"
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
  - "deadlocks [.NET Framework]"
  - "LoaderLock MDA"
  - "MDAs (managed debugging assistants), loader locks"
  - "managed debugging assistants (MDAs), loader locks"
  - "operating system loader locks"
  - "loader locks"
  - "locks, threads"
ms.assetid: 8c10fa02-1b9c-4be5-ab03-451d943ac1ee
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# loaderLock MDA
`loaderLock` Managed 偵錯助理 \(MDA\) 可偵錯到嘗試在持有 Microsoft Windows 作業系統載入器鎖定的執行緒上執行 Managed 程式碼的動作。這樣的執行是不合法的，因為它可能會產生死結，並在作業系統的載入器初始化 DLL 之前就使用 DLL。  
  
## 症狀  
 在作業系統的載入器鎖定內執行程式碼時，最常發生的失敗是在執行緒嘗試呼叫其他也需要此載入器鎖定的 Win32 函式時，會產生死結。這類函式的範例有 `LoadLibrary`、`GetProcAddress`、`FreeLibrary` 和 `GetModuleHandle`。應用程式可能不會直接呼叫這些函式；Common Language Runtime \(CLR\) 可能會在發生類似 <xref:System.Reflection.Assembly.Load%2A> 的較高層次呼叫或平台叫用方法的第一個呼叫之後，呼叫這些函式。  
  
 如果執行緒正在等候另一個執行緒開始或完成，也可能會發生死結。當執行緒開始或完成執行時，它必須取得作業系統的載入器鎖定，才能將事件傳遞給受影響的 DLL。  
  
 最後，也可能會有以下的情況發生：在作業系統的載入器正確初始化 DLL 之前發生這些 DLL 的呼叫。不像死結失敗可以透過檢查與該死結有關的所有執行緒之堆疊來獲得診斷，要診斷是否使用未初始化的 DLL 卻不使用這個 MDA，是非常困難的。  
  
## 原因  
 針對 .NET Framework 1.0 或 1.1 版所建置的混合 Managed\/Unmanaged C\+\+ 組件，通常會嘗試在載入器鎖定內執行 Managed 程式碼，除非有採取特殊的防護動作，例如，與 **\/NOENTRY** 連結。如需這些問題的詳細描述，請參閱 MSDN Library 中的＜混合 DLL 載入程序＞。  
  
 針對 .NET Framework 2.0 版所建置的混合 Managed\/Unmanaged C\+\+ 組件比較不容易受到這些問題的影響，這些組件與使用違反作業系統規則的 Unmanaged DLL 之應用程式有相同降低的風險。例如，如果 Unmanaged DLL 的 `DllMain` 進入點呼叫 `CoCreateInstance` 來取得已公開給 COM 的 Managed 物件，則結果是嘗試在載入器鎖定內執行 Managed 程式碼。  如需 .NET Framework 2.0 版 \(含\) 以後版本中載入器鎖定的詳細資訊，請參閱[混合組件的初始化](../Topic/Initialization%20of%20Mixed%20Assemblies.md)。  
  
## 解決方式  
 在 Visual C\+\+ .NET 2002 和 Visual C\+\+ .NET 2003 中，使用 `/clr` 編譯器選項編譯的 DLL，可能會在載入時造成非決定性的死結，這個問題稱為混合 DLL 載入或載入器鎖定問題。  Visual C\+\+ 2005 \(含\) 以後的版本幾乎已經解決混合 DLL 載入程序中，所有不具決定性的鎖定問題。  然而在一些情況下，仍然有可能 \(具決定性地\) 發生載入器鎖定。  如需其餘載入器鎖定問題之原因和解決方式的詳細說明，請參閱[混合組件的初始化](../Topic/Initialization%20of%20Mixed%20Assemblies.md)。  如果該主題並未說明您的載入器鎖定問題，您必須檢查執行緒的堆疊，以判斷載入器鎖定發生的原因及更正問題的方法。  查看堆疊追蹤，以找出啟動這個 MDA 的執行緒。此執行緒嘗試以不合法的方式呼叫 Managed 程式碼，同時也持有作業系統的載入器鎖定。您可能會在堆疊上看到 DLL 的 `DllMain` 或同等的進入點；在作業系統的規則之下，您可以在這類進入點中合法執行的作業很有限，這些規則預先排除任何 Managed 的執行。  
  
## 對執行階段的影響  
 一般來說，此處理序內會有幾個執行緒鎖死，其中一個執行緒可能是負責執行記憶體回收的執行緒，因此，這個死結可能會對整個處理序產生重大影響。此外，它將會阻止任何需要作業系統的載入器鎖定的其他作業，例如，載入及卸載組件或 DLL 以及啟動或停止執行緒。  
  
 在某些不常見的情況下，也有可能在 DLL 中觸發存取違規或類似問題，而且會在初始化這些 DLL 之前，呼叫這些 DLL。  
  
## Output  
 這個 MDA 報告正在嘗試進行不合法的 Managed 執行；您需要檢查此執行緒的堆疊，以判斷載入器鎖定發生的原因及更正問題的方法。  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <loaderLock/>  
  </assistants>  
</mdaConfig>  
```  
  
## 請參閱  
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)