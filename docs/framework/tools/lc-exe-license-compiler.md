---
title: "Lc.exe (授權編譯器) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 4b20c589622526fd973700ed5b8bdd6f86d9b2ff
ms.contentlocale: zh-tw
ms.lasthandoff: 06/02/2017

---
# <a name="lcexe-license-compiler"></a>Lc.exe (授權編譯器)
授權編譯器可以讀取包含授權資訊的文字檔，並產生可內嵌於通用語言執行平台可執行檔的二進位檔案做為資源。  
  
 每當將授權控制項加入至表單時，Windows Form 設計工具便會自動產生或更新 .licx 文字檔。 專案系統會將 .licx 文字檔轉換為可支援 .NET 控制項授權的 .licenses 二進位資源，當做編譯的一部分。 接著此二進位資源將嵌入專案輸出。  
  
 使用授權編譯器建置您的專案時，不支援 32 位元與 64 位元之間的跨平台編譯。 這是因為授權編譯器必須載入組件，卻不允許從 32 位元應用程式載入 64 位元組件，反之亦然。 在這種情況下，請使用授權編譯器，以手動方式從命令列編譯授權，並指定對應的架構。  
  
 此工具會自動與 Visual Studio 一起安裝。 若要執行此工具，請使用 [開發人員命令提示字元] (或 Windows 7 中的 [Visual Studio 命令提示字元])。 如需詳細資訊，請參閱[命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)。  
  
 在命令提示字元下輸入下列命令：  
  
## <a name="syntax"></a>語法  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|選項|說明|  
|------------|-----------------|  
|**/complist:** filename|指定要包含在 .licenses 檔案中含有授權元件清單的檔案名稱。 使用元件的完整名稱與每行只有一個元件方式參考每個元件。<br /><br /> 命令列使用者可以為專案中的每個表單指定個別的檔案。 Lc.exe 接受多個輸入檔並產生單一 .licenses 檔案。|  
|**/h**[**elp**]|顯示工具的命令語法和選項。|  
|**/i:** module|指定包含列於 **/complist** 檔案中之元件的模組。 若要指定一個以上的模組，請使用多個 **/i** 旗標。|  
|**/nologo**|隱藏 Microsoft 程式啟始資訊顯示。|  
|**/outdir:** path|指定要放置輸出 .licenses 檔案的目錄。|  
|**/target:** targetPE|指定要產生 .licenses 檔案的可執行檔。|  
|**/v**|指定詳細資訊模式；顯示編譯程序資訊。|  
|**@** file|指定回應檔 (.rsp)。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="example"></a>範例  
  
1.  如果您要使用名為 `HostApp.exe` 之應用程式中 `Samples.DLL` 所包含的授權控制項 `MyCompany.Samples.LicControl1`，可以建立包含下列程式碼的 `HostAppLic.txt`。  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2.  使用下列命令建立這個稱為 `HostApp.exe.licenses` 的 .licenses 檔案。  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3.  建置包含 .licenses 檔案當做資源的 `HostApp.exe`。 如果您正在建置 C# 應用程式，可以使用下列命令來建置應用程式。  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 下列命令會從由 `myApp.licenses`、`hostapplic.txt` 和 `hostapplic2.txt` 所指定的授權元件清單編譯 `hostapplic3.txt`。 `modulesList` 引數是指定包含授權元件的模組。  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a>回應檔範例  
 下列清單顯示回應檔 `response.rsp` 的範例。 如需回應檔的詳細資訊，請參閱[回應檔](/visualstudio/msbuild/msbuild-response-files)。  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 下列命令列使用 `response.rsp` 檔。  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a>另請參閱  
 [工具](../../../docs/framework/tools/index.md)   
 [Al.exe (組件連結器)](../../../docs/framework/tools/al-exe-assembly-linker.md)   
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

