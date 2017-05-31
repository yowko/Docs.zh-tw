---
title: "-delaysign (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
dev_langs:
- CSharp
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
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
ms.openlocfilehash: f3dc76214acb66f2212a3611c0c419889e58c359
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---
# <a name="delaysign-c-compiler-options"></a>/delaysign (C# 編譯器選項)
這個選項可讓編譯器保留輸出檔案中的空間，以便稍後新增數位簽章。  
  
## <a name="syntax"></a>語法  
  
```  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 如果需要完整簽署的組件，請使用 **/delaysign-**。 如果只想在組件中放置公開金鑰，請使用 **/delaysign+**。 預設值為 **/delaysign-**。  
  
## <a name="remarks"></a>備註  
 **/delaysign** 選項必須搭配 [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) 或 [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) 才有作用。  
  
 當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。 所產生的數位簽章會儲存在包含資訊清單的檔案中。 當延遲簽署組件時，編譯器不會去計算和儲存簽章，但會保留檔案中的空間，以便稍後再加入簽章。  
  
 例如，使用 **/delaysign+** 時，可讓測試人員將組件放入全域快取中。 測試之後，您可以使用 [Assembly Linker](https://msdn.microsoft.com/library/c405shex) 公用程式將私密金鑰放入組件中，以完整簽署組件。  
  
 如需詳細資訊，請參閱[建立和使用強式名稱的組件](https://msdn.microsoft.com/library/xwb8f617)和[延遲簽署組件](../../../framework/app-domains/delay-sign-assembly.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性]  頁面。  
  
2.  修改 [僅延遲簽署] 屬性。  
  
 如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
