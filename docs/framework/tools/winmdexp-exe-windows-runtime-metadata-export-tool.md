---
title: "Winmdexp.exe (Windows 執行階段中繼資料匯出工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Runtime Metadata Export Tool
- Winmdexp.exe
ms.assetid: d2ce0683-343d-403e-bb8d-209186f7a19d
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 723f724663cb7f08814327a04193f96db7f02ed0
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="winmdexpexe-windows-runtime-metadata-export-tool"></a>Winmdexp.exe (Windows 執行階段中繼資料匯出工具)
[!INCLUDE[wrt](../../../includes/wrt-md.md)] 中繼資料匯出工具 (Winmdexp.exe) 會將 .NET Framework 模組轉換為包含 [!INCLUDE[wrt](../../../includes/wrt-md.md)]中繼資料的檔案。 雖然 .NET Framework 組件和 [!INCLUDE[wrt](../../../includes/wrt-md.md)]中繼資料檔案使用相同的實體格式，但是中繼資料資料表的內容有些差異，也就是說，.NET Framework 組件不會自動做為 [!INCLUDE[wrt](../../../includes/wrt-md.md)]元件使用。 將 .NET Framework 模組轉換為 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 元件的程序稱為「匯出」。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 和 [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] 中，產生的 Windows 中繼資料 (.winmd) 檔案同時包含中繼資料和實作。  
  
 當您使用 [[!INCLUDE[wrt](../../../includes/wrt-md.md)]元件] 範本時 (在 C# 中位於 [Windows 市集] 下，在 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 或 [!INCLUDE[vs_dev11_ext](../../../includes/vs-dev11-ext-md.md)] 中位於 [Visual Basic] 下)，編譯器目標是 .winmdobj 檔案，而後續建置步驟會呼叫 Winmdexp.exe 將 .winmdobj 檔案匯出到 .winmd 檔案。 這是建置 [!INCLUDE[wrt](../../../includes/wrt-md.md)]元件的建議方式。 如果您想要更充分掌控建置流程，超越 Visual Studio 所提供的範圍，請直接使用 Winmdexp.exe。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
winmdexp [options] winmdmodule  
```  
  
#### <a name="parameters"></a>參數  
  
|引數或選項|描述|  
|------------------------|-----------------|  
|`winmdmodule`|指定要匯出的模組 (.winmdobj)。 只允許一個模組。 若要建立這個模組，請使用 `/target` 編譯器選項搭配 `winmdobj` 目標。 請參閱 [/target:winmdobj (C# 編譯器選項)](~/docs/csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md) 或 [/target (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/target.md)。|  
|`/docfile:` `docfile`<br /><br /> `/d:` `docfile`|指定 Winmdexp.exe 將產生的輸出 XML 文件檔。 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，輸出檔案基本上與輸入 XML 文件檔相同。|  
|`/moduledoc:` `docfile`<br /><br /> `/md:` `docfile`|指定編譯器使用 `winmdmodule` 所產生的 XML 文件檔名稱。|  
|`/modulepdb:` `symbolfile`<br /><br /> `/mp:` `symbolfile`|指定式資料庫 (PDB) 檔名稱，該檔案包含 `winmdmodule` 的符號。|  
|`/nowarn:` `warning`|隱藏指定的警告編號。 對於 *warning*，僅提供錯誤碼的數字部分，不包含前置零。|  
|`/out:` `file`<br /><br /> `/o:` `file`|指定輸出 Windows 中繼資料 (.winmd) 檔的名稱。|  
|`/pdb:` `symbolfile`<br /><br /> `/p:` `symbolfile`|指定將包含所匯出 Windows 中繼資料 (.winmd) 檔之符號的輸出程式資料庫 (PDB) 檔 (PDB) 名稱。|  
|`/reference:` `winmd`<br /><br /> `/r:` `winmd`|指定匯出期間參考的中繼資料檔 (.winmd 或組件)。 如果您使用位於 "\Program Files (x86)\Reference Assemblies\Microsoft\Framework\\.NETCore\v4.5" 的參考組件 (在 32 位元電腦上位於 "\Program Files\\...")，請同時包含 System.Runtime.dll 和 mscorlib.dll 的參考。|  
|`/utf8output`|指定應該採用 UTF-8 編碼的輸出訊息。|  
|`/warnaserror+`|指定應該將所有警告視為錯誤。|  
|**@** `responsefile`|指定包含選項的回應檔 (.rsp) (以及選擇性的 `winmdmodule`)。 `responsefile` 中的每一行都應該包含單一引數或選項。|  
  
## <a name="remarks"></a>備註  
 Winmdexp.exe 的設計並不是將任意 .NET Framework 組件轉換成 .winmd 檔案。 它需要的是使用 `/target:winmdobj` 選項編譯的模組，並且適用其他限制。 這些限制中最重要的是，組件的 API 介面中公開的所有類型都必須是 [!INCLUDE[wrt](../../../includes/wrt-md.md)]類型。 如需詳細資訊，請參閱 Windows 開發人員中心的[在 C# 和 Visual Basic 中建立 Windows 執行階段元件文件](http://go.microsoft.com/fwlink/p/?LinkID=238313)中的＜宣告 Windows 執行階段元件中的類型＞一節。  
  
 當您使用 C# 或 Visual Basic 撰寫 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式或 [!INCLUDE[wrt](../../../includes/wrt-md.md)]元件時，.NET Framework 可提供支援，讓您透過 [!INCLUDE[wrt](../../../includes/wrt-md.md)]進行程式設計時更順暢。 這會在[適用於 Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)文章中討論。 在過程中，有些常用的 [!INCLUDE[wrt](../../../includes/wrt-md.md)]類型會對應至 .NET Framework 類型。 Winmdexp.exe 會將這個過程反轉，並產生 API 介面來使用對應的 [!INCLUDE[wrt](../../../includes/wrt-md.md)]類型。 例如，建構自 <xref:System.Collections.Generic.IList%601> 介面的類型會對應到建構自 [!INCLUDE[wrt](../../../includes/wrt-md.md)][IVector\<T>](http://go.microsoft.com/fwlink/p/?LinkId=251132) 介面的類型。  
  
## <a name="see-also"></a>請參閱  
 [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
 [在 C++ 和 Visual Basic 中建立 Windows 執行階段元件](http://go.microsoft.com/fwlink/p/?LinkID=238313)  
 [Winmdexp.exe 錯誤訊息](../../../docs/framework/tools/winmdexp-exe-error-messages.md)  
 [建置、部署及組態工具 (.NET Framework)](http://msdn.microsoft.com/library/b8c921be-6012-4181-b8d4-ab15813fc9a7)
