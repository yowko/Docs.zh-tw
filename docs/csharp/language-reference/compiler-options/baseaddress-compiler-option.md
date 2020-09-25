---
description: -baseaddress (C# 編譯器選項)
title: -baseaddress (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 76da496f7045f12778bba273947b913be1b94e3e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91196841"
---
# <a name="-baseaddress-c-compiler-options"></a>-baseaddress (C# 編譯器選項)

**-baseaddress** 選項讓您指定要載入 DLL 的慣用基底位址。 如需此選項的使用時機與使用原因之詳細資訊，請參閱 [Larry Osterman 的部落格](/archive/blogs/larryosterman/why-should-i-even-bother-to-use-dlls-in-my-system)。  
  
## <a name="syntax"></a>語法  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>引數  

 `address`  
 DLL 的基底位址。 這個位址可以指定十進位、十六進位或八進位數字。  
  
## <a name="remarks"></a>備註  

 DLL 的預設基底位址是由 .NET common language runtime 所設定。  
  
 請注意，這個位址會去掉低位字。 例如，如果您指定的是 0x11110001，它會去掉尾數變成 0x11110000。  
  
 若要完成 DLL 的簽章程序，請使用 SN.EXE 和 -R 選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. 開啟專案的 [屬性]**** 頁面。  
  
2. 按一下 [建置]**** 屬性頁面。  
  
3. 按一下 [進階]  按鈕。  
  
4. 修改 **DLL 基底位址**屬性。  
  
     若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
