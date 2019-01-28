---
title: -unsafe (C# 編譯器選項)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4a8f7d099b2cd3c1b4331c87f853b617fef505ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726529"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (C# 編譯器選項)
**-unsafe** 編譯器選項允許程式碼使用 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 關鍵字來進行編譯。  
  
## <a name="syntax"></a>語法  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>備註  
 如需 Unsafe 程式碼的詳細資訊，請參閱 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [建置] 屬性頁面。  
  
3.  選取 [容許 Unsafe 程式碼] 核取方塊。  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>在 csproj 檔案中新增此選項

請開啟專案的 .csproj 檔案，並新增下列項目：

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>。  
  
## <a name="example"></a>範例  
 針對 Unsafe 模式編譯 `in.cs`：  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
