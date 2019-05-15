---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 1c3c70b24de5163ca004b41a21017205a19d9730
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583372"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
可讓編譯器不會自動參考標準程式庫。  
  
## <a name="syntax"></a>語法  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>備註  
 `-nostdlib`選項會移除自動 System.dll 組件參考，並可防止編譯器讀取 Vbc.rsp 檔案。 Vbc.rsp 檔案，位於與 Vbc.exe 檔案相同的目錄中，參考常用的.NET Framework 組件並匯入`System`和`Microsoft.VisualBasic`命名空間。  
  
> [!NOTE]
>  一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。  
  
> [!NOTE]
>  `-nostdlib`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`而不需要參考標準程式庫。 您必須設定`_MYTYPE`字串 「 空白 」，若要移除的條件式編譯常數`My`物件。  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
