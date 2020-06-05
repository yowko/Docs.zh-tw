---
title: -verbose
ms.date: 03/13/2018
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
ms.openlocfilehash: 405b557568a736de3ddc3b51e265261222613131
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403027"
---
# <a name="-verbose"></a>-verbose
使編譯器產生詳細的狀態和錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```console  
-verbose[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定與 `-verbose` 指定相同 `-verbose+` ，這會導致編譯器發出詳細資訊訊息。 此選項的預設值為 `-verbose-` 。  
  
## <a name="remarks"></a>備註  
 `-verbose`選項會顯示編譯器發出之錯誤總數的相關資訊、報告模組正在載入哪些元件，以及顯示目前正在編譯的檔案。  
  
> [!NOTE]
> 此 `-verbose` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb` 並指示編譯器顯示詳細的狀態資訊。  
  
```console  
vbc -verbose in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
