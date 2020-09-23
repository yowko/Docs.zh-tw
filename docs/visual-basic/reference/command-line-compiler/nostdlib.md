---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 4fcc5305985f5ba32b3e6ffb740c0611821215d3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097653"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic) 

導致編譯器不自動參考標準程式庫。  
  
## <a name="syntax"></a>語法  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>備註  

 `-nostdlib`選項會移除 System.dll 元件的自動參考，並防止編譯器讀取 Vbc 檔。 Vbc 檔案（位於與 Vbc.exe 檔案相同的目錄中）會參考常用 .NET Framework 元件，並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。  
  
> [!NOTE]
> 一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 元件。  
  
> [!NOTE]
> `-nostdlib`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  

 下列程式碼會進行編譯， `T2.vb` 而不會參考標準程式庫。 您必須將 `_MYTYPE` 條件式編譯常數設定為字串 "Empty"，以移除 `My` 物件。  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [-noconfig](noconfig.md)
- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [自訂 My 可以使用的物件](../../developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
