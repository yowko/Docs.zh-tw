---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: 6ee842dbe65cbd9d147e77ec523a2b031d303738
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002384"
---
# <a name="-baseaddress"></a>-baseaddress
指定建立 DLL 時的預設基底位址。  
  
## <a name="syntax"></a>語法  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`address`|必要項。 DLL 的基底位址。 此位址必須指定為十六進位數位。|  
  
## <a name="remarks"></a>備註  
 DLL 的預設基底位址是由 .NET Framework 所設定。  
  
 請注意，此位址中的較低順序單字會四捨五入。 例如，如果您指定0x11110001，它會四捨五入為0x11110000。  
  
 若要完成 DLL 的簽署程式，請使用強式命名工具（Sn.exe）的 `–R` 選項。  
  
 如果目標不是 DLL，則會忽略此選項。  
  
|若要在 Visual Studio IDE 中設定-baseaddress|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階**]。<br />4.修改 [ **DLL 基底位址：** ] 方塊中的值。 **注意：**     [ **DLL 基底位址：** ] 方塊是唯讀的，除非目標是 dll。|  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)）
