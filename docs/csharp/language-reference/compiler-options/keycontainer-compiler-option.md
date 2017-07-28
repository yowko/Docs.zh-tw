---
title: "-keycontainer (C# 編譯器選項) | Microsoft Docs"
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
ms.translationtype: Human Translation
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 30b851a3e44c90582227beda7245a7c4b0d57b47
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="keycontainer-c-compiler-options"></a>/keycontainer (C# 編譯器選項)
指定密碼編譯金鑰容器的名稱。  
  
## <a name="syntax"></a>語法  
  
```console  
/keycontainer:string  
```  
  
## <a name="arguments"></a>引數  
 `string`  
 強式名稱金鑰容器的名稱。  
  
## <a name="remarks"></a>備註  
 使用 **/keycontainer** 選項時，編譯器會將公開金鑰從指定的容器插入資訊清單，並使用私密金鑰簽署最終組件，藉此建立可共用的元件。 若要產生金鑰檔，請在命令列鍵入 sn -k `file`。 sn-i 會將金鑰組安裝在容器中。  
  
 如果您使用 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md) 進行編譯，則在使用 [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md) 將這個模組編譯為組件時，金鑰檔的名稱會保留在模組中並併入組件。  
  
 您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>)。  
  
 您也可以使用 [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) 將加密資訊傳遞給編譯器。 如果您想要將公開金鑰新增至資訊清單，但希望等到測試過後再簽署組件，請使用 [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md)。  
  
 如需詳細資訊，請參閱[建立和使用強式名稱的組件](https://msdn.microsoft.com/library/xwb8f617)和[延遲簽署組件](../../../framework/app-domains/delay-sign-assembly.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  Visual Studio 開發環境無法使用這個編譯器選項。  
  
 您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>，以程式設計方式存取這個編譯器選項。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
