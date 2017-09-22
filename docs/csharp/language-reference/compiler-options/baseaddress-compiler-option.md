---
title: "-baseaddress (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /dllbase
dev_langs:
- CSharp
helpviewer_keywords:
- baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
caps.latest.revision: 18
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
ms.openlocfilehash: 91193ae794957b5045a225614d6322e86d18d459
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="baseaddress-c-compiler-options"></a>/baseaddress (C# 編譯器選項)
**/baseaddress** 選項讓您指定要載入 DLL 的慣用基底位址。 如需此選項的使用時機與使用原因的詳細資訊，請參閱[改善應用程式的啟動時間](http://go.microsoft.com/fwlink/?LinkId=107043)和 [Larry Osterman 的網誌](http://go.microsoft.com/fwlink/?LinkId=107044)。  
  
## <a name="syntax"></a>語法  
  
```console  
/baseaddress:address  
```  
  
## <a name="arguments"></a>引數  
 `address`  
 DLL 的基底位址。 這個位址可以指定十進位、十六進位或八進位數字。  
  
## <a name="remarks"></a>備註  
 DLL 的預設基底位址是由 .NET Framework Common Language Runtime 所設定。  
  
 請注意，這個位址會去掉低位字。 例如，如果您指定的是 0x11110001，它會去掉尾數變成 0x11110000。  
  
 若要完成 DLL 的簽章程序，請使用 SN.EXE 和 -R 選項。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性] 頁面。  
  
2.  按一下 [建置] 屬性頁面。  
  
3.  按一下 [ **進階** ] 按鈕。  
  
4.  修改 **DLL 基底位址**屬性。  
  
     若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=fullName>   
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)

