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
ms.openlocfilehash: 733013c8eca75bad0dc0bdf1d76f1468b1d903a8
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759388"
---
# <a name="-baseaddress"></a>-baseaddress
建立 DLL 時，請指定預設的基底地址。  
  
## <a name="syntax"></a>語法  
  
```  
-baseaddress:address  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`address`|必要項。 DLL 的基底位址。 此位址必須指定為十六進位數字。|  
  
## <a name="remarks"></a>備註  
 DLL 的預設基底位址由設定[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]。  
  
 請注意這個位址中的低序位字會捨入。 比方說，如果您指定的是 0x11110001，它會去掉尾數變成 0x11110000 四捨五入。  
  
 若要完成 DLL 的簽章的程序，使用`–R`的強式命名的工具 (Sn.exe) 的選項。  
  
 如果目標不是 DLL，則會忽略此選項。  
  
|若要在 Visual Studio IDE 中設定-baseaddress|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。 <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階**]。<br />4.修改中的值**DLL 基底位址：**  方塊中。 **注意：**    **DLL 基底位址：** 方塊是唯讀除非目標是 DLL。|  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))
