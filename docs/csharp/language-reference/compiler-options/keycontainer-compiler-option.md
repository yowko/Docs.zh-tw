---
title: "-keycontainer (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keycontainer
dev_langs:
- CSharp
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5d27fa0b80ca6df15394ad1fda149377cac41a8b
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# /keycontainer (C# Compiler Options)
指定密碼編譯金鑰容器的名稱。  
  
## 語法  
  
```  
/keycontainer:string  
```  
  
## Arguments  
 `string`  
 強式名稱金鑰容器的名稱。  
  
## 備註  
 使用 **\/keycontainer** 選項時，編譯器會將指定容器內的公開金鑰放入組件資訊清單內，並用私密金鑰為最終的組件簽署，建立出共用元件。  若要產生金鑰檔，請在命令列上輸入 sn \-k `file` 。輸入sn \-i 會將金鑰組安裝至容器。  
  
 如果您用 [\/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 進行編譯，金鑰檔案的名稱就會放在模組內，當您使用 [\/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) 將模組編譯到組件內時才放入組件。  
  
 您也可以為任何 Microsoft Intermediate Language \(MSIL\) 模組，指定這個選項當做原始程式碼中的自訂屬性 \(<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>\)。  
  
 您還可以使用 [\/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) 將加密資訊傳遞至編譯器。  如果您要將公開金鑰加入至組件資訊清單，但仍要組件經過測試後才簽署，請使用 [\/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)。  
  
 如需詳細資訊，請參閱[建立和使用強式名稱的組件](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)以及[延遲簽署組件](../Topic/Delay%20Signing%20an%20Assembly.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  Visual Studio 開發環境中沒有這個編譯器選項。  
  
 您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>，以程式設計方式存取這個編譯器選項。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)

