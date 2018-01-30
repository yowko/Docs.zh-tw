---
title: "-debug (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d67d53e679a2d1255e87cfa426bf844089481061
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="-debug-c-compiler-options"></a>-debug (C# 編譯器選項)
**-debug** 選項可讓編譯器產生偵錯資訊，並將它放在一或多個輸出檔案中。  
  
## <a name="syntax"></a>語法  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 指定 `+` 或 **-debug** 會讓編譯器產生偵錯資訊，並將其放在程式資料庫 (.pdb 檔案) 中。 指定 `-` (當您未指定 **-debug** 時，它就會生效) 將不會建立任何偵錯資訊。  
  
 `full` &#124; `pdbonly`  
 指定編譯器所產生的偵錯資訊類型。 完整引數 (當您未指定 **-debug:pdbonly** 時，它就會生效) 允許將偵錯工具附加至執行中的程式。 指定 pdbonly 讓原始程式碼在偵錯工具中啟動程式時進行偵錯，但只有在將執行中的程式附加到偵錯工具時，才會顯示組譯工具。  
  
## <a name="remarks"></a>備註  
 若要建立偵錯組建，請使用此選項。 如果未指定 **-debug**、**-debug+** 或 **-debug:full**，您將無法偵錯程式的輸出檔案。  
  
 如果您使用 **-debug:full**，請注意會對 JIT 最佳化程式碼速度和大小造成某種程度的影響，以及對使用 **-debug:full** 的程式碼品質造成某種程度的影響。 建議使用 **-debug:pdbonly** 或沒有 PDB 可以產生發行程式碼。  
  
> [!NOTE]
>  **-debug:pdbonly** 與 **-debug:full** 之間的一項差異在於使用 **-debug:full** 時，編譯器會發出 <xref:System.Diagnostics.DebuggableAttribute>，以用來告知 JIT 編譯器有偵錯資訊可用。 因此，如果使用 **-debug:full**，則會在程式碼包含設定為 false 的 <xref:System.Diagnostics.DebuggableAttribute> 時收到錯誤。  
  
 如需如何設定應用程式偵錯效能的詳細資訊，請參閱[使映像偵錯更容易](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)。  
  
 若要變更 .pdb 檔案的位置，請參閱 [-pdb (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [建置] 屬性頁面。  
  
3.  按一下 [ **進階** ] 按鈕。  
  
4.  修改 [偵錯資訊] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>。  
  
## <a name="example"></a>範例  
 將偵錯資訊放入輸出檔案 `app.pdb` 中：  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
