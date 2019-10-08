---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 8c5bc1d2ce331b8fe9461f91d64fbeab5a070b59
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004982"
---
# <a name="-verbose"></a>-verbose
使編譯器產生詳細的狀態和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定 `-verbose` 與指定 `-verbose+` 相同，這會導致編譯器發出詳細資訊訊息。 此選項的預設值為 `-verbose-`。  
  
## <a name="remarks"></a>備註  
 [@No__t-0] 選項會顯示編譯器發出之錯誤總數的相關資訊、報告模組正在載入哪些元件，以及顯示目前正在編譯的檔案。  
  
> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb`，並指示編譯器顯示詳細狀態資訊。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
