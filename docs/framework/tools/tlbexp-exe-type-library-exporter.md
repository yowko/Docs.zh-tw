---
title: "Tlbexp.exe (類型程式庫匯出工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting type library [.NET Framework]
- exporter tool [.NET Framework]
- Tlbexp.exe
- Type Library Exporter
- type libraries [.NET Framework], exporting
ms.assetid: a487d61b-d166-467b-a7ca-d8b52fbff42d
caps.latest.revision: "35"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47710b81de79a9dfbb6bddd39035be2986350b0e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="tlbexpexe-type-library-exporter"></a>Tlbexp.exe (類型程式庫匯出工具)
類型程式庫匯出工具可以產生類型程式庫，這個類型程式庫描述定義在通用語言執行平台組件中的類型。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
tlbexp assemblyName [options]  
```  
  
#### <a name="parameters"></a>參數  
  
|引數|描述|  
|--------------|-----------------|  
|*assemblyName*|要匯出類型程式庫的組件。|  
  
|選項|描述|  
|------------|-----------------|  
|**/asmpath:** *目錄*|指定要搜尋組件的位置。 如果使用這個選項，則必須明確指定要搜尋參考組件的位置，包括目前的目錄在內。<br /><br /> 當您使用 **asmpath** 選項時，型別程式庫匯出工具不會在全域組件快取 (GAC) 中尋找組件。|  
|**/help**|顯示工具的命令語法和選項。|  
|**/names:** *filename*|指定類型程式庫中名稱的大小寫。 *filename* 引數是一個文字檔。 檔案中的每一行指定了類型程式庫中一個名稱的大小寫。|  
|**/nologo**|隱藏 Microsoft 程式啟始資訊顯示。|  
|**/oldnames**|在發生類型名稱衝突時，強制 Tlbexp.exe 匯出裝飾類型名稱。 請注意，此為 .NET Framework 2.0 版之前版本中的預設行為。|  
|**/out:** *file*|指定要產生的類型程式庫檔案的名稱。 如果省略這個選項，Tlbexp.exe 會產生一個與組件名稱 (指實際組件名稱，不一定和包含組件的檔案同名) 相同的類型程式庫和 .tlb 副檔名。|  
|**/silence:** `warningnumber`|隱藏顯示指定的警告。 此選項無法搭配 **/silent** 使用。|  
|**/silent**|隱藏顯示成功訊息。 此選項無法搭配**/silence** 使用。|  
|**/tlbreference:** *typelibraryname*|強制 Tlbexp.exe 明確解析類型程式庫參考，而不需查閱登錄。 例如，如果組件 B 參考組件 A，您就可以使用這個選項提供明確的類型程式庫參考，而不需依賴登錄中所指定的類型程式庫。 Tlbexp.exe 會執行版本檢查，以確定類型程式庫版本是否與組件版本相符；如果不符，便會產生錯誤。<br /><br /> 請注意，如果將 <xref:System.Runtime.InteropServices.ComImportAttribute> 屬性套用至介面，然後又由其他類型實作，則 **tlbreference** 選項仍然會查閱登錄。|  
|**/tlbrefpath:** *path*|參考類型程式庫的完整路徑。|  
|**/win32**|在 64 位元電腦上編譯時，這個選項會指定 Tlbexp.exe 產生 32 位元的類型程式庫。|  
|**/win64**|在 32 位元電腦上編譯時，這個選項會指定 Tlbexp.exe 產生 64 位元的型別程式庫。|  
|**/verbose**|指定詳細資訊模式，顯示需要產生類型程式庫的任何參考組件的清單。|  
|**/?**|顯示工具的命令語法和選項。|  
  
> [!NOTE]
>  Tlbexp.exe 的命令列選項不區分大小寫，而且可以依任何順序提供。 您只需要指定足夠的選項來唯一識別它。 例如，**/n** 相當於 **/nologo**，而 **/o:** *outfile.tlb* 相當於 **/out:** *outfile.tlb*。  
  
## <a name="remarks"></a>備註  
 Tlbexp.exe 會產生一個類型程式庫，其含有組件中所定義的類型定義。 應用程式 (例如 Visual Basic 6.0) 可以使用產生的類型程式庫來繫結至組件中所定義的 .NET 類型。  
  
> [!IMPORTANT]
>  您無法使用 Tlbexp.exe 匯出 Windows 中繼資料 (.winmd) 檔案。 不支援匯出 Windows 執行階段組件。  
  
 全部組件會一次同時轉換。 您無法使用 Tlbexp.exe 來為組件中所定義的類型子集產生類型資訊。  
  
 您無法使用 Tlbexp.exe 從已經使用[型別程式庫匯入工具 (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md) 匯入的組件中產生型別程式庫。 反之，您應該參考使用 Tlbimp.exe 匯入的原始類型程式庫。 您可以從參考使用 Tlbimp.exe 匯入之組件的組件匯出類型程式庫。 請參閱下列範例區段。  
  
 Tlbexp.exe 會將產生的類型程式庫放置在目前的工作目錄或指定給輸出檔的目錄。 單一組件可能導致產生多個類型程式庫。  
  
 Tlbexp.exe 會產生類型程式庫但是不會註冊它。 這和[組件註冊工具 (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) 形成對比，組件註冊工具會產生並註冊型別程式庫。 若要產生並以 COM 註冊類型程式庫，請使用 Regasm.exe。  
  
 如果您未指定 `/win32` 或 `/win64` 選項當中的任一項，Tlbexp.exe 會產生與執行編譯的電腦類型 (32 位元或 64 位元電腦) 相對應之 32 位元或 64 位元的類型程式庫。 為了交互編譯，您可以在 32 位元電腦上使用 `/win64` 選項以產生 64 位元的類型程式庫，或在 64 位元電腦上使用 `/win32` 選項以產生 32 位元的類型程式庫。 在 32 位元的類型程式庫中，<xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 值會設定為 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN32>。 在 64 位元的型別程式庫中，<xref:System.Runtime.InteropServices.ComTypes.SYSKIND> 值會設定為 <xref:System.Runtime.InteropServices.ComTypes.SYSKIND.SYS_WIN64>。 所有資料類型的轉換資料 (例如，類似 `IntPtr` 和 `UIntPtr` 指標大小的資料類型) 都會適當地加以轉換。  
  
 如果您使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性來指定 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType> 或 `VT_UNKOWN` 的 `VT_DISPATCH` 值，則 Tlbexp.exe 會忽略所有後續使用的 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> 欄位。 例如，假設有以下的簽章：  
  
```  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_UNKNOWN, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructUnkSafe(){return null;}  
[return:MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VarEnum.VT_DISPATCH, SafeArrayUserDefinedSubType=typeof(ConsoleKeyInfo))] public Array StructDispSafe(){return null;}  
```  
  
 會產生下列類型程式庫：  
  
```  
[id(0x60020004)]  
HRESULT StructUnkSafe([out, retval] SAFEARRAY(IUnknown*)* pRetVal);  
[id(0x60020005)]  
HRESULT StructDispSafe([out, retval] SAFEARRAY(IDispatch*)* pRetVal);  
```  
  
 請注意，Tlbexp.exe 會忽略 <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType> 欄位。  
  
 由於類型程式庫無法容納這些組件中的所有資訊，因此，Tlbexp.exe 在匯出處理序時可能會捨棄一些資料。 如需轉換處理序的說明並且識別型別程式庫所發出每件資訊的來源，請參閱[組件至型別程式庫轉換的摘要](http://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896)。  
  
 請注意，類型程式庫匯出工具會將 <xref:System.TypedReference> 參數匯出為 `VARIANT` 的方法，即使 <xref:System.TypedReference> 物件在 Unmanaged 程式碼中不具任何意義。 當您匯出具有 <xref:System.TypedReference> 參數的方法時，類型程式庫匯出工具不會產生警告或錯誤，而使用結果類型程式庫的 Unmanaged 程式碼也將無法正常執行。  
  
 Microsoft Windows 2000 (含) 以後版本都支援類型程式庫匯出工具。  
  
## <a name="examples"></a>範例  
 下列命令會產生一個和 `myTest.dll` 中組件同名的類型程式庫。  
  
```  
tlbexp myTest.dll  
```  
  
 下列命令會以 `clipper.tlb` 名稱產生類型程式庫。  
  
```  
tlbexp myTest.dll /out:clipper.tlb  
```  
  
 下列命令說明使用 Tlbexp.exe 來從組件 (其參考已經使用 Tlbimp.exe 匯入的組件) 中匯出類型程式庫。  
  
 先使用 Tlbimp.exe 匯入 `myLib.tlb` 類型程式庫，然後將它儲存為 `myLib.dll`。  
  
```  
tlbimp myLib.tlb /out:myLib.dll  
```  
  
 下列命令會使用 C# 編譯器來編譯 `Sample.dll,`，它會參考上一個範例中所建立的 `myLib.dll`。  
  
```  
CSC Sample.cs /reference:myLib.dll /out:Sample.dll  
```  
  
 下列命令會產生參考 `Sample.dll` 之類型程式庫的 `myLib.dll`。  
  
```  
tlbexp Sample.dll  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Runtime.InteropServices.TypeLibExporterFlags>  
 [工具](../../../docs/framework/tools/index.md)  
 [Regasm.exe (組件登錄工具)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [組件至型別程式庫轉換的摘要](http://msdn.microsoft.com/library/3a37eefb-a76c-4000-9080-7dbbf66a4896)  
 [Tlbimp.exe (類型程式庫匯入工具)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
