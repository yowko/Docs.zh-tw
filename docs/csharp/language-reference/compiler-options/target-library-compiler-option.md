---
title: -target:library (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: c947b2015c19d0809cab4535e989ee83ebf17fd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606388"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target:library (C# 編譯器選項)
**-目標：庫**選項使編譯器創建動態連結程式庫 （DLL）， 而不是可執行檔 （EXE）。  
  
## <a name="syntax"></a>語法  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>備註  
 將建立副檔名為 .dll 的 DLL。  
  
 除非使用[-out](./out-compiler-option.md)選項另行指定，否則輸出檔案名將採用第一個輸入檔的名稱。  
  
 在命令列指定時，所有檔都用於創建 .DLL 檔案，以創建下一**個-出出**或 **-目標：模組**選項。  
  
 建置 .dll 檔案時，不需要 [Main](../../programming-guide/main-and-command-args/index.md) 方法。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟專案的 [屬性]**** 頁面。  
  
2. 按一下 [應用程式]**** 屬性頁。  
  
3. 修改 [輸出類型]**** 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="example"></a>範例  
 建立 `in.dll` 以編譯 `in.cs`：  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>另請參閱

- [-目標（C# 編譯器選項）](./target-compiler-option.md)
- [C# 編譯器選項](./index.md)
