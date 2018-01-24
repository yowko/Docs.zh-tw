---
title: "Peverify.exe (PEVerify 工具)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- portable executable files, PEVerify
- verifying MSIL and metadata
- PEVerify tool
- type safety requirements
- MSIL
- PEverify.exe
- PE files, PEVerify
ms.assetid: f4f46f9e-8d08-4e66-a94b-0c69c9b0bbfa
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5acb6da7c68f899daa4144e897e9ec31fcfa868a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="peverifyexe-peverify-tool"></a>Peverify.exe (PEVerify 工具)
PEVerify 工具可以協助像是編譯器撰寫者、指令碼引擎開發人員等產生 Microsoft Intermediate Language (MSIL) 的開發人員，判斷其 MSIL 程式碼和相關聯的中繼資料是否符合類型安全需求。 只有在避免使用某些語言建構時，某些編譯器才會產生可驗證的類型安全程式碼。 如果您是使用這類編譯器的開發人員，可能會想要驗證您並未損及程式碼的類型安全。 在這種情況下，您可以在檔案上執行 PEVerify 工具來檢查 MSIL 和中繼資料。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
peverify filename [options]  
```  
  
#### <a name="parameters"></a>參數  
  
|引數|描述|  
|--------------|-----------------|  
|*filename*|要檢查其 MSIL 和中繼資料的可攜式執行檔 (PE)。|  
  
|選項|描述|  
|------------|-----------------|  
|**/break=** *maxErrorCount*|發生 *maxErrorCount* 錯誤之後中止驗證。<br /><br /> .NET Framework 2.0 (含) 以後版本不支援此參數。|  
|**/clock**|以毫秒為單位測量並報告下列驗證時間：<br /><br /> **MD Val. cycle**<br /> 中繼資料驗證週期<br /><br /> **MD Val. pure**<br /> 單純中繼資料驗證<br /><br /> **IL Ver. cycle**<br /> Microsoft Intermediate Language (MSIL) 驗證週期<br /><br /> **IL Ver pure**<br /> 單純 MSIL 驗證<br /><br /> **MD Val. cycle** 和 **IL Ver. cycle** 時間包括了執行必要的啟始和關閉程序所需的時間。 **MD Val. pure** 和 **IL Ver pure** 時間則是反映純粹執行驗證所需的時間。|  
|**/help**|顯示工具的命令語法和選項。|  
|**/hresult**|以十六進位格式顯示錯誤碼。|  
|**/ignore=** *hex.code* [, *hex.code*]|忽略指定的錯誤碼。|  
|**/ignore=@** *responseFile*|忽略指定的回應檔中列出的錯誤碼。|  
|**/il**|針對 *filename* 所指定組件中實作的方法，執行 MSIL 型別安全驗證檢查。 除非您指定 **/quiet** 選項，否則此工具會針對每個找到的問題傳回詳細描述。|  
|**/md**|在 *filename* 所指定的組件上，執行中繼資料驗證檢查。 這會逐步檢查檔案內的所有中繼資料結構，並報告遇到的所有驗證問題。|  
|**/nologo**|不顯示產品版本和著作權資訊。|  
|**/nosymbols**|在 .NET Framework 2.0 版中，隱藏回溯相容性的行號。|  
|**/quiet**|指定無訊息模式，隱藏驗證問題報告的輸出。 Peverify.exe 仍會報告檔案是否為類型安全，但不會報告阻礙類型安全驗證之問題的資訊。|  
|`/transparent`|只驗證透明方法。|  
|**/unique**|忽略重複的錯誤碼。|  
|**/verbose**|在 .NET Framework 2.0 版中，使用 MSIL 驗證訊息顯示其他資訊。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 通用語言執行平台透過以類型安全的方式執行應用程式程式碼，協助強制執行安全性和隔離機制。 正常情況下，不是[可驗證型別安全](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)的程式碼無法執行，但是您可以設定安全性原則，讓受信任但無法驗證的程式碼執行。  
  
 如果 **/md** 和 **/il** 兩個選項都未指定，則 Peverify.exe 會執行這兩種檢查。 Peverify.exe 會先執行 **/md** 檢查。 如果沒有任何錯誤，則會執行 **/il** 檢查。 如果您同時指定 **/md** 和 **/il**，則即使中繼資料有錯誤，還是會執行 **/il** 檢查。 因此，如果中繼資料沒有錯誤，**peverify** *filename* 就相當於 **peverify** *filename* **/md** **/il**。  
  
 Peverify.exe 會依據資料流分析加上有效的中繼資料上數百項規則的清單，執行全面性的 MSIL 驗證檢查。 如需 Peverify.exe 所執行檢查的詳細資訊，請參閱 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] 的 [Tools Developers Guide] 資料夾中的＜中繼資料驗證規格＞和＜MSIL 指令集規格＞。  
  
 請注意，.NET Framework 2.0 版 (含) 以後版本支援傳回使用下列 MSIL 指令指定的可驗證 `byref`：`dup`、`ldsflda`、`ldflda`、`ldelema`、`call` 和 `unbox`。  
  
## <a name="examples"></a>範例  
 下列命令會對 `myAssembly.exe` 組件中實作的方法，執行中繼資料驗證檢查和 MSIL 類型安全驗證檢查。  
  
```  
peverify myAssembly.exe /md /il  
```  
  
 成功完成上述要求之後，Peverify.exe 會顯示下列訊息。  
  
```  
All classes and methods in myAssembly.exe Verified  
```  
  
 下列命令會對 `myAssembly.exe` 組件中實作的方法，執行中繼資料驗證檢查和 MSIL 類型安全驗證檢查。 工具會顯示執行這些檢查所需的時間。  
  
```  
peverify myAssembly.exe /md /il /clock  
```  
  
 成功完成上述要求之後，Peverify.exe 會顯示下列訊息。  
  
```  
All classes and methods in myAssembly.exe Verified  
Timing: Total run     320 msec  
        MD Val.cycle  40 msec  
        MD Val.pure   10 msec  
        IL Ver.cycle  270 msec  
        IL Ver.pure   230 msec  
```  
  
 下列命令會對 `myAssembly.exe` 組件中實作的方法，執行中繼資料驗證檢查和 MSIL 類型安全驗證檢查。 不過，Peverify.exe 會在達到最大錯誤計數 100 時停止。 工具也會忽略指定的錯誤碼。  
  
```  
peverify myAssembly.exe /break=100 /ignore=0x12345678,0xABCD1234  
```  
  
 下列命令會產生與上面的前一個範例相同的結果，但是會指定回應檔 `ignoreErrors.rsp` 中要忽略的錯誤碼。  
  
```  
peverify myAssembly.exe /break=100 /ignore@ignoreErrors.rsp  
```  
  
 回應檔可包含逗號分隔的錯誤碼清單。  
  
```  
0x12345678, 0xABCD1234  
```  
  
 或者，回應檔可以透過每行一個錯誤碼的方式格式化。  
  
```  
0x12345678  
0xABCD1234  
```  
  
## <a name="see-also"></a>請參閱  
 [工具](../../../docs/framework/tools/index.md)  
 [NIB：撰寫可驗證的型別安全程式碼](http://msdn.microsoft.com/library/d18f10ef-3b48-4f47-8726-96714021547b)  
 [型別安全和安全性](http://msdn.microsoft.com/library/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
