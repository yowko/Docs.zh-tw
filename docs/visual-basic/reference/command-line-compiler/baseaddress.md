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
ms.openlocfilehash: c794d1fc1c9d20e22ffa747e3175c846341ad8ad
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097757"
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
|`address`|必要。 DLL 的基底位址。 此位址必須指定為十六進位數位。|  
  
## <a name="remarks"></a>備註  

 DLL 的預設基底位址是由 .NET Framework 設定。  
  
 請注意，此位址中的低序位單字會四捨五入。 例如，如果您指定0x11110001，則會將它四捨五入為0x11110000。  
  
 若要完成 DLL 的簽署程式，請使用 `–R` 強式命名工具的選項 ( # A0) 。  
  
 如果目標不是 DLL，則會忽略這個選項。  
  
|若要在 Visual Studio IDE 中設定-baseaddress|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。 <br />2. 按一下 [ **編譯** ] 索引標籤。<br />3. 按一下 [ **Advanced**]。<br />4. 修改 [ **DLL 基底位址：** ] 方塊中的值。 **注意：**      除非目標是 DLL，否則 **DLL 基底位址：** box 是唯讀的。|  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-目標 (Visual Basic) ](target.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [Sn.exe (強式名稱工具) ](../../../framework/tools/sn-exe-strong-name-tool.md)) 
