---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 5b3899462af7c4aa8e0f77377a8d7485975f9867
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937264"
---
# <a name="-verbose"></a>-verbose
使編譯器產生詳細的狀態和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定`-verbose`與指定`-verbose+`相同, 這會導致編譯器發出詳細資訊訊息。 此選項的預設值為`-verbose-`。  
  
## <a name="remarks"></a>備註  
 `-verbose`選項會顯示編譯器發出之錯誤總數的相關資訊、報告模組正在載入哪些元件, 以及顯示目前正在編譯的檔案。  
  
> [!NOTE]
> 此`-verbose`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼會`In.vb`編譯並指示編譯器顯示詳細的狀態資訊。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
