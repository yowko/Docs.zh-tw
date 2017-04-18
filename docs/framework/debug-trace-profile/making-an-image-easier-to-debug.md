---
title: "使映像偵錯更容易 | Microsoft Docs"
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
  - "影像 [.NET Framework]，偵錯"
  - "用於偵錯的可執行檔映像"
  - "偵錯 [.NET Framework]，可執行檔映像以便"
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# 使映像偵錯更容易
當編譯 Unmanaged 程式碼時，您可以設定 IDE 參數或命令列選項，配置一個可執行映像做為偵錯用。  例如，您可以使用 Visual C\+\+ 中的 \/**Zi** 命令列選項，詢問它是否要發出偵錯符號檔 \(副檔名為 .pdb\)。  同樣地，\/**Od** 命令列選項是讓編譯器知道要停用最佳化。  最終的程式碼執行速度可能會稍慢，但對偵錯而言則更容易，因此有必要執行這項作業。  
  
 當編譯 .NET Framework Managed 程式碼時，如 Visual C\+\+、Visual Basic 和 C\# 這類的編譯器會將它們的原始程式編入 Microsoft Intermediate Language \(MSIL\)。  然後在執行前，由 JIT 將 MSIL 編入原生機器碼 \(Machine Code\)。  而在 Unmanaged 程式碼上，您可以設定 IDE 參數或命令列選項，配置一個可執行映像做為偵錯用。  此外，您也可以將偵錯用的 JIT 編譯 \(Compilation\) 設定為相同的方式。  
  
 這個 JIT 組態有兩個重點：  
  
-   您可以要求 JIT 編譯器產生追蹤資訊。  如此偵錯工具可使 MSIL 的鏈結和它的對應機器碼相符，並追蹤儲存區域變數和函式引數的位置。在 .NET Framework 2.0 版中，JIT 編譯器會固定產生追蹤資訊，因此不需加以要求。  
  
-   您可以要求 JIT 編譯器不最佳化最終的機器碼。  
  
 通常，產生 MSIL 的編譯器會依照您指定的 IDE 參數或命令列選項 \(如 \/**Od**\)，設定適當的 JIT 編譯器選項。  
  
 在某些情況下，您可能會想要變更 JIT 編譯器的行為，讓它產生的機器碼 \(Machine Code\) 更容易偵錯。  例如，您可能會想要針對正式版本來產生 JIT 追蹤資訊，或是控制最佳化。  您可以使用初始設定檔案 \(Initialization File\) \(.ini 檔案\) 來進行。  
  
 例如，如果您想要偵錯的組件稱為 MyApp.exe，然後您可以在與 MyApp.exe 相同的資料夾中建立一個文字檔 MyApp.ini，其中包含以下三行程式碼：  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 您可以將每一個選項的值設為 0 或 1，而其他不存在的選項則預設值為 0。  將 `GenerateTrackingInfo` 設為 1 並將 `AllowOptimize` 設為 0 可以提供最容易的偵錯作業。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，JIT 編譯器一定會產生追蹤資訊，不論 `GenerateTrackingInfo` 的值為何；不過，`AllowOptimize` 值仍舊有效。  在使用[Ngen.exe \(Native Image Generator\)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 先行編譯未最佳化的原生映像時，此 .ini 檔必須存在於當 Ngen.exe 執行時，具有 `AllowOptimize=0` 設定的目標資料夾中。  如果您先行編譯了未最佳化的組件，則必須在執行 Ngen.exe 前使用 NGen.exe **\/uninstall** 選項，才能將程式碼先行編譯為最佳化程式碼。  如果此 .ini 檔未存在於資料夾中，則根據預設，Ngen.exe 會將程式碼先行編譯為最佳化程式碼。  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggableAttribute?displayProperty=fullName> 會控制組件的設定。  **DebuggableAttribute** 包含兩個欄位，會記錄 JIT 編譯器是否應該最佳化和 \(或\) 產生追蹤資訊的相關設定。  在 .NET Framework 2.0 版中，JIT 編譯器會固定產生追蹤資訊。  
  
> [!NOTE]
>  對於正式版本組建，編譯器並不會設定任何的 **DebuggableAttribute**。  JIT 編譯器的預設行為是產生最高的效能以及最難偵錯的機器碼。  啟用 JIT 追蹤只些微降低一點效能，而停用最佳化則會對效能造成很大的影響。  
  
> [!NOTE]
>  **DebuggableAttribute** 一次會套用至整個組件，而不是套用至組件內的個別模組。  因此如果已建立組件，開發工具必須將自訂屬性附加至組件中繼資料語彙基元 \(Token\)，否則會附加至名稱為 **System.Runtime.CompilerServices.AssemblyAttributesGoHere** 的類別。  接著 ALink 工具會從每個模組中將這些 **DebuggableAttribute** 屬性升級至其所屬的組件。  如果發生衝突，即表示 ALink 作業失敗。  
  
> [!NOTE]
>  在 .NET Framework 1.0 版中，當指定了 **\/clr** 和 **\/Zi** 編譯器選項時，Microsoft Visual C\+\+ 編譯器會新增 **DebuggableAttribute** 。  在 .NET Framework 1.1 版中，您必須以手動方式在程式碼中新增 **DebugabbleAttribute**，或使用 **\/ASSEMBLYDEBUG** 連結器選項。  
  
## 請參閱  
 [Debugging, Tracing, and Profiling](../../../docs/framework/debug-trace-profile/index.md)   
 [Enabling JIT\-Attach Debugging](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)   
 [Enabling Profiling](http://msdn.microsoft.com/zh-tw/3b669676-f0e0-4ebf-8674-68986dd2020d)