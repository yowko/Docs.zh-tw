---
title: -filealign (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /filealign
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
ms.openlocfilehash: d51dd0d63bec251d879ffb5e59ce5f7edaf136b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-filealign-c-compiler-options"></a>-filealign (C# 編譯器選項)
**-filealign** 選項可讓您指定輸出檔案中的區段大小。  
  
## <a name="syntax"></a>語法  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>引數  
 `number`  
 指定輸出檔案中區段大小的值。 有效值為 512、1024、2048、4096 和 8192。 這些值是以位元組為單位。  
  
## <a name="remarks"></a>備註  
 每個區段都會對齊界限，而這個界限是 **-filealign** 值的倍數。 沒有固定預設值。 如果未指定 **-filealign**，通用語言執行平台會在編譯時期選取預設值。  
  
 您可以藉由指定區段大小，來影響輸出檔案的大小。 修改區段大小對執行於較小裝置上的程式而言可能很有用。  
  
 請使用 [DUMPBIN](/cpp/build/reference/dumpbin-options) 來查看輸出檔案中區段的相關資訊。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [建置] 屬性頁面。  
  
3.  按一下 [ **進階** ] 按鈕。  
  
4.  修改 [檔案對齊] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>。  
  
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
