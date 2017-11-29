---
title: "使映像偵錯更容易"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 46a9c11f3545e5d2b9f91572a87ee2614810e4d0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="making-an-image-easier-to-debug"></a>使映像偵錯更容易
當編譯 Unmanaged 程式碼時，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。 例如，您可以在 Visual C++ 中使用 /**Zi** 命令列選項，要求它發出偵錯符號檔 (副檔名為 .pdb)。 同樣地，/**Od** 命令列選項會通知編譯器停用最佳化。 要是此為必要，產生的程式碼執行速度較慢，但更容易偵錯。  
  
 當編譯 .NET Framework Managed 程式碼時，Visual C++、Visual Basic 和 C# 等編譯器會將其原始程式編譯成 Microsoft Intermediate Language (MSIL)。 MSIL 會在剛好執行前，接著以 JIT 方式編譯為原生機器碼。 如同使用 Unmanaged 程式碼一樣，您可以設定 IDE 參數或命令列選項，設定可執行映像進行偵錯。 此外，您可以極近似的方式設定 JIT 編譯進行偵錯。  
  
 JIT 組態有兩個層面：  
  
-   您可以要求 JIT 編譯器產生追蹤資訊。 這可讓偵錯工具的機器碼對應項目對應上 MSIL 鏈結，追蹤本機變數和函式引數的儲存位置。  在 .NET Framework 2.0 版中，JIT 編譯器一律會產生追蹤資訊，因此不需要提出要求。  
  
-   您可以要求 JIT 編譯器不要最佳化產生的機器碼。  
  
 一般來說，產生 MSIL 的編譯器會根據您指定的 IDE 參數或命令列選項，例如，/**Od**，適當地設定 JIT 編譯器選項。  
  
 在某些情況下，您可能想要變更 JIT 編譯器的行為，以便更容易偵錯它產生的機器碼。 例如，您可能想要產生零售組建的 JIT 追蹤資訊，或控制最佳化。 您可以使用初始設定 (.ini) 檔案完成此作業。  
  
 例如，如果您想要偵錯的組件稱為 MyApp.exe，則可以在和 MyApp.exe 相同的資料夾中，建立名為 MyApp.ini 的文字檔，包含這三行：  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 每個選項的值可以設成 0 或 1，任何不存在的選項預設值皆為 0。 將 `GenerateTrackingInfo` 設為 1、`AllowOptimize` 設為 0，會提供最簡單的偵錯。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，JIT 編譯器一律會產生追蹤資訊，無論 `GenerateTrackingInfo` 的值為何；不過，`AllowOptimize` 值仍然有效。 當使用 [Ngen.exe (原生映像產生器)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) 先行編譯未最佳化的原生映像時，在執行 Ngen.exe 時，.ini 檔案中必須位在目標資料夾中且附有 `AllowOptimize=0`。 如已先行編譯未最佳化的組件，您必須先使用 NGen.exe **/uninstall** 選項移除先行編譯的程式碼，再重新執行 Ngen.exe 先行編譯最佳化的程式碼。 如果資料夾中沒有 .ini 檔案，Ngen.exe 預設會將程式碼預先編譯為最佳化。  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggableAttribute?displayProperty=nameWithType> 控制組件的設定。 **DebuggableAttribute** 包含兩個欄位，記錄 JIT 編譯器是否應該最佳化的設定，及/或產生追蹤資訊。 在 .NET Framework 2.0 版中，JIT 編譯器一律會產生追蹤資訊。  
  
> [!NOTE]
>  編譯器不會為零售組建設定任何 **DebuggableAttribute**。 JIT 編譯器預設行為是產生最高的效能，幾乎不偵錯機器碼。 啟用 JIT 追蹤會略降低效能，而停用最佳化則會大幅降低效能。  
  
> [!NOTE]
>  **DebuggableAttribute** 是一次套用至整個組件，不是一一套用到組件中的個別模組。 因此，開發工具必須將自訂屬性附加至組件中繼資料權杖 (如已建立組件)，或附加至稱為 **System.Runtime.CompilerServices.AssemblyAttributesGoHere** 的類別。 接著，ALink 工具會將這些 **DebuggableAttribute** 屬性從每個模組升級至其所屬的組件。 如果發生衝突，ALink 作業就會失敗。  
  
> [!NOTE]
>  在 .NET Framework 1.0 版中，當指定 **/clr** 和 **/Zi** 編譯器選項時，Microsoft Visual C++ 編譯器會新增 **DebuggableAttribute**。 在 .NET Framework 1.1 版中，您必須在程式碼中手動新增 **DebugabbleAttribute**，或使用 **/ASSEMBLYDEBUG** 連結器選項。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯、追蹤和程式碼剖析](../../../docs/framework/debug-trace-profile/index.md)  
 [啟用 JIT 附加偵錯](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 [啟用分析](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)
