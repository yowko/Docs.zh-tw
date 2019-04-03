---
title: -target:winexe (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /target:winexe
helpviewer_keywords:
- /target compiler options [C#], /target:winexe
- -target compiler options [C#], /target:winexe
- target compiler options [C#], /target:winexe
ms.assetid: b5a0619c-8caa-46a5-a743-1cf68408ad7a
ms.openlocfilehash: 5d5e5c62dc1a5fe6901ee232084a704d7d936b76
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411959"
---
# <a name="-targetwinexe-c-compiler-options"></a>-target:winexe (C# 編譯器選項)
**-target:winexe** 選項可讓編譯器建立可執行檔 (EXE)，其為一個 Windows 程式。  
  
## <a name="syntax"></a>語法  
  
```console  
-target:winexe  
```  
  
## <a name="remarks"></a>備註  
 將會建立副檔名為 .exe 的可執行檔。 Windows 程式是從 .NET Framework 程式庫或使用 Windows API 提供使用者介面的程式。  
  
 使用 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md) 建立主控台應用程式。  
  
 除非特別使用 [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) 選項指定輸出檔案名稱，否則輸出檔案名稱會採用包含 [Main](../../../csharp/programming-guide/main-and-command-args/index.md) 方法的輸入檔案名稱。  
  
 指定於命令列時，下一個 **-out** 或 [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) 選項之前的所有檔案都是用來建立 Windows 程式。  
  
 編譯為 .exe 檔案的原始程式碼檔中只需要一個 **Main** 方法。 如果您的程式碼有多個具有 **Main** 方法的類別，則 [-main](../../../csharp/language-reference/compiler-options/main-compiler-option.md) 選項可讓您指定哪個類別包含 **Main** 方法。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [應用程式] 屬性頁。  
  
3.  修改 [輸出類型] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>。  
  
## <a name="example"></a>範例  
 將 `in.cs` 編譯為 Windows 程式︰  
  
```console  
csc -target:winexe in.cs  
```  
  
## <a name="see-also"></a>另請參閱

- [-target (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)
- [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
