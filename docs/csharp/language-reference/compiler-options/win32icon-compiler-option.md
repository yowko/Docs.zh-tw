---
title: -win32icon (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5014b1da714f8e29f869d4641da93796a607aa4d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45674061"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C# 編譯器選項)
**-win32icon** 選項會在輸出檔案內插入一個 .ico 檔，讓輸出檔案在檔案總管中具有所需的外觀。  
  
## <a name="syntax"></a>語法  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 您想要新增至輸出檔的 .ico 檔案。  
  
## <a name="remarks"></a>備註  
 .ico 檔案可以使用 [Resource Compiler](/windows/desktop/menurc/resource-compiler) (資源編譯器) 建立。 資源編譯器是在編譯 Visual C++ 程式時叫用，而 .ico 檔案則是從 .rc 檔案建立。  
  
 請參閱 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (以參考) 或 [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (以附加) .NET Framework 資源檔。 請參閱 [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) 以匯入 .res 檔案。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [應用程式] 屬性頁。  
  
3.  修改**應用程式圖示**屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>。  
  
## <a name="example"></a>範例  
 編譯 `in.cs` 並附加 .ico 檔案 `rf.ico`，以產生 `in.exe`：  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>請參閱  

- [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
