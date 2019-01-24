---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 7a5dd305d1cc40e57d0f07f383151dc1a965bdda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513915"
---
# <a name="-verbose"></a>-verbose
可讓編譯器產生詳細的狀態和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定`-verbose`等同於指定`-verbose+`，因而導致編譯器發出詳細訊息。 此選項的預設值是`-verbose-`。  
  
## <a name="remarks"></a>備註  
 `-verbose`選項會顯示編譯器所發出的錯誤總數的相關資訊、 報表組件正在載入的模組，並顯示目前正在進行編譯的檔案。  
  
> [!NOTE]
>  `-verbose`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`In.vb`和指示編譯器將會顯示詳細資訊的狀態資訊。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
