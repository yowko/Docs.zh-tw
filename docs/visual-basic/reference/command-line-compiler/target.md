---
title: -target （Visual Basic）
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
ms.openlocfilehash: 2d7ccfc6b033a9021e683a4a2501ca2ccc29956d
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004932"
---
# <a name="-target-visual-basic"></a>-target （Visual Basic）
指定編譯器輸出的格式。  
  
## <a name="syntax"></a>語法  
  
```console  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>備註  
 下表摘要說明 `-target` 選項的效果。  
  
|**選項**|**Behavior**|  
|----------------|------------------|  
|`-target:exe`|讓編譯器建立可執行檔主控台應用程式。<br /><br /> 這是未指定 `-target` 選項時的預設選項。 可執行檔是以 .exe 副檔名來建立。<br /><br /> 除非以 `/out` 選項指定，否則輸出檔案名會採用包含 `Sub Main` 程式的輸入檔名稱。<br /><br /> 編譯成 .exe 檔案的原始程式碼檔中只需要一個 `Sub Main` 程式。 使用 `-main` 編譯器選項來指定哪個類別包含 `Sub Main` 程式。|  
|`-target:library`|讓編譯器建立動態連結程式庫（DLL）。<br /><br /> 動態連結程式庫檔案是使用 .dll 副檔名所建立。<br /><br /> 除非另有指定 `-out` 選項，否則輸出檔名稱會採用第一個輸入檔的名稱。<br /><br /> 建立 DLL 時，不需要 `Sub Main` 程式。|  
|`-target:module`|使編譯器產生可新增至元件的模組。<br /><br /> 系統會使用副檔名 .netmodule 來建立輸出檔案。<br /><br /> .NET common language runtime 無法載入沒有元件的檔案。 不過，您可以使用 `-reference`，將這類檔案併入元件的組件資訊清單中。<br /><br /> 當某個模組中的程式碼參考另一個模組中的內部類型時，必須使用 `-reference`，將這兩個模組併入組件資訊清單。<br /><br /> [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)選項會從模組匯入中繼資料。|  
|`-target:winexe`|讓編譯器建立可執行檔 Windows 應用程式。<br /><br /> 可執行檔是以 .exe 副檔名來建立。 以 Windows 為基礎的應用程式則是從 .NET Framework Class Library 或 Windows Api 提供使用者介面。<br /><br /> 除非以 `-out` 選項指定，否則輸出檔案名會採用包含 `Sub Main` 程式的輸入檔名稱。<br /><br /> 編譯成 .exe 檔案的原始程式碼檔中只需要一個 `Sub Main` 程式。 如果您的程式碼有多個具有 @no__t 0 程式的類別，請使用 `-main` 編譯器選項來指定哪一個類別包含 @no__t 2 程式|  
|`-target:appcontainerexe`|讓編譯器建立可執行檔 Windows 應用程式，必須在應用程式容器中執行。 此設定是設計用於 @no__t 0 應用程式。<br /><br /> **Appcontainerexe**設定會在[可移植的可執行](/windows/desktop/Debug/pe-format)檔的 [特性] 欄位中設定一個位。 此位表示應用程式必須在應用程式容器中執行。 設定此位時，如果 `CreateProcess` 方法嘗試在應用程式容器外啟動應用程式，就會發生錯誤。 除了這個位設定外， **-target： appcontainerexe**相當於 **-target： winexe**。<br /><br /> 可執行檔是以 .exe 副檔名來建立。<br /><br /> 除非您使用 `-out` 選項來指定，否則輸出檔案名會採用包含 `Sub Main` 程式的輸入檔名稱。<br /><br /> 編譯成 .exe 檔案的原始程式碼檔中只需要一個 `Sub Main` 程式。 如果您的程式碼包含多個具有 @no__t 0 程式的類別，請使用 `-main` 編譯器選項來指定哪一個類別包含 @no__t 2 程式|  
|`-target:winmdobj`|讓編譯器建立可轉換成 Windows 執行階段二進位（winmd）檔案的中繼檔案。 除了 managed 語言程式以外，JavaScript 和C++程式也可以使用 winmd 檔案。<br /><br /> 中繼檔案是以副檔名 winmdobj 來建立。<br /><br /> 除非您使用 `-out` 選項另行指定，否則輸出檔名稱會採用第一個輸入檔的名稱。 不需要 `Sub Main` 程式。<br /><br /> Winmdobj 檔案的設計是用來做為 <xref:Microsoft.Build.Tasks.WinMDExp> 匯出工具的輸入，以產生 Windows 中繼資料（WinMD）檔案。 WinMD 檔案具有 winmd 副檔名，並同時包含來自原始程式庫的程式碼，以及 JavaScript、 C++和 Windows 執行階段使用的 WinMD 定義。|  
  
 除非您指定 `-target:module`，否則 `-target` 會使 .NET Framework 的組件資訊清單新增至輸出檔。  
  
 每個 Vbc 實例最多會產生一個輸出檔案。 如果您指定的編譯器選項（例如 `-out` 或 `-target`）超過一次，編譯器處理的最後一個會生效。 編譯中所有檔案的相關資訊會加入資訊清單中。 除了使用 `-target:module` 所建立的輸出檔以外，所有輸出檔都包含資訊清單中的元件中繼資料。 使用[Ildasm （IL](../../../framework/tools/ildasm-exe-il-disassembler.md)解譯器）來查看輸出檔案中的中繼資料。  
  
 `-target` 的簡短形式為 `-t`。  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定目標  
  
1. 在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。   
  
2. 按一下 [應用程式] 索引標籤。  
  
3. 修改 [**應用程式類型**] 方塊中的值。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `in.vb`，並建立 `in.dll`：  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-out （Visual Basic）](../../../visual-basic/reference/command-line-compiler/out.md)
- [-reference （Visual Basic）](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
