---
title: -nostdlib (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: 19a70e500f6b75fd003bdb798f242cddb3926935
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964354"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
導致編譯器不自動參考標準程式庫。  
  
## <a name="syntax"></a>語法  
  
```  
-nostdlib  
```  
  
## <a name="remarks"></a>備註  
 `-nostdlib`選項會移除對 system.object 元件的自動參考, 並防止編譯器讀取 Vbc .rsp 檔案。 與 vbc 檔案位於相同目錄中的 Vbc .rsp 檔案, 會參考常用的 .NET Framework 元件, 並匯入`System`和`Microsoft.VisualBasic`命名空間。  
  
> [!NOTE]
> 我們一律會參考 Mscorlib.dll 和 Microsoft。  
  
> [!NOTE]
> 此`-nostdlib`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼會`T2.vb`進行編譯, 而不會參考標準程式庫。 您必須將`_MYTYPE`條件式編譯常數設定為字串 "Empty", 才能移除該`My`物件。  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [自訂 My 中可用的物件](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
