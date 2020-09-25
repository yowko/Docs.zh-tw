---
description: -target:library (C# 編譯器選項)
title: -target:library (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 0f5b1e1bec8fd601bf111e1c2c64adf22d0a064e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91193721"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target:library (C# 編譯器選項)

**-Target： library**選項會讓編譯器建立動態連結程式庫 (DLL) ，而不是 (EXE) 的可執行檔。  
  
## <a name="syntax"></a>語法  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>備註  

 將建立副檔名為 .dll 的 DLL。  
  
 除非另行指定，否則[-out](./out-compiler-option.md)輸出檔名稱會採用第一個輸入檔的名稱。  
  
 當您在命令列指定時，會使用下一個或 **-target： module**選項**之前的所有**檔案來建立 .dll 檔案。  
  
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

- [-目標 (c # 編譯器選項) ](./target-compiler-option.md)
- [C# 編譯器選項](./index.md)
