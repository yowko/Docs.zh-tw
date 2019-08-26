---
title: -optimize (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606608"
---
# <a name="-optimize-c-compiler-options"></a>-optimize (C# 編譯器選項)
**-optimize** 選項啟用或停用由編譯器執行的最佳化，讓您的輸出檔案變得更小、更快且更有效率。  
  
## <a name="syntax"></a>語法  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>備註  
 **-optimize** 也會告知通用語言執行平台在執行階段進行程式碼最佳化。  
  
 根據預設，會停用最佳化。 指定 **-optimize+** 以啟用最佳化。  
  
 建置組件要使用的模組時，使用與那些組件相同的 **-optimize** 設定。  
  
 **-o** 是 **-optimize** 的簡短形式。  
  
 它可以合併 **-optimize** 和 [-debug](./debug-compiler-option.md) 選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟專案的 [屬性]  頁面。  
  
2. 按一下 [建置]  屬性頁面。  
  
3. 修改**最佳化程式碼**屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>。  
  
## <a name="example"></a>範例  
 編譯 `t2.cs` 並啟用編譯器最佳化：  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
