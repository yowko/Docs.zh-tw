---
title: "-win32res (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c24da8bb745847612d882d00eff7f03dbc60475
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-win32res-c-compiler-options"></a>-win32res (C# 編譯器選項)
**-win32res** 選項會將 Win32 資源插入至輸出檔案中。  
  
## <a name="syntax"></a>語法  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 您想要新增至輸出檔的資源檔。  
  
## <a name="remarks"></a>備註  
 您可以使用[資源編譯器](../../language-reference/compiler-options/resource-compiler-option.md)建立 Win32 資源檔。 資源編譯器是在編譯 Visual C++ 程式時叫用，而 .res 檔案則是從 .rc 檔案建立。  
  
 Win32 資源可以包含版本或點陣圖 (圖示) 資訊，這項資訊可以協助您在 [檔案總管] 中識別應用程式。 如果您未指定 **-win32res**，編譯器會根據組件版本產生版本資訊。  
  
 請參閱 [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (以參考) 或 [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (以附加) .NET Framework 資源檔。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [應用程式] 屬性頁。  
  
3.  按一下 [資源檔] 按鈕，然後使用下拉式方塊選擇檔案。  
  
## <a name="example"></a>範例  
 編譯 `in.cs` 並附加 Win32 資源檔 `rf.res`，以產生 `in.exe`：  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
